# PS2 Hardware Constraints & Design Implications

## Hardware Specifications (PlayStation 2)

| Component | Specification | Impact on Dark Cloud |
|-----------|---------------|---------------------|
| **CPU (EE)** | 294.912 MHz MIPS III (R5900) | Main game logic; AI; physics |
| **VU0 (Vector Unit 0)** | 147.456 MHz (COP2) | Vertex transformation; skinning |
| **VU1 (Vector Unit 1)** | 147.456 MHz (Microcode) | Custom geometry processing; particle systems |
| **GS (Graphics Synthesizer)** | 147.456 MHz; 4 MB eDRAM | All rendering; 480i/480p output |
| **Main RAM** | 32 MB RDRAM (3.2 GB/s) | **Critical bottleneck**; all assets |
| **VRAM** | 4 MB (embedded in GS) | Frame buffer; textures (swapped from main) |
| **IOP** | 33.8688 MHz (PS1 CPU) | I/O; sound (SPU2); DVD drive |
| **SPU2** | 24 Voices; 48 kHz | ADPCM streaming; real-time effects |
| **DVD-ROM** | 4x CAV (3.5–5.5 MB/s) | Streaming assets; level loading |

---

## Memory Management (The 32 MB Wall)

### Allocation Budget (Typical Dark Cloud Frame)
| Category | Est. Usage | Notes |
|----------|------------|-------|
| **Executable Code** | 2–3 MB | EE + VU microcode |
| **Frame Buffers** | 2–3 MB | Double/triple buffer; Z-buffer |
| **Texture Cache** | 8–12 MB | Streamed from DVD; LRU eviction |
| **Geometry Data** | 4–6 MB | Room templates; enemy models |
| **Audio** | 2–4 MB | SPU2 RAM + streaming buffers |
| **Game State** | 1–2 MB | Entities; inventory; world |
| **System/OS** | 1–2 MB | Kernel; IOP communication |
| **Free/Fragmentation** | ~2 MB | **Critical for streaming** |

### Dark Cloud Specifics
| System | Memory Strategy |
|--------|-----------------|
| **Procedural Dungeons** | Room templates (not full level); instantiated at runtime |
| **Georama** | Piece models shared; only placement data unique |
| **Weapons** | Procedural stats; only base models stored |
| **Textures** | 128×128/256×256; 4-bit/8-bit CLUT; heavy reuse |
| **Audio** | SPU2 streaming; minimal RAM footprint |
| **Save Data** | Memory Card (8 MB); compressed bit-packed |

---

## Rendering Pipeline (GS Constraints)

### Fill-Rate Limits
- **Pixel Fill**: 2.4 GP/s (theoretical)
- **Realistic**: 1.2–1.5 GP/s (with blending/Z-test)
- **Dark Cloud**: ~600–800 MP/s (30 fps target)

### Geometry Throughput
- **VU1 Microcode**: Custom per game
- **Dark Cloud**: ~5–10M triangles/frame (procedural + static)
- **VU0**: Skinning (characters); vertex lighting

### Texture Constraints
| Limitation | Workaround |
|------------|------------|
| **4 MB VRAM** | Texture streaming; mipmaps in main RAM |
| **Max Texture** | 1024×1024 (theoretical); practical 512×512 |
| **CLUT** | 4-bit (16 colors) / 8-bit (256 colors) for UI/sprites |
| **Compression** | None hardware; custom RLE in main RAM |

### DC2 Cel-Shading Pipeline
1. **VU1**: Transform + Outline Detection (Dot(N,L) < Threshold)
2. **GS**: Render Base + Outline Pass (Stencil/Offset)
3. **Post**: Bloom (Downsample → Blur → Add) — GS bandwidth heavy
3. **Textures**: Soft (Low contrast); minimal specular maps

---

## DVD Streaming & Loading

### Dark Cloud Approach
| System | Technique |
|--------|-----------|
| **Dungeon Floors** | Room templates in RAM; enemies/items streamed |
| **Georama** | Piece models in RAM; placement data only |
| **Cutscenes** | Pre-rendered FMV (DVD) → Real-time transition |
| **Audio** | SPU2 streaming (ADPCM); voice in cutscenes only |

### DC2 Improvements
- **Larger Texture Budgets** (Cel-shading = simpler textures)
- **Better Microcode** (VU1 optimized for outline pass)
- **Reduced Load Times** (Better DVD layout; 1.5× faster)

---

## CPU Optimization Patterns (DC1/DC2)

### EE (Main Thread)
```c
// Typical frame
UpdateInput();
UpdateCamera();
UpdateEntities();      // 60–100 entities max
UpdateProcedural();    // Dungeon gen (spread over frames)
UpdateGeorama();       // Only in village mode
UpdateUI();
SubmitVU1Microcode();  // Kick VU1
```

### VU1 (Geometry)
- **Microcode**: Double-buffered (Current/Next)
- **Dark Cloud**: Custom "Dungeon" microcode (room instancing)
- **DC2**: "CelShader" microcode (outline + lighting)

### VU0 (Skinning)
- Characters only (6 in DC1; 2+Steve+Forms in DC2)
- 2–4 bones per vertex; software fallback for complex

### IOP (Background)
- DVD reads (Async; double-buffered)
- SPU2 DMA (Audio streaming)
- Memory Card I/O (Save/Load)

---

## Dark Cloud 1 vs 2 Technical Differences

| System | DC1 | DC2 | Change |
|--------|-----|-----|--------|
| **Engine** | Custom (DC1) | **Rewritten** (DC2) | From scratch per Hino |
| **Renderer** | Standard Lighting | **Cel-Shading + Bloom** | New VU1 microcode |
| **Procedural** | Room templates | **Improved variance** | Better room graph |
| **Memory** | Tight (32 MB limit) | **Same limit; better mgmt** | Texture streaming v2 |
| **Audio** | SPU2 basic | **Streaming + Voice** | SPU2 optimization |
| **Load Times** | Noticeable | **Reduced 30%** | DVD layout + prefetch |
| **Save System** | Village only | **Anywhere (Menu)** | SRAM + Memory Card |
| **VU1 Microcode** | Dungeon | **CelShader + Dungeon** | Dual microcode swap |

