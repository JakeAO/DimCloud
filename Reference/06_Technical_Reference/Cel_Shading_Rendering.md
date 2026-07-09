# Cel-Shading Rendering Pipeline — Technical Reference

## Overview

This document details the cel-shading pipeline used in Dark Cloud 2, evolved through Dragon Quest VIII, Rogue Galaxy, and Ni no Kuni.

---

## Pipeline Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                      CEL-SHADING PIPELINE                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  VERTEX STAGE (VS/Compute)                                      │
│  ├─ Transform (Model→View→Clip)                                 │
│  ├─ Normal/ Tangent/ Bitangent Transform                        │
│  ├─ Light Vector Calculation (Per-Vertex/Cluster)               │
│  ├─ Outline Vertex Extrusion (Back-Face)                        │
│  └─ Instance/Primitive ID for Cel Lookup                        │
│                                                                 │
│  GEOMETRY/MESH STAGE (Optional)                                 │
│  ├─ Mesh Shader Amplification (Culling/LOD)                     │
│  ├─ Mesh Shader Generation (Procedural Geo)                     │
│  └─ Meshlet Culling (Frustum/Occlusion)                         │
│                                                                 │
│  RASTERIZATION                                                  │
│  ├─ Conservative Raster (Outlines)                              │
│  ├─ Conservative Raster (Shaded)                                │
│  └─ Depth Pre-Pass (Optional)                                   │
│                                                                 │
│  FRAGMENT STAGE (PS)                                            │
│  ├─ OUTLINE PASS                                                │
│  │   ├─ Back-Face Detection (Sign(N·V))                         │
│  │   ├─ Extrusion Along Normal                                  │
│  │   ├─ Stencil Write (Outline Mask)                            │
│  │   └─ Color = OutlineColor (Usually Black)                    │
│  │                                                              │
│  ├─ SHADE PASS                                                  │
│  │   ├─ Normal Reconstruction (G-Buffer / Forward)              │
│  │   ├─ Lighting (N·L, N·H)                                     │
│  │   ├─ **Cel Ramp Lookup** (1D/2D Texture)                     │
│  │   ├─ Matcap / Rim / Fresnel                                  │
│  │   ├─ Specular (Cel-Specular)                                 │
│  │   └─ Stencil Test (Mask Outlines)                            │
│  │                                                              │
│  ├─ HIGHLIGHT PASS (Optional)                                   │
│  │   ├─ Specular Power → Cel Ramp                               │
│  │   └─ Additive Blend                                          │
│  │                                                              │
│  ├─ OUTLINE COMPOSITE (Screen-Space)                            │
│  │   ├─ Sobel/Depth/Normal Edge Detect                          │
│  │   ├─ ID Buffer Edge Detect                                   │
│  │   └─ Composite (Stencil Mask)                                │
│  │                                                              │
│  └─ POST-PROCESS STACK                                          │
│      ├─ HDR Tonemap (ACES/Filmic)                               │
│      ├─ Bloom (Separable Blur)                                  │
│      ├─ Color Grading (LUT)                                     │
│      ├─ Vignette / Film Grain                                   │
│      └─ UI Overlay                                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Core Techniques

### 1. Outline Rendering

#### Method A: Vertex Extrusion (Classic)
```hlsl
// Vertex Shader
float4 VS_Main(VS_INPUT input) {
    float3 normalW = mul((float3x3)World, input.Normal);
    float3 viewDir = normalize(CameraPos - WorldPos);
    
    // Back-face detection
    float facing = dot(normalW, viewDir);
    
    // Extrude back-faces
    float3 posW = WorldPos + normalW * OutlineWidth * step(0, facing);
    
    return mul(ViewProj, float4(posW, 1));
}
```
**Pros**: Exact geometry; no screen-space artifacts  
**Cons**: Extra draw call; vertex cost; thin geometry issues

