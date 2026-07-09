# Brainstorm: Engine Architecture — Successor Target v5.0

*All content is theorycraft/non-canon for a spiritual successor.*

---

## Evolution Summary

| Version | Game(s) | Key Innovation | Platform |
|---------|---------|----------------|----------|
| **v1.0** | Dark Cloud | First PS2 title; procedural dungeon + Georama | PS2 |
| **v2.0** | Dark Cloud 2 | **Full rewrite**; cel-shading; time travel systems | PS2 |
| **v2.5** | Dragon Quest VIII | World streaming; seamless overworld; toon shading | PS2 |
| **v3.0** | Rogue Galaxy | Seamless planet exploration; action combat; procedural planets | PS2 |
| **v3.5** | White Knight Chronicles | Online co-op; transform; PS3 Cell/RSX | PS3 |
| **v4.0** | Ni no Kuni | Ghibli pipeline; deferred + PBR hybrid | PS3 |
| **v4.2** | Yo-kai Watch | Multi-platform (3DS/Mobile/Switch) | 3DS |
| **v5.0** | **Successor Target** | **Mesh Shaders + RT + Compute + ECS** | **PC/PS5/XSX/Switch2** |

---

## Level-5 Engine Genealogy

```
Level-5 Engine v1.0 (DC1)
    │
    ├─ Complete Rewrite → v2.0 (DC2)
    │       │
    │       ├─ DQ8 Branch → v2.5 (DQ8)
    │       │       │
    │       │       ├─ RG Branch → v3.0 (Rogue Galaxy)
    │       │       │
    │       │       └─ Layton Branch → v2.7 (Professor Layton)
    │       │
    │       └─ WKC Branch → v3.5 (White Knight Chronicles)
    │
    └─ Complete Rewrite → v4.0 (Ni no Kuni / Yo-kai Watch)
            │
            ├─ PS4 Branch → v4.5 (PS4 Titles)
            └─ Mobile Branch → v4.2 (Yo-kai Watch Mobile)
```

---

## What Worked (Keep)

1. **Full Rewrite When Needed** — v1→v2 was necessary; v3→v4 was evolution
2. **Custom VU Microcode** → **Modern: Compute Shaders** — Own the pipeline
3. **Procedural + Handcrafted Hybrid** — Best of both worlds
4. **Data-Driven Design** — Lua/Scripting for designers
5. **Custom Toolchain** — Maya/Max plugins → **Modern: Blender/Houdini/USD plugins**
6. **Engine as Game Enabler** — Tech serves design (not tech demo)

---

## What to Modernize

| PS2 Pattern | Modern Equivalent |
|-------------|-------------------|
| **VU Microcode** | **Compute Shaders / Mesh Shaders** |
| **DVD Streaming** | **NVMe / DirectStorage** |
| **4 MB VRAM Management** | **12–24 GB VRAM / Virtual Texturing** |
| **Fixed-Function Lighting** | **PBR / Ray Tracing / GI** |
| **Single-threaded EE** | **Job System / ECS / Multi-threaded** |
| **Custom Script VM** | **Lua / C# / Visual Scripting** |
| **Custom Maya Plugins** | **Blender / Houdini / USD Pipeline** |
| **DVD Layout Optimization** | **Asset Bundles / Addressables** |
| **VU1 Microcode Swap** | **Pipeline State Objects / Dynamic Shaders** |
| **32 MB RAM Budgeting** | **Arena Allocators + RAII** |

---

## Architecture Target for v5.0 (Successor)

```
MAIN THREAD (Game Logic / ECS)
    │
    ├─ Simulation (World State / Agents / Economy)
    ├─ Procedural Systems (Dungeon / World / Seeds)
    ├─ Crafting / Invention / Legacy Forge
    ├─ Quest / Narrative Manager
    └─ Multiplayer / Sync (Deterministic)
    │
RENDER THREAD (GPU-Driven)
    │
    ├─ Culling (GPU Frustum/Occlusion)
    ├─ Mesh Shader Pipeline (Procedural Geo)
    ├─ Compute Shaders (Particles / Water / Cloth)
    ├─ Ray Tracing (GI / Reflections / Shadows)
    ├─ Meshlet Rendering (Nanite-style)
    └─ Post-Process Stack (HDR / Bloom / DOF / AA)
    │
ASYNC THREADS
    │
    ├─ Asset Streaming (NVMe DirectStorage)
    ├─ Procedural Generation (Seeds → Assets)
    ├─ Audio / Physics / Network
    └─ Background Simulation (World Tick)
    │
TOOLS & PIPELINE
    │
    ├─ USD / glTF / Blender / Houdini
    ├─ Hot-Reload (Shaders / Scripts / Blueprints)
    ├─ Procedural Graph Editor (Dungeon / World / Seeds)
    ├─ Deterministic Replay / Seeds
    └─ Community Content Pipeline (Mods / Seeds / Blueprints)
```

