# Brainstorm: Cel-Shading Rendering Pipeline — Successor Target

*All content is theorycraft/non-canon for a spiritual successor.*

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
│  │   ├─ Specular Power → Cel Specular Ramp                      │
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
float3 normalW = mul((float3x3)World, input.Normal);
float3 viewDir = normalize(CameraPos - WorldPos);
float facing = dot(normalW, viewDir);

// Back-face detection
float isBackFace = step(0, facing);

// Extrude back-faces along normal
float3 posW = WorldPos + normalW * OutlineWidth * isBackFace;
output.Pos = mul(ViewProj, float4(posW, 1));
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
    
    float edge = 0;
    [unroll] for (int i = 0; i < 8; i++) {
        float2 nuv = uv + OFFSETS[i] * PixelSize;
        edge += step(DepthThreshold, abs(DepthTexture.Load(int3(nuv, 0)).r - depth));
        edge += step(NormalThreshold, distance(NormalTexture.Load(int3(nuv, 0)).rg, normal));
        edge += step(0.5, abs(int(IDTexture.Load(int3(nuv, 0)).r) - int(id)));
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
Texture1D<float3> CelRamp : register(t0);
SamplerState SamplerLinearClamp : register(s0);

float3 CelShade(float NdotL, float3 baseColor) {
    // N·L in [-1, 1] → [0, 1]
    float idx = (NdotL * 0.5 + 0.5);
    
    // Hard bands (e.g., 4 bands)
    idx = floor(idx * _CelBands) / _CelBands;
    
    // Sample ramp
    float3 shade = CelRamp.Sample(SamplerLinearClamp, idx).rgb;
    
    return baseColor * shade;
}
```

#### 2D Cel Ramp (Banded + Hue Shift)
```
Texture2D<float3> CelRamp2D : register(t0);
// U: N·L (0→1)
// V: Band Index (0→NumBands-1) + Hue Variation
```

#### Band Configuration (Typical)
| Band | N·L Range | Purpose |
|------|-----------|---------|
| **0** | [-1.0, -0.5) | Core Shadow |
| **1** | [-0.5, 0.0) | Form Shadow |
| **2** | [0.0, 0.5) | Light Side |
| **3** | [0.5, 1.0] | Highlight |

**Color Design**:
- Shadow bands → Cooler hue (blue/purple tint)
- Light bands → Warmer hue (yellow/orange tint)
- Highlight → Near-white + color tint

---

### 3. Specular (Cel-Specular)

#### Blinn-Phong → Cel Ramp
```hlsl
float3 CelSpecular(float NdotH, float shininess) {
    float spec = pow(saturate(NdotH), shininess * 100.0);
    
    // Cel bands
    float idx = floor(spec * _SpecularBands) / _SpecularBands;
    
    return _SpecularColor * SpecularRamp.Sample(SamplerLinearClamp, idx).rgb;
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
Texture2D<float3> Matcap : register(t1);

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

**Usage**: Skin (DC2), Metal/Cloth/Weapon (DQ8/NNK), UI Icons

---

### 5. Rim / Fresnel

```hlsl
float RimFactor(float3 normalW, float3 viewW) {
    float facing = dot(normalW, viewW);
    float rim = 1 - saturate(facing);
    return pow(rim, _RimPower) * _RimIntensity;
}
```

---

## Modern Pipeline (Mesh Shaders + Compute + RT)

### Mesh Shader Pipeline (DX12/Vulkan)
```
[Amplification Shader] → [Mesh Shader] → [Rasterizer] → [Pixel Shader]
```

#### Amplification Shader (Culling + Instance Gen)
```hlsl
[AmplificationShader("MeshletCulling")]
void AmplifyMain(uint clusterID : SV_ClusterID, out uint instanceCount : SV_InstanceCount) {
    // Frustum/Occlusion culling per meshlet
    // LOD selection
    // Output instance count for Mesh Shader
}
```

#### Mesh Shader (Geometry Gen + Cel Vertex)
```hlsl
[MeshShader("CelMeshlet")]
void MeshMain(
    uint tid : SV_DispatchThreadID,
    uint instanceID : SV_InstanceID,
    inout TriStream<VS_OUTPUT> triStream
) {
    // Fetch meshlet data
    // Vertex transform + outline extrusion
    // Emit triangles
}
```

### Compute-Based Cel Shading (Forward+ / Clustered)

```hlsl
// Clustered Forward+ Cel Shading
[numthreads(8,8,1)]
void CS_CelShade(uint3 dtid : SV_DispatchThreadID) {
    // Per-tile light culling
    // Per-pixel cel shading
    // Output to G-Buffer or Forward
}
```

**Benefits**: 1000+ dynamic lights; consistent cel look; scales with resolution

---

## Ray Tracing Integration (Cel-Aware)

### GI (RTXGI / DDGI)
```
RT GI → Cel Ramp → Banded Indirect
```
- Probe irradiance → N·L → Cel Ramp
- Maintains cel aesthetic in indirect

### Reflections
```
SSR → RT Fallback → Cel Ramp → Sharp Bands
```
- Cel ramps applied to reflection color

### Shadows
```
Cascaded Shadow Maps + RT Contact Hardening
```
- Cel shadow: Hard edge; optional penumbra band

---

## Anti-Aliasing for Cel-Shading

| Method | Compatibility | Quality |
|--------|---------------|---------|
| **MSAA** | ✅ Native | Good (edges) |
| **SMAA** | ✅ Post | Good (preserves outlines) |
| **TAA** | ⚠️ Tricky | Ghosting on outlines |
| **DLSS/FSR2** | ✅ Upscale | Best (temporal + spatial) |

**Recommendation**: **SMAA + DLSS/FSR2** for outlines; MSAA 2x fallback

---

## Cel Ramp Authoring

### Texture Format
| Property | Value |
|----------|-------|
| **Format** | R8G8B8A8_UNORM / BC1/BC7 |
| **Dimensions** | 256×1 (1D) or 256×4 (2D) |
| **Wrap** | Clamp |
| **Filter** | Point (Hard Bands) / Linear (Soft) |
| **Mips** | None (1D) / Yes (2D) |

### Band Design Guidelines
| Band | N·L Range | Purpose | Hue Shift |
|------|-----------|---------|-----------|
| **0** | [-1.0, -0.5) | Core Shadow | Cool (Blue/Purple) |
| **1** | [-0.5, 0.0) | Form Shadow | Cool → Neutral |
| **2** | [0.0, 0.5) | Light Side | Warm (Yellow/Orange) |
| **3** | [0.5, 1.0] | Highlight | Near-White + Tint |

### Material Preview Tool
- **Real-time Preview**: Model + Light + Ramp Editor
- **Band Editor**: Drag thresholds; see instant result
- **Export**: PNG + JSON (Engine format)

---

## Outline Techniques Comparison

| Technique | Quality | Performance | Best For |
|-----------|---------|-------------|----------|
| **Geometry Extrusion** (DC2) | Low | High (Vertex) | Legacy / Low-end |
| **Screen-Space Sobel** (Depth/Normal) | Medium | Medium | General |
| **Screen-Space Edge Detect** (Depth+Normal+ID) | High | Medium | Stylized |
| **Mesh Shader Edge** (Meshlet boundaries) | Highest | High (GPU) | Next-Gen |
| **Analytic Outline** (SDF) | Infinite | High | Vector Art |

**Recommended**: Hybrid Screen-Space (Depth+Normal+ID) + Geometry Extrusion fallback

---

## Performance Budgets (Target: 4K/60)

| Pass | Budget (ms) | Optimization |
|------|-------------|--------------|
| **Depth Pre-Pass** | 0.5 | Hierarchical Z |
| **Outline (Geometry)** | 1.0 | Meshlet Culling |
| **Outline (Screen)** | 0.3 | Compute Shader |
| **Cel Shade (Forward+)** | 2.5 | Clustered Lights |
| **Matcap/Rim** | 0.3 | Texture Cache |
| **Post-Process** | 0.8 | Compute Blur |
| **UI/Overlay** | 0.2 | Canvas Renderer |
| **Total** | **~5.6 ms** | **16.6 ms Budget (60 fps)** |

---

## Art Direction Guidelines

### Color Palette (Per Biome/Era)
| Era/Zone | Base Hue | Accent | Outline |
|----------|----------|--------|---------|
| **Ancient Past** | Earth tones | Gold/Copper | Dark Brown |
| **Recent Past** | Industrial | Brass/Steel | Charcoal |
| **Present** | Vibrant | Cyan/Magenta | Black |
| **Future** | Neon | Holographic | White/Glow |

### Character Design for Cel
- **Silhouette Readability**: Strong shapes; distinct profiles
- **Color Blocking**: Flat colors; minimal gradients
- **Outline Harmony**: Outline color complements base (not pure black)
- **Rim Light as Personality**: Warm=Heroic, Cool=Mysterious

---

## Shader Permutations (Key)

| Permutation | Keywords | Count |
|-------------|----------|-------|
| **Shade Only** | `CEL_SHADE` | 1 |
| **Shade + Outline (Geo)** | `CEL_SHADE` `OUTLINE_GEO` | 1 |
| **Shade + Outline (Screen)** | `CEL_SHADE` `OUTLINE_SCREEN` | 1 |
| **Shade + Matcap** | `CEL_SHADE` `MATCAP` | 1 |
| **Skinned + Outline** | `SKINNED` `OUTLINE_GEO` | 1 |
| **Instanced + Cel** | `INSTANCED` `CEL_SHADE` | 1 |
| **Total (Est.)** | | **~24** |

---

## Successor Pipeline Additions

| Feature | Implementation |
|---------|----------------|
| **Temporal AA for Cel** | Custom resolve preserving outlines |
| **Variable Rate Shading** | Lower rate on flat cel bands |
| **Meshlet Culling** | GPU-driven; outline-aware |
| **Dynamic Cel Bands** | Art-directed per scene/time |
| **Outline Thickness** | Screen-space + depth-aware |
| **Color Grading LUT** | Per-era / per-region grading |
| **Outline Stylization** | Dashed/Tapered/Calligraphic |
| **Ink Simulation** | Per-pixel noise on outline edge |

---

## References & Further Reading

1. **Lake, A. et al.** "Stylized Rendering in Dragon Quest VIII." *CEDEC 2005.*
2. **Sousa, T.** "Cel Shading in Rogue Galaxy." *SIGGRAPH 2006 Sketches.*
3. **NVIDIA.** "Non-Photorealistic Rendering with GPU Shaders." *GPU Gems 2.*
4. **Valve.** "Cel Shading in Team Fortress 2." *GDC 2007.*
5. **Miyake, Y.** "Ni no Kuni Rendering Pipeline." *CEDEC 2011.*
6. **Epic Games.** "Nanite & Mesh Shaders in UE5." *GDC 2021.*