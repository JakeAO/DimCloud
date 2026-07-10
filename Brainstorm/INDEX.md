# Brainstorm — Successor Design Documentation

This folder contains all speculative design content for the Dark Cloud spiritual successor (codename: DimCloud). Content here is **non-canon theorycraft** — ideas, proposals, and design exploration.

## Folder Structure

```
Brainstorm/
├── INDEX.md                    # This file
├── Locked/                     # Canonical design decisions (locked in)
│   ├── 01_Design_Pillars.md    # Core vision, pillars, mantras
│   └── 02_Design_Philosophy.md # Hino's principles, anti-pillars
├── 02_Weapon_Systems/          # Weapon system evolution concepts
├── 03_Georama_Systems/         # Georama system evolution concepts
├── 04_Core_Loops/              # Core loop comparison and density
├── 05_Engine_Architecture/     # Engine v5.0 architecture target
├── 06_Rendering_Pipeline/      # Cel-shading + modern pipeline
├── 07_Systems_Integration/     # Cross-pillar synergies
└── 08_Project_Planning/        # Development roadmap
```

## Content Guidelines

### Locked/ Folder
Contains decisions that have been **approved and finalized**. These are the canonical design choices for the successor. Content here should not be changed without explicit discussion.

### Other Folders
Contains **active brainstorming** — ideas that are being explored but not yet finalized. These may be modified, merged, or discarded as design evolves.

## Current Locked Decisions

| Decision | Status | Notes |
|----------|--------|-------|
| 5 Design Pillars | ✅ Locked | Weapon Legacy, Causal Georama, Creative Crafting, Mastery Progression, Procedural Seeds (Companion Ecosystem removed) |
| Design Philosophy | ✅ Locked | 7 principles from Hino's interviews, anti-pillars identified |
| Sets of 3 | ✅ Locked | Foundational rule: every major system offers 3 choices, phases, or sub-components |
| 3 Protagonists | ✅ Locked | Evoker (Distant Past) / Machinist (Present) / Cyborg (Distant Future); 3 stances each; free-roam + char-lock exceptions; separate arsenals, global essences/traits. See `Locked/03_Characters.md` |
| Companion Pillar Removed | ✅ Locked | Cut entirely. No allies/monsters/vehicles as companions. Trio hot-swap only; DC2 monster/ridepod flavor folded into stances. See `Locked/03_Characters.md` |
| Combat Foundation | ✅ Locked | 9 weapons (1/stance), universal move kit, stance archetypes, Resonance model, Defensive 2-Option (Block/Dodge + Perfect). See `Locked/04_Combat_Foundation.md` |
| Causal Georama | ✅ Locked | 3 era-layers, WFC generative cascade (Past→Present→Future), witness-only Future, discrete travel, puzzle/constraint-based (no sim), 3 condition + 3 blueprint axes. See `Locked/05_Causal_Georama.md` |
| Procedural Seeds | ✅ Locked | Local deterministic seeds (Dungeon+Stage+Attempt); no share/multiplayer/parity; 3 tiers (Std/Heroic/Mythic); 3 challenges/stage from broad objective pool; Georama state drives content. See `Locked/06_Procedural_Seeds.md` |
