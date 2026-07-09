# Dark Cloud 1 — Dungeon System

## Overview
Procedurally generated dungeons with fixed themes, 10–20 floors each. Key enemy per floor holds progression key. Back-door areas offer risk/reward.

---

## Dungeon List

| # | Name | Floors | Theme | Key Enemy | Boss | New Char |
|---|------|--------|-------|-----------|------|----------|
| 1 | Divine Beast Cave | 15 | Cave/Forest | Lizard Man | Dran (Possessed) | Xiao |
| 2 | Wise Owl Forest | 15 | Forest | Owl Man | King's Curse (Tree) | Goro |
| 3 | Shipwreck | 12 | Water/Ruins | Fish Man | Ship Captain | Ruby |
| 4 | Sun & Moon Temple | 18 | Desert/Temple | Mummy | La Saia | Ungaga |
| 5 | Moon Sea | 15 | Lunar/Cave | Moon People | Minotaur Joe | Osmond |
| 6 | Gallery of Time | 20 | Abstract/Time | Various | Seda / Dark Genie | — |

---

## Procedural Generation

### Floor Structure
```
Entrance Room
    │
    ├─▶ Hallway → Room → Hallway → Room → ... → Key Room
    │                │
    │                ├─▶ Side Room (loot)
    │                ├─▶ Healing Spring (rare)
    │                └─▶ Back Door (rare)
    │
    └─▶ Exit Room (Key used here) → Next Floor
```

### Generation Parameters
| Parameter | Range | Notes |
|-----------|-------|-------|
| Room count | 8–15 | Scales with floor |
| Room templates | 15–25 per theme | Reused across floors |
| Enemy groups | 3–8 per floor | Themed tables |
| Atla spheres | 1–3 | Guaranteed on key floors |
| Back door chance | 10% per floor | Higher in later dungeons |

### Room Templates (Per Theme)
| Theme | Room Types |
|-------|------------|
| Cave | Rough cavern, crystal chamber, lava pool, mushroom grove |
| Forest | Glade, hollow tree, stream crossing, ruins |
| Water | Flooded hall, ship deck, coral garden, air pocket |
| Desert | Sand dunes, pillar hall, trap corridor, oasis |
| Lunar | Crater, crystal spire, low-grav chamber, monolith |

---

## Key Enemy & Floor Key

### Mechanics
- **One enemy per floor** carries the **Floor Key**
- **No visual indicator** — must defeat enemies until key drops
- **Key drop rate** — 100% from key enemy; 0% from others
- **Strategy**: Clear all enemies (safest) or speedrun hunting key carrier

### Key Enemy Behavior
- **Standard AI** — No special behavior; doesn't flee
- **Can be any enemy type** on that floor
- **Back door floors** — Key enemy often mini-boss tier

---

## Special Floor Types

| Type | Frequency | Features |
|------|-----------|----------|
| **Standard** | 70% | Normal enemies, 1–2 Atla |
| **Back Door** | 10% | Tougher enemies, better loot, 2–3 Atla |
| **Healing Spring** | 5% | Full HP + Thirst restore; safe zone |
| **Mini-Boss** | 5% | Unique enemy; drops rare attachment |
| **Event/Story** | 10% | Fixed layout; cutscene; boss at end |

### Back Door Details
- **Access**: Random staircase appears in standard room
- **Enemies**: +5–10 levels; new variants (red palette)
- **Loot**: High-tier attachments, crystals, repair powders
- **Risk**: No save inside; death = return to village, lose gold

---

## Enemy Design

### AI Behaviors
| Type | Behavior |
|------|----------|
| **Melee** | Approach → Attack → Retreat |
| **Ranged** | Maintain distance → Shoot → Strafe |
| **Charger** | Wind up → Rush (unblockable) → Recover |
| **Caster** | Float → Cast spell (telegraphed) → Cooldown |
| **Swarm** | Group rush; individual weak |

