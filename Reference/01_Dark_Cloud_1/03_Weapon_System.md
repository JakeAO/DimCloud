# Dark Cloud 1 — Weapon System

## Overview
**Core Philosophy**: "Characters don't level. Weapons do." Each of 6 characters wields one weapon type. Weapons gain ABS (XP) from kills, level up, absorb attached items, and evolve through Build Up paths.

---

## Weapon XP System

### ABS (Absorption Points)
| Source | Amount |
|--------|--------|
| Standard kill | ~10–50 ABS (scales with enemy level) |
| Back-door enemy | 1.5–2× |
| Boss kill | Large lump sum |

### ABS Gauge & Level Up
- Blue bar on weapon status screen
- When full → **Upgrade** option available
- Upgrade consumes attached items → permanent stat gains
- Weapon name gains `+1`, `+2`, etc.
- **Synthesis Points (SP)** granted: +3 early, +4–5 at higher tiers

### Abs Up Attachment
- **Effect**: 1.5× ABS gain
- **Strategy**: Equip on grinding weapons; swap off for boss fights

---

## Attachments (Synthesis Items)

### Slot System
- Each weapon has **fixed slot count** (3–6)
- Attachments occupy slots until weapon Upgrades
- On Upgrade: all attached items **absorbed permanently** → slots freed

### Attachment Categories

| Category | Items | Effect |
|----------|-------|--------|
| **Stat Crystals** | Power / Endurance / Speed Crystal | +Atk / +WHP / +Spd (permanent on upgrade) |
| **Elemental Crystals** | Fire / Ice / Lightning / Wind / Holy | Add elemental damage |
| **Anti-Type Crystals** | Beast / Scale / Exorcism / Smash / Cyclone | ×1.5–2.0 damage vs family |
| **Utility** | Abs Up, Steal, Critical, Knockback, Drain | Special effects |

### Attachment Values (Typical)
| Item | Atk | WHP | Spd | Element | Anti-Type |
|------|-----|-----|-----|---------|-----------|
| Power Crystal | +3 | — | — | — | — |
| Endurance Crystal | — | +5 | — | — | — |
| Speed Crystal | — | — | +2 | — | — |
| Fire Crystal | — | — | — | +5 Fire | — |
| Beast Crystal | — | — | — | — | +10 Beast |
| Abs Up | — | — | — | — | — (1.5× ABS) |

---

## Build Up (Weapon Evolution)

### Mechanism
- Every weapon (except starter) has **1–3 evolution paths**
- Requirements shown in **Build Up screen** — stats in **red** must reach threshold
- When all red stats met → **Build Up** button flashes
- Evolution: Weapon transforms → **resets to Level 1** → keeps all absorbed stats → new base stats + new growth curve

### Evolution Tree Example (Toan — Swords)
```
Chronicle 1 (starter)
    │
    ├─→ Chronicle 2 → Chronicle 3 → ... → Chronicle Sword (final)
    │
    ├─→ Sword of Zeus → Thunder Sword → ... → Atlamillia Sword
    │
    └─→ Macho Sword → ... → (multiple branches)
```

### Stat Requirements (Sample)
| Weapon | Build Up Target | Red Stats Required |
|--------|-----------------|-------------------|
| Battle Wrench | True Battle Wrench | Atk 8→13 |
| True Battle Wrench | Drill Wrench | Atk 13→18, Smash +5 |
| Battle Wrench | (alt) Heavy Wrench | Atk 8→12, Dur +10 |

### Evolution Rules
- **Multiple paths**: Some weapons branch (choice matters)
- **Convergence**: Different bases can evolve into same weapon (base stats differ)
- **Final forms**: No further Build Up; max stats capped
- **SynthSphere transfer**: +5 weapon → SynthSphere (60% stats) → attach to another

---

## SynthSphere (Spectrumization)

### Creation
- Weapon must be **+5 or higher**
- Menu: **Status Break** → Weapon consumed → **SynthSphere** created
- SynthSphere holds **~60% of weapon's stats + abilities**

### Usage
- SynthSphere consumes **SP = weapon's +level** (e.g., +5 = 5 SP)
- Attach to target weapon → transfers stats
- Can upgrade with SynthSphere attached → makes stats permanent
- **Strategy**: Level disposable weapon → SynthSphere → transfer to main

### Transfer Efficiency
| Source Weapon Level | Stat Transfer Rate |
|---------------------|-------------------|
| +5 | ~60% |
| +10 | ~65% |
| +15 | ~70% |
| +20 | ~75% |

---

## Weapon Hit Points (WHP) / Durability

### Mechanics
- **Melee hit**: -1 WHP
- **Ranged shot**: -1 WHP
- **Charge attack**: -2 WHP
- **WHP = 0**: Weapon **destroyed permanently** (except starter weapons)
- **Repair Powder**: Restores ~30–50 WHP (instant, menu or hotkey)

### WHP Values by Tier
| Tier | Base WHP | Max (with Endurance Crystals) |
|------|----------|------------------------------|
| Starter | 50–80 | ~150 |
| Mid-game | 100–200 | ~300 |
| Late-game | 250–400 | ~500 |
| Ultimate | 500+ | ~700 |