---

## Engine Requirements

| Requirement | Target |
|-------------|--------|
| **Platforms** | PC (Win/Linux), PS5, Xbox Series, Switch 2 |
| **Rendering** | Mesh Shaders + RT + Compute (DX12/Vulkan) |
| **Simulation** | 100k+ Agents (GPU/CPU Hybrid) |
| **World Size** | 100+ km² (Streaming) |
| **Players** | Single + Async Community (4–8 Co-op) |
| **Mod Support** | Full (Lua/WASM + Asset Pipeline) |
| **Pipeline** | glTF/USD + Custom Schemas |
| **Scripting** | Lua 5.4 + WASM (Sandboxed) |
| **Build System** | CMake + Ninja + CI/CD |
| **Languages** | C++20 / Rust (Core) / C# (Tools) |

---

## Target Specs

| Platform | Minimum | Recommended | Ultra |
|----------|---------|-------------|-------|
| **CPU** | 4-core / 3.0 GHz | 8-core / 4.0 GHz | 16-core / 4.5 GHz |
| **GPU** | 4 GB VRAM / DX11 | 12 GB VRAM / DX12U | 24 GB VRAM / RTX 4090 |
| **RAM** | 8 GB | 16 GB | 32 GB |
| **Storage** | SSD (SATA) | NVMe Gen3 | NVMe Gen4 |
| **OS** | Win 10 64-bit | Win 11 64-bit | Win 11 64-bit |
| **Resolution** | 1080p / 30 | 1440p / 60 | 4K / 60-120 |
| **Ray Tracing** | Off | Hybrid | Full |

---

## Engine Architecture Patterns

### ECS (Entity Component System)
```
Archetype-Based (EnTT / Flecs / Custom)
    │
    ├─ Components: Transform, Health, Inventory, AI, Renderable, etc.
    ├─ Systems: Physics, AI, Rendering, Crafting, Economy, etc.
    ├─ Queries: Iterate matching entities (cache-friendly)
    └─ Events: Entity created/destroyed, component added/removed
```

### Job System (Multi-threading)
```cpp
// Job Graph with Dependencies
JobHandle simulatePhysics = PhysicsSystem.Schedule();
JobHandle updateAI = AISystem.Schedule(simulatePhysics);
JobHandle generateDungeon = DungeonSystem.Schedule();
JobHandle.CompleteAll();
```

### GPU-Driven Rendering
```hlsl
// Mesh Shader Pipeline
[AmplificationShader("MeshletCulling")]
void AmplifyMain(uint clusterID : SV_ClusterID, out uint instanceCount : SV_InstanceCount) { ... }

[MeshShader("CelMeshlet")]
void MeshMain(uint tid : SV_DispatchThreadID, uint instanceID : SV_InstanceID, inout TriStream<VS_OUTPUT> triStream) { ... }
```

### GPU Compute for Simulation
```hlsl
// Agent simulation on GPU
[numthreads(64,1,1)]
void CS_AgentSim(uint3 dtid : SV_DispatchThreadID) {
    // 100k+ agents; needs/wants/behaviors
    // Output: position, state, interactions
}
```

---

## Rendering Pipeline

### Cel-Shading + PBR Hybrid
```
Mesh Shader → Amplification Shader → Rasterizer → Fragment Shader → Post
```

#### Vertex/Amplification
- **Mesh Shader**: Procedural expansion (dungeon/world), LOD, culling
- **Amplification**: Instance culling, LOD selection, instance generation

#### Fragment (Cel + PBR Hybrid)
- **Diffuse**: N·L → Cel Ramp (configurable bands; 3-7)
- **Specular**: GGX → Cel Specular Ramp (sharp bands)
- **Rim**: 1-(N·V) → Rim Ramp + Matcap
- **Outline**: Screen-space (Depth/Normal/ID edges) + Geometry extrusion hybrid
- **Matcap**: Per-material capture (skin/cloth/metal/weapon)

#### Post-Process Stack
1. **HDR Tonemap** (ACES / Filmic)
2. **Bloom** (Separable Gaussian; threshold+knee)
3. **Volumetric Fog/Light Shafts**
4. **SSAO/SSGI** (Optional; Quality setting)
5. **Motion Blur** (Velocity buffer)
6. **DOF** (Bokeh)
7. **Color Grade** (3D LUT)
8. **Film Grain / Vignette**
9. **UI Overlay** (Canvas renderer)

### Ray Tracing Targets
| Feature | Target |
|---------|--------|
| **GI** | RTXGI / DDGI (Dynamic; Cel-aware) |
| **Reflections** | SSR + RT fallback (Cel-preserving) |
| **Shadows** | Cascaded + RT contact hardening |
| **Ambient Occlusion** | SSAO + RT refinement |