#### Method B: Screen-Space (Post-Process)
```hlsl
// Compute Shader / Pixel Shader
float4 OutlineDetect(float2 uv) {
    float depth = DepthTexture.Load(int3(uv, 0)).r;
    float2 normal = NormalTexture.Load(int3(uv, 0)).rg;
    uint id = IDTexture.Load(int3(uv, 0)).r;
    
    // Sample neighbors
    float edge = 0;
    [unroll] for (int i = 0; i < 8; i++) {
        float2 nuv = uv + OFFSETS[i] * PixelSize;
        edge += step(DepthThreshold, abs(DepthTexture.Load(int3(nuv, 0)).r - depth));
        edge += step(NormalThreshold, distance(NormalTexture.Load(int3(nuv, 0)).rg, normal));
        edge += step(0, abs(int(IDTexture.Load(int3(nuv, 0)).r) - int(id)));
    }
    
    return saturate(edge) * OutlineColor;
}
```
**Pros**: Single pass; works on all geometry; stylized control  
**Cons**: Resolution-dependent; temporal artifacts; depth discontinuities

#### Method C: Hybrid (Modern Best Practice)
- **Primary**: Vertex extrusion for clean silhouette
- **Secondary**: Screen-space for interior edges / creases
- **Composite**: Stencil mask + depth-aware blend

---

### 2. Cel Shading (Diffuse)

#### 1D Cel Ramp Lookup
```hlsl
// Cel Ramp Texture: 1D (256×1) or 2D (256×4 for bands)
Texture1D CelRamp : register(t0);

float3 CelShade(float NdotL, float3 baseColor) {
    // NdotL in [-1, 1] → [0, 1]
    float idx = (NdotL * 0.5 + 0.5);
    
    // Hard bands (e.g., 4 bands)
    idx = floor(idx * NumBands) / NumBands;
    
    // Sample ramp
    float3 shade = CelRamp.Sample(SamplerLinearClamp, idx).rgb;
    
    return baseColor * shade;
}
```

#### Band Configuration (Typical)
| Bands | Distribution | Use Case |
|-------|--------------|----------|
| 2 | [0, 0.5), [0.5, 1] | Minimalist / Retro |
| 3 | [0, 0.33), [0.33, 0.66), [0.66, 1] | Classic Anime |
| 4 | [0, 0.25), [0.25, 0.5), [0.5, 0.75), [0.75, 1] | **DC2/DQ8 Standard** |
| 5+ | Custom | High-Fidelity / NNK |

#### 2D Cel Ramp (Banded + Hue Shift)
```
Texture2D CelRamp2D : register(t0);
// U: N·L (0→1)
// V: Band Index (0→NumBands-1) + Hue Variation
```
Allows per-band hue shift (e.g., shadows cooler, highlights warmer)

---

### 3. Specular (Cel-Specular)

#### Blinn-Phong → Cel Ramp
```hlsl
float3 CelSpecular(float NdotH, float shininess) {
    float spec = pow(saturate(NdotH), shininess);
    
    // Cel bands
    float idx = floor(spec * SpecularBands) / SpecularBands;
    
    return SpecularColor * SpecularRamp.Sample(SamplerLinearClamp, idx).rgb;
}
```

#### Cel-Specular Bands
| SpecularBands | Visual |
|---------------|--------|
| 1 | None (Matte) |
| 2 | Hard Highlight |
| 3 | Standard Anime |
| 4+ | Soft Gradient |

---

### 4. Matcap (Material Capture)

```hlsl
// Matcap Texture: Spherical Environment Map (512×512)
Texture2D Matcap : register(t1);

float3 MatcapShade(float3 normalW, float3 viewW) {
    // View-space reflection vector
    float3 R = reflect(-viewW, normalW);
    
    // Spherical coords
    float2 uv = float2(
        0.5 + R.x * 0.5,
        0.5 - R.y * 0.5
    );
    
    return Matcap.Sample(SamplerLinearClamp, uv).rgb;
}
```

**Usage**: Skin (DC2), Metal/Cloth (DQ8/NNK), UI Icons

---

### 5. Rim / Fresnel

```hlsl
float RimFactor(float3 normalW, float3 viewW) {
    float facing = dot(normalW, viewW);
    float rim = 1 - saturate(facing);
    return pow(rim, RimPower) * RimIntensity;
}
```