### Monster Families (Anti-Type Targets)
| Family | Members | Weakness Crystal |
|--------|---------|------------------|
| **Beast** | Rats, Wolves, Lions | Beast Crystal |
| **Scale** | Lizards, Dragons, Turtles | Scale Crystal |
| **Undead** | Skeletons, Zombies, Ghosts | Exorcism Crystal |
| **Armored** | Golems, Turtles, Knights | Smash Crystal |
| **Flying** | Bats, Birds, Insects | Cyclone Crystal |
| **Aquatic** | Fish, Crabs, Frogs | — (elemental) |

---

## Dungeon Resources

### Consumables Found
| Item | Floors | Use |
|------|--------|-----|
| Repair Powder | All | Restore WHP |
| Water (all) | All | Thirst |
| Healing Items | All | HP |
| Status Cures | Mid+ | Poison, Curse, etc. |
| Attachments | Mid+ | Weapon synthesis |
| Crystals | Late | Elemental/anti-type |
| Gourds / Fruits | Rare | Permanent stats |
| Keys | Key enemy only | Floor exit |

### Atla Distribution
| Dungeon | Total Atla | Per Floor Avg |
|---------|------------|---------------|
| Divine Beast Cave | 45 | 3.0 |
| Wise Owl Forest | 52 | 3.5 |
| Shipwreck | 38 | 3.2 |
| Sun & Moon Temple | 65 | 3.6 |
| Moon Sea | 50 | 3.3 |
| Gallery of Time | 0 (story) | — |

---

## Boss Design

| Boss | Phase 1 | Phase 2 | Weakness | Strategy |
|------|---------|---------|----------|----------|
| **Dran** | Melee swings | Fire breath | Ice | Xiao ranged; dodge charges |
| **King's Curse** | Root spawns | Tree form | Fire | Goro hammer; burn roots |
| **Ship Captain** | Gun + summons | Ghost ship | Holy | Ruby exorcism; Osmond gun |
| **La Saia** | Sand clones | True form | Water | Ungaga staff; hit real one |
| **Minotaur Joe** | Charge + axe | Enraged speed | Wind | Xiao cyclones; kite |
| **Dark Genie** | Multi-form | True Genie | All | Maxed ultimate weapons |

---

## Pacing & Difficulty Curve

| Dungeon | Avg Floor Time | Recommended Weapon Lvl | Key Challenge |
|---------|----------------|------------------------|---------------|
| Divine Beast Cave | 5 min | +1 to +3 | Learning systems |
| Wise Owl Forest | 8 min | +3 to +5 | River reconstruction |
| Shipwreck | 10 min | +5 to +8 | Water navigation, Ruby join |
| Sun & Moon Temple | 12 min | +8 to +12 | Desert, dual bosses |
| Moon Sea | 15 min | +12 to +18 | Lunar gravity, Osmond |
| Gallery of Time | 20 min | +18 to Max | Marathon, no Georama |

---

## Overseas Version Changes
- **Extra enemy variants** per dungeon (+2–3 per theme)
- **Improved pathfinding** — enemies don't get stuck on geometry
- **Additional back door rooms** — more variety
- **Demon Shaft** (post-game) — 100 floors; infinite; best grinding

---

## Design Analysis

### Strengths
- **Clear objective** — Find key → exit (no ambiguity)
- **Risk/reward** — Back doors optional but lucrative
- **Thematic variety** — Each dungeon feels distinct
- **Character gating** — New traversal unlocks dungeon secrets

### Weaknesses
- **Visual repetition** — 15 floors of same tileset = fatigue
- **Key hunting RNG** — Can be first or last enemy; no skill expression
- **No map persistence** — Layout regenerates each entry (can't learn)
- **Spring rarity** — Thirst management feels arbitrary, not tactical

### DC2 Improvements
- **Medal objectives** — Time Trial, Wipe Out, Spheda, Fishing per floor
- **Map persistence** — Pau (support char) reveals full map
- **Donny** — Unlocks all doors/chests (removes key hunting)
- **Spheda/Fishing** — Alternative floor activities