### Anti-Aliasing for Cel-Shading
| Method | Compatibility | Quality |
|--------|---------------|---------|
| **MSAA** | ✅ Native | Good (edges) |
| **SMAA** | ✅ Post | Good (preserves outlines) |
| **TAA** | ⚠️ Tricky | Ghosting on outlines |
| **DLSS/FSR2** | ✅ Upscale | Best (temporal + spatial) |

**Recommendation**: **SMAA + DLSS/FSR2** for outlines; MSAA 2x fallback

---

## Procedural Systems Architecture

### Dungeon Generation (Node-Based Graph)
```
Seed → Graph Gen → Room Templates → Connection Graph → Population → Validation
```

### World Generation (Macro/Micro Hybrid)
```
MACRO (Handcrafted Anchors):
  ├─ Entrance Set Piece
  ├─ Mid-Floor Landmark
  ├─ Boss Arena
  └─ Exit Transition

MICRO (Procedural Connective Tissue):
  ├─ Room Templates (Parametric: size, exits, theme)
  ├─ Connection Graph (Spanning tree + controlled loops)
  ├─ Objective Seeding (Medals/Secrets/Resources)
  ├─ Prop/Decoration Scatter (Rules-based)
  └─ Enemy/Item Population (Simulation-driven)
```

### Seed Format (Shareable)
```json
{
  "seed": "DIMCLOUD_DUNGEON_001",
  "version": "2.1",
  "dungeon": "verdant_ruins",
  "floor": 7,
  "layout": "macro_anchor_micro_connect",
  "macroAnchors": ["entrance", "waterfall_room", "boss_arena"],
  "microSeed": 0xDEADBEEF,
  "objectives": ["time_trial", "wipeout", "photo_target", "secret_room"],
  "enemyTheme": "corrupted_nature",
  "worldStateHash": 0xCAFEBABE,
  "creator": "PlayerName",
  "difficulty": "heroic",
  "tags": ["speedrun", "photography", "lore"]
}
```

---

## Deterministic Simulation

### Requirements
- **Fixed Timestep**: 60 Hz (configurable)
- **Float Determinism**: IEEE 754 strict; no fast-math
- **RNG**: Xoshiro256** / PCG; seedable per system
- **Input Recording**: Frame-perfect replay
- **Cross-Platform**: Identical results PC/Console

### Use Cases
- **Replay System**: Ghost runs; strategy sharing
- **Multiplayer**: Lockstep / Rollback netcode
- **Testing**: Golden master frames; regression detection
- **Community Seeds**: Identical dungeon across platforms

---

## Persistent World Architecture

### World State (Streaming)
```
CHUNK (1km × 1km):
  ├─ Terrain (Heightmap + Splatmap)
  ├─ Vegetation (Instanced; LOD)
  ├─ Structures (Blueprints → Instanced Meshes)
  ├─ Agents (NPCs; Wildlife; Threats)
  ├─ Resources (Nodes; Deposits; Nodes)
  ├─ Events (Active; Scheduled; Historical)
  └─ Player Data (Ownership; Progress; Modifications)
```

### Continuous Simulation (Offline Progress)
```
TICK (1/sec simulated):
  ├─ Resource Flow: Past Mines → Present Factories → Future Tech
  ├─ Population: Housing → Workers → Specialists → Leaders
  ├─ Economy: Supply/Demand; Prices; Trade Routes
  ├─ Ecology: Flora/Fauna Populations; Migration; Extinction Risk
  ├─ Corruption: Dark Energy Spread; Player Containment
  └─ Threats: Raider Attacks; Monster Evolution; Disasters; Cosmic
```

### State Serialization
```cpp
// World State Snapshot
struct WorldSnapshot {
    uint64_t tick;
    ChunkData[] chunks;
    AgentState[] agents;
    EconomyState economy;
    EventLog events;
    PlayerProgress[] players;
};
// Compressed: ~50MB for full world; incremental saves
```

---

## Multiplayer / Async Community

### Sync Model
- **Single Player**: Local simulation
- **Co-op (2-4)**: Host authoritative; state sync
- **Async Community**: Blueprint/Seed/Blueprint sharing (no real-time sync)

### Community Pipeline
```
Player Creates Blueprint/Seed
        │
        ▼
Validate (Size/Performance/Content)
        │
        ▼
Publish → Community Hub (Mod.io / Custom)
        │
        ▼
Curate: Vote / Tag / Fork / Report
        │
        ▼
Canon Integration (Top Voted → NPC Builds in World)
        │
        ▼
Legacy: Designs Persist Across Playthroughs
```

---

## Asset Pipeline (Modern)

