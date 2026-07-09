# Dark Cloud 1 — Georama System

## Overview

The **Georama** is a town-building mode where players reconstruct villages from Atla spheres collected in dungeons. It transforms abstract dungeon rewards into visible, interactive 3D communities.

---

## Atla → Georama Pipeline

```
DUNGEON                          VILLAGE
┌─────────────┐                  ┌─────────────┐
│ Atla Sphere │ ──(Toan only)──▶ │   Atla      │
│  (Red/Green)│                  │  Inventory  │
└─────────────┘                  └──────┬──────┘
                                        │
                                        ▼
                               ┌─────────────────┐
                               │  ASSEMBLE       │
                               │  (Auto-complete │
                               │   when parts    │
                               │   collected)    │
                               └────────┬────────┘
                                        │
                                        ▼
                               ┌─────────────────┐
                               │  PLACEMENT MODE │
                               │  (Select + Grid)│
                               └────────┬────────┘
                                        │
                    ┌───────────────────┼───────────────────┐
                    ▼                   ▼                   ▼
            ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
            │  Buildings  │     │  Villagers  │     │  Nature     │
            │  (Houses,   │     │  (NPCs with │     │  (Trees,    │
            │   Shops,    │     │   requests) │     │   Rivers,   │
            │   Windmill) │     │             │     │   Hills)    │
            └─────────────┘     └─────────────┘     └─────────────┘
```

---

## Placement Mechanics

### Grid System
- **Tile-based** — Square grid; each piece occupies 1×1 to 4×4 tiles
- **Rotation** — 90° increments; some pieces asymmetric (entrance facing)
- **Collision** — No overlap; must place on valid terrain (flat, raised, water)
- **Terrain types** — Grass, Dirt, Sand, Water, Raised Earth (1–3 height levels)

### Building Assembly
1. **Collect all parts** — Frame, roof, door, windows, interior items, sign
2. **Auto-assembles** — When complete, becomes single "Building" object
3. **Place building** — Select from menu → position on grid → confirm
4. **Place villagers** — After building placed, assign NPC to it

### Villager Requests
Each NPC has **1–2 placement wishes**:
| Request Type | Example | Reward |
|--------------|---------|--------|
| Proximity | "Near the pond" | Item / Shop unlock |
| Avoidance | "Far from the noisy Macho family" | Item |
| Orientation | "Entrance facing east" | Item |
| Adjacency | "Next to the shop" | Item |
| Terrain | "On raised ground" | Item |

### Completion Tracking (Georama Analysis Menu)
Three percentages per village:
| Track | Source | 100% Effect |
|-------|--------|-------------|
| **Collection** | Atla found / Total Atla in dungeon | Required for next dungeon |
| **Reconstruction** | Pieces placed / Total pieces | Required for next dungeon |
| **Requests** | Wishes fulfilled / Total wishes | **Bonus reward** (unique item/skill) |

> **Note**: Only Collection + Reconstruction at 100% unlocks next area. Requests are optional but highly rewarded.

---

## Village Progression

| Village | Dungeon | Key Features | 100% Request Reward |
|---------|---------|--------------|---------------------|
| **Norune** | Divine Beast Cave | Tutorial; Toan's house, Dran's windmill | Toan: Spin Slash skill |
| **Matataki** | Wise Owl Forest | River system; Goro joins | Goro: Battle Axe (→ Inferno path) |
| **Queens** | Shipwreck | Port town; Ruby joins | Ruby: Witch Parfait (defense) |
| **Muska Lacka** | Sun & Moon Temple | Desert; Ungaga joins | Ungaga: ? |
| **Brownboo** | Gallery of Time | Moon People; Osmond joins | Osmond: ? |
| **Yellow Drops** | Moon Sea | Moon city; Sun Giant parts | ? |
| **Gallery of Time** | (Story) | Seda's past; not a rebuild village | — |

---

## Georama Rewards (100% Requests)

| Village | Character | Reward | Significance |
|---------|-----------|--------|--------------|
| Norune | Toan | **Spin Slash** | Only AoE melee skill; high WHP cost |
| Matataki | Goro | **Battle Axe** | Only weapon evolving to **Inferno** (ultimate) |
| Queens | Ruby | **Witch Parfait** | +5-7 Defense (save-scum for +7) |
| Muska Lacka | Ungaga | **Frill Neck** / **Sandstorm** | Key weapon / defense item |
| Brownboo | Osmond | **Sun & Moon Badge** | Story/collection |
| Yellow Drops | — | **Sun Giant** parts | Story progression |

---

## Advanced Mechanics

### Placement Strategy
- **Water flow** — Rivers must connect source → sink; villager requests often reference
- **Roads/Paths** — Cosmetic but some requests: "Near the road"
- **Raised Earth** — Limited tiles; high-demand for "view" requests
- **Shop placement** — Unlocks inventory; place centrally for villager access logic

### Georama Menu (Select Button)
| Option | Function |
|--------|----------|
| **Build** | Place assembled pieces |
| **Move** | Relocate placed pieces |
| **Rotate** | Rotate selected piece |
| **Status** | View villager requests + completion % |
| **Analysis** | View Collection/Reconstruction/Request % |
| **Exit** | Return to gameplay |

---

## Overseas Version Changes
| Change | Impact |
|--------|--------|
| **Georama Analysis** shows request % per villager | Easier to track individual wishes |
| Extra Atla in some dungeons | Slightly easier 100% collection |
| Additional decorative pieces | More cosmetic variety |

---

## Design Analysis

### Strengths
- **Tangible progression** — Empty plain → living village in real-time 3D
- **Logic puzzle** — Requests create spatial reasoning challenge
- **Emotional payoff** — Villagers thank you; music changes; village feels alive
- **Replayability** — Multiple valid layouts; optimization for 100%

### Weaknesses (DC1)
- **Limited piece variety** — Same house models reused
- **Grid rigidity** — No free-form placement; rotation snaps
- **Request opacity** — Must talk to each NPC repeatedly; no quest log
- **No gameplay impact** — Shops only; no defense, no crafting, no simulation

### DC2 Evolution (Preview)
- **Geostones → Blueprints → Materials → Build** (more steps, more agency)
- **Culture Points** — Quantitative town quality metric
- **Time Travel** — Past placement affects Future state
- **Functional buildings** — Shops, factories, farms produce resources