### Overseas Version Change
- **JP**: Broken weapon = **deleted from inventory**
- **US/EU**: Broken weapon = **kept at 0 WHP**, repairable (but loses ABS)
- **DC2**: Further softened — broken weapon retained, only loses some ABS

---

## Character Weapon Types

| Character | Weapon Type | Range | Traversal Ability |
|-----------|-------------|-------|-------------------|
| **Toan** | Swords / Daggers | Melee | None (main char) |
| **Xiao** | Slingshots | Ranged | **Jump** (cross gaps) |
| **Goro** | Hammers / Axes | Melee | **Break Rocks** |
| **Ruby** | Magic Rings | Ranged | **Fly** (short hover) |
| **Ungaga** | Staves / Spears | Melee | **Sandwalk** (quicksand) |
| **Osmond** | Guns / Blasters | Ranged | **Unlock Doors** |

### Weapon Counts (Approx)
| Character | Base Weapons | Evolved Forms | Total Unique |
|-----------|--------------|---------------|--------------|
| Toan | 12 | 25+ | ~35 |
| Xiao | 8 | 15+ | ~22 |
| Goro | 10 | 20+ | ~28 |
| Ruby | 8 | 15+ | ~22 |
| Ungaga | 9 | 18+ | ~25 |
| Osmond | 10 | 20+ | ~28 |

---

## Optimization Strategies

### Early Game
1. **Focus one main weapon** per character
2. **Abs Up** attachment always equipped while grinding
3. **Element matching** — farm crystals for current dungeon's enemy types
4. **Repair management** — carry 10+ Repair Powders per dungeon run

### Mid Game
1. **Build disposable weapons** to +5 → SynthSphere → transfer to main
2. **Anti-type crystals** for boss prep (Exorcism for undead, etc.)
3. **Character-specific defense items** — Fruit of Eden / Gourds allocated to mains

### Late Game
1. **Ultimate weapon paths** — plan Build Up requirements early
2. **SynthSphere chaining** — +20 weapon → SynthSphere → +20 another → combine
3. **Backup weapons** — always have +5 spare for emergency SynthSphere

---

## Reference: Key Weapons by Character

### Toan (Swords) — Ultimate Paths
| Final Weapon | Build Path | Notable Req |
|--------------|------------|-------------|
| **Atlamillia Sword** | Macho Sword → ... | Atk 50+, Holy 30+ |
| **Chronicle Sword** | Chronicle 1 → 2 → 3 → ... | Balanced high stats |
| **Sword of Zeus** | Thunder line | Lightning 40+, Atk 45+ |

### Goro (Hammers) — Ultimate Paths
| Final Weapon | Build Path | Notable Req |
|--------------|------------|-------------|
| **Inferno** | Battle Ax → True Battle Ax → ... | Fire 30+, Smash 20+ |
| **Goro's Hammer** | Chronicle line | Balanced |

### Xiao (Slingshots) — Ultimate Paths
| Final Weapon | Build Path | Notable Req |
|--------------|------------|-------------|
| **Dragon's Y** | Bone Slingshot → Flamingo → ... | Wind 25+, Cyclone 15+ |

---

## Weapon Attributes (10 Core Stats)

| Attribute | Abbrev | Effect |
|-----------|--------|--------|
| Attack | ATK | Base damage |
| Durability | DUR | WHP max / decay rate |
| Flame | FLA | Fire damage |
| Chill | CHI | Ice damage |
| Lightning | LIG | Lightning damage |
| Cyclone | CYC | Wind damage (vs flying) |
| Smash | SMA | vs Armored (turtles, golems) |
| Exorcism | EXO | vs Undead |
| Beast | BEA | vs Beasts |
| Scale | SCA | vs Dragons/Reptiles |

### Attribute Caps
- Each weapon has **max value per attribute** (varies by weapon tier)
- Synthesis cannot exceed cap
- Evolution resets level but **raises caps**

---

## Reference Data (JSON)
```json
{
  "weaponTypes": 6,
  "characters": 6,
  "maxLevel": 99,
  "synthSphereUnlockLevel": 5,
  "absMultiplierAbsUp": 1.5,
  "startingSynthesisPoints": 3,
  "attributeCount": 10
}
```

---

## Design Analysis

### Strengths
- **Weapon as character** — Growth feels personal; loss hurts
- **Build diversity** — Multiple evolution paths per weapon type
- **SynthSphere economy** — Recycling creates long-term planning
- **Risk/reward** — Durability forces preparation vs. greed decisions

### Weaknesses
- **Opacity** — Build Up requirements hidden until near-complete
- **Grind** — ABS farming repetitive; no auto-battle / speed-up
- **Inventory pressure** — Attachments + repair + water + items = full bags
- **Permadeath trauma** — Losing +15 weapon feels terrible (JP version)

### DC2 Improvements
- Broken weapon **retained** (loses ABS only)
- **Synthesis Points** replace slots — more flexible
- **Spectrumize** any item (not just +5 weapons)
- **Weapon evolution trees visible** in-game (sword growth chart)
- **Ridepod** — separate customizable weapon platform