### Formats
| Type | Format | Notes |
|------|--------|-------|
| **Geometry** | glTF 2.0 + Meshlet extension | Binary; draco compression |
| **Materials** | glTF + Custom PBR extensions | Cel ramp + Matcap + Outline |
| **Animations** | glTF + Custom morph targets | Blend shapes for cel |
| **Scenes** | USD (authoring) → glTF (runtime) | USD for editing; glTF for runtime |
| **Blueprints** | Custom JSON + glTF references | Parametric + simulation history |
| **Seeds** | FlatBuffers | Deterministic; fast parse |

### Pipeline Stages
```
ARTIST (Blender/Houdini/Substance)
    │
    ▼
EXPORT (glTF + Custom Extensions)
    │
    ▼
IMPORT PIPELINE (CI/CD)
    ├─ Validation (Naming, Limits, Naming Conventions)
    ├─ Processing (Meshlet Generation, LOD, Tangents)
    ├─ Compression (Draco, BasisU, Oodle)
    ├─ Atlas/Packing (Texture Arrays, Material Atlases)
    ├─ Meshlet Generation (Nanite-style)
    └─ Manifest Generation (Addressables)
    │
    ▼
RUNTIME (Streaming)
    ├─ Priority-based (Player Proximity)
    ├─ Background (Low-priority)
    └─ Predictive (World Simulation Hints)
```

### Hot-Reload Support
- **Shaders**: Compile on change; swap at frame boundary
- **Scripts**: Lua/WASM hot-reload; state preservation
- **Blueprints**: Parameter tweak; instant preview
- **Assets**: Texture/Model swap; no restart

---

## Technical Debt to Avoid

| Debt | Origin | Prevention |
|------|--------|------------|
| **Hardcoded Magic Numbers** | DC1/DC2 | Data-Driven All Config |
| **Single-threaded Logic** | PS2 EE | Job System from Day 1 |
| **Manual Memory Mgmt** | 32 MB Limit | Arena Allocators + RAII |
| **Proprietary Formats** | PS2 Era | Open Standards (glTF/USD/OBJ) |
| **No Hot-Reload** | Console Era | Script/Shader/Asset Hot-Reload |
| **No Automated Testing** | Console QA | CI/CD + Unit/Integration Tests |
| **Platform-Specific Code** | PS2/PS3/DS | Abstraction Layers (RHI/RPI) |
| **No Analytics** | Pre-Telemetry | Built-in Telemetry (Opt-in) |

---

## Engine Team Structure (Estimated)

| Role | Count | Focus |
|------|-------|-------|
| **Core Engine** | 4 | Memory, Job System, ECS, Asset Pipeline |
| **Rendering** | 4 | Mesh Shaders, RT, Compute, Cel Pipeline |
| **Simulation** | 3 | AI, Economy, Ecology, World State |
| **Procedural** | 3 | Dungeon/World/Seed Systems |
| **Tools/Editors** | 3 | Graph Editors, Blueprint, Live Preview |
| **Pipeline/Build** | 2 | CI/CD, Asset Processing, Hot-Reload |
| **Platform** | 2 | PS5/XSX/Switch2/PC Ports |
| **Audio/Physics** | 2 | Integration + Custom Systems |
| **Total** | **23** | (Scalable to 40+ for full production) |

---

## Risk Mitigation

| Risk | Mitigation |
|------|------------|
| **Cel + RT conflict** | Cel-aware RT (masked rays; banded GI) |
| **Simulation performance** | GPU agent compute; LOD simulation distance |
| **Asset streaming stalls** | DirectStorage; predictive prefetch |
| **Cross-platform determinism** | Fixed-point math for critical paths |
| **Community content moderation** | Automated validation + human curation |
| **Scope creep** | Phase gates; MVP defined; stretch documented |

---

## Development Timeline (Estimated)

| Phase | Duration | Milestone |
|-------|----------|-----------|
| **Pre-Production** | 6 Mo | Architecture Finalized; Core Systems Prototype |
| **MVP (Core Loop)** | 6 Mo | Proc Dungeon + Weapon XP + Basic Georama |
| **Alpha (Feature Complete)** | 6 Mo | Dual Char + Ridepod/Transform + Spectrumize + Visible Trees |
| **Beta (DC2 Parity)** | 6 Mo | Time Travel Georama + Photo/Invention + Medals + Fishing |
| **1.0 (Successor Identity)** | 6 Mo | Multi-Era + Legacy Forge + Blueprint Share + Seeds |
| **Post-Launch** | Ongoing | Mod Support + Seasonal Seeds + Community Events |

---

*"We didn't carry over code from Dark Cloud to Dark Cloud 2. We threw it all away. But we carried over the experience. The next engine must do the same: discard the code, keep the wisdom."* — Akihiro Hino (Paraphrased)