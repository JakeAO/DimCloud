# Locked: Causal Georama

*Canonical world-building design for DimCloud. Do not modify without explicit discussion.*

---

## Decision Summary

| # | Decision | Status |
|---|----------|--------|
| 1 | 3 era-layers: Distant Past / Present / Distant Future | ✅ Locked (from `03_Characters.md`) |
| 2 | Present = always-accessible hub; Past & Future = visited layers | ✅ Locked |
| 3 | Causal flow = forward cascade (Distant Past → Present → Distant Future) | ✅ Locked |
| 4 | Build Conditions = 3 axes (Population / Prosperity / Protection) | ✅ Locked |
| 5 | Parametric Blueprints = 3 axes (Form / Function / Footprint) | ✅ Locked |
| 6 | Player verb: Design → Build → Meet Conditions → World State Changes → Future Alters | ✅ Locked |
| 7 | Visible Causality: every build shows immediate geometric + systemic change | ✅ Locked |
| 8 | Distant Future is **witness-only** (no placement; observe / inspect result) | ✅ Locked |
| 9 | Era travel = **discrete transition** (map warp point or menu) | ✅ Locked |
| 10 | **No continuous simulation**; Georama is puzzle / constraint-satisfaction based | ✅ Locked |
| 11 | Causality via **Wave Function Collapse** generative pipeline (Past→Present→Future) | ✅ Locked |

---

## The Three Era-Layers

| Era | Owner Hero | Role in Causal Chain | Player Action |
|-----|-----------|----------------------|---------------|
| **Distant Past** | Evoker | Foundational layer | Establish origins / ruins / first settlements |
| **Present** | Machinist | Hub layer (always accessible) | Build the living town; the active base |
| **Distant Future** | Cyborg | Consequence layer | Witness & reap the results of Past + Present |

---

## Causal Flow — Wave Function Collapse Pipeline

Causality is realized **generatively**. Each era-layer is partially hand-placed by the player (anchors + mutators), then **Wave Function Collapse (WFC)** completes the layer consistently. The collapsed output of one layer becomes the input constraint set for the next — so the Distant Future is a deterministic, inspectable consequence of Distant Past choices.

```
DISTANT PAST
  ├─ Player places: terrain pieces + mutators (anchors / constraints)
  └─ WFC COLLAPSE ──▶ generates PRESENT terrain (non-uniform grid)
                                │
PRESENT  (hub)
  ├─ Player places: structures (blueprints) + mutators
  ├─ Must satisfy: Population / Prosperity / Protection
  └─ WFC COLLAPSE ──▶ generates DISTANT FUTURE terrain + structures
                                │
DISTANT FUTURE  (witness-only)
  └─ Player observes the consequence; may inspect causal trace
```

- **Handcrafted anchors** (player placements) = meaning; **WFC fill** = volume. Honors Philosophy Pillar 4 (Procgen for volume; Handcraft for meaning).
- **Visible Causality**: every future feature is traceable to a past anchor ("this Future spire exists because you placed that Past ruin").
- **Distant Future is witness-only** (decision #8): no placement; the player reaps and inspects the generated result.
- **Non-uniform grid**: WFC resolves an organic tile-graph (not a rigid checkerboard), while placement stays grid-like.

### Mutators (constraint pieces)
Player-placed modifiers that bias WFC collapse. Candidate Sets-of-3 taxonomy *(proposed, not yet locked)*:
- **Terrain** mutators — river, mountain, plateau
- **Resource** mutators — ore vein, water source, ley-line
- **Hazard** mutators — corruption seed, fault line, blight

> This extends DC2's Past→Future binary into a 3-layer *generative* cascade — causality is emergent from constraints, not a hand-tuned sim.

---

## Build Conditions (Sets of 3)

Each Georama area is "complete" when its 3 condition axes are satisfied:

| Axis | Meaning | Example Levers |
|------|---------|----------------|
| **Population** | Inhabitants, workers, specialists | Housing, recruitment, amenities |
| **Prosperity** | Resources, economy, culture | Production, trade, culture buildings |
| **Protection** | Defense, resilience, containment | Walls, guards, corruption containment |

> Replaces the brainstorm doc's 4-condition model (Pop/Resources/Terrain/Culture) to honor Sets of 3.

---

## Parametric Blueprints (Sets of 3 axes)

| Axis | Definition |
|------|------------|
| **Form** | Size / style / aesthetic of the structure |
| **Function** | What it produces or enables (output type) |
| **Footprint** | Terrain / adjacency / era-placement constraints |

Blueprints are parametric (not fixed pieces): player tunes the 3 axes within constraints → output building with matching stats/effects.

---

## Causal Integration with Other Pillars

- **Weapon Legacy**: building in an era can forge/modify weapons tied to that era's hero (e.g., Distant Past forge → Evoker weapon Memory).
- **Procedural Seeds**: Georama world-state generates/modifies dungeon Seeds (new biomes, enemy tables, loot from Future state).
- **Creative Crafting**: blueprints require materials/components gathered via dungeon runs and crafting.
- **Mastery**: world completion % across the 3 eras = a mastery track.

---

## Open Items (not yet locked)

- **Mutator taxonomy**: confirm the Terrain / Resource / Hazard Sets-of-3 (or propose alternatives).
- **WFC constraint rules**: tile-compatibility adjacency set; how mutators propagate across layers.
- **Generated-layer → dungeon integration**: how collapsed Present/Future layers seed Procedural Dungeon Seeds / overworld (ties to Procedural Seeds pillar).
- **Causal trace UI**: how the player inspects future←past linkages ("why is this here?").
- **Brainstorm doc reconciliation**: `03_Georama_Systems` (4-era continuous-sim concept) is now superseded by this 3-era WFC model.
