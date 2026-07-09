# Dark Cloud 2 — Weapon System 2.0 (Synthesis Points & Spectrumize)

## Overview
DC2 evolves DC1's weapon system: **Synthesis Points (SP) replace slots**, **Spectrumize any item** (not just +5 weapons), **Build Up trees visible in-game**, **Durability forgiving** (broken weapons kept).

---

## Core Changes from DC1

| System | DC1 | DC2 |
|--------|-----|-----|
| **Attachment Capacity** | Fixed slots (3–6) | **Synthesis Points (SP)** — Variable per level |
| **Spectrumize Source** | Only +5 weapons → SynthSphere | **Any item** → SynthSphere (weapons, crystals, items) |
| **SynthSphere Cost** | SP = Weapon +Level | SP = Item's **Synth Cost** (1–20+) |
| **Weapon Breakage** | Destroyed (JP) / Kept at 0 WHP (Overseas) | **Kept; loses ~10% ABS only** |
| **Evolution Visibility** | Hidden until stats met | **Full tree shown** (Sword Growth Chart) |
| **Dual Weapons** | 1 per character | **2 per character** (Melee + Ranged) |
| **Ridepod** | N/A | **Separate customizable weapon platform** |

---

## ABS & Leveling (Unchanged Core)

### ABS Gain
- **Final blow weapon** gets ABS (blue orbs)
- **Party members** — Only active character's weapon gains ABS
- **Support Characters** — Some boost ABS gain (Gerald, Milane, Lin)

### Level Up
- ABS Gauge fills → **Auto Level Up** (no menu confirm)
- **SP Gained**: +3 early, +4 mid, +5 late
- **Stat Gains**: Atk +1–2, Dur +1–2 per level (varies by weapon)

---

## Synthesis Points (SP) System

### SP as Capacity
- Each weapon has **Current SP / Max SP**
- **Max SP** increases on Level Up
- **Attaching SynthSphere costs SP** = Sphere's Synth Cost
- **Cannot exceed Max SP**

### SP Management
| Action | SP Cost |
|--------|---------|
| Attach SynthSphere (1-cost) | 1 |
| Attach SynthSphere (5-cost) | 5 |
| Attach +5 Weapon Sphere | 5 |
| Attach +10 Weapon Sphere | 10 |
| **Detach** | **Free** (Sphere returns to inventory) |

> **Key Difference from DC1**: Detaching is **free and lossless**. Experiment freely.

### SP Boosters (Support Characters)
| Character | Boost | Weapon Types |
|-----------|-------|--------------|
| **Gerald** (Max's Dad) | +1 SP/Level | Max's **Guns** |
| **Milane** | +1 SP/Level | Monica's **Swords** |
| **Lin** | +1 SP/Level | Monica's **Armbands** (temp) |
| **Adel** | Slows WHP decay | **Unequipped** weapons |

---

## Spectrumize (The Universal Converter)

### What Can Be Spectrumized
| Category | Examples | Synth Cost | Typical Stat Transfer |
|----------|----------|------------|----------------------|
| **Crystals** | Power/Endure/Speed/Element/Anti-Type | 1–3 | Single stat +5–15 |
| **Items** | Fruits, Gems, Enemy Drops, Fish | 1–5 | Specific stats |
| **Weapons** | Any level (but <+5 = "Unstable") | = Weapon Level | **~60% of weapon's stats** |
| **Ridepod Parts** | Legs, Arms, Body, Weapons | 3–10 | Part-specific stats |

### Spectrumize Rules
1. **Weapon < +5** → **"Unstable SynthSphere"** — Warning: low transfer rate (~20%)
2. **Weapon ≥ +5** → **Stable SynthSphere** — ~60% transfer + abilities
3. **Abilities Transfer** — Critical, Steal, Abs Up, Element Max, etc.
4. **Multiple Items** — Can Spectrumize 5× Power Crystal → 1 Sphere (Cost 5, +25 Atk)

### Spectrumize UI Flow
```
Item Menu → Select Item → "Spectrumize" → Confirm → SynthSphere appears in empty slot
     │
     ▼
Weapon Menu → Select Weapon → "Status" → Check SP → Select SynthSphere → "Synthesize"
     │
     ▼
Weapon absorbs stats → SP reduced → SynthSphere consumed
```

---

## Build Up (Weapon Evolution)

### Visible Evolution Trees
- **Weapon Menu → Build Up** shows **full tree** with all branches
- **Red Stats** = Requirements not met
- **White Stats** = Requirements met
- **Flash "Build Up"** when all requirements met

### Evolution Mechanics
| Aspect | Detail |
|--------|--------|
| **Reset Level** | Evolved weapon starts at Level 1 (0 ABS) |
| **Retain Stats** | All absorbed stats **kept** |
| **New Base Stats** | Higher base; new growth curve |
| **New SP Curve** | Often better SP/Level |
| **Branching** | 2–4 paths per weapon (e.g., Battle Wrench → True Battle Wrench OR Drill Wrench) |

### Example: Max's Wrench Tree (Simplified)
```
Battle Wrench (Start)
    │
    ├─ Atk 13 → True Battle Wrench
    │       │
    │       ├─ Atk 18, Smash 10 → Drill Wrench
    │       │
    │       └─ Atk 18, Lightning 15 → Thunder Wrench
    │
    └─ Fire 10, Smash 8 → Flame Wrench
            │
            └─ Fire 20, Atk 20 → Inferno Wrench (Ultimate)
```

### Monica's Dual Trees
| Weapon Type | Ultimate Paths |
|-------------|----------------|
| **Swords** | Chronicle → Atlamillia / Sword of Zeus / Dark Cloud Sword |
| **Armbands** | Himarra → Mandora / Scarecrow (Monster Badge evolutions) |

---

## Ridepod (Steve) — Separate Weapon System

### Steve as Weapon Platform
- **Not a character** — Equipped like a weapon (R-Stick click to mount)
- **Own ABS, Level, SP, WHP** — Independent of Max/Monica
- **Customizable Parts** — Body, Legs, Arms, Weapon (Melee), Weapon (Ranged)

### Part Categories
| Slot | Types | Effect |
|------|-------|--------|
| **Body** | Standard, Heavy, Light, Ultimate | HP, Defense, SP Curve |
| **Legs** | Walker, Roller, Hover, Propeller, Jet | Speed, Terrain, Jump |
| **Arms** | Claw, Drill, Beam, Missile | Melee Dmg, Range, Element |
| **Melee Weapon** | Hammer, Sword, Drill, Fist | Primary Attack |
| **Ranged Weapon** | Gun, Cannon, Laser, Missile | Secondary Attack |

### Steve Progression
1. **Invention** — Photograph objects → Idea Card → Assemble Parts
2. **Purchase** — Cedric's shop (unlocks per chapter)
3. **Spectrumize Parts** — Like weapons; transfer stats to other parts
4. **Fuel** — Energy Pack (invented) → Steve operates; depletes in combat

---

## Durability (WHP) — Forgiving Model

| Scenario | DC1 (Overseas) | DC2 |
|----------|----------------|-----|
| WHP → 0 | Weapon kept at 0 WHP | Weapon kept; **loses ~10% ABS** |
| Repair | Repair Powder (anytime) | Repair Powder (anytime) |
| Broken in Boss | Reload or fight barehanded | Continue with weakened weapon |
| Unequipped Decay | None | **Adel** (support) slows decay |

### Repair Items
| Item | Restores | Source |
|------|----------|--------|
| Repair Powder | ~50 WHP | Shops, Chests |
| Gun Repair Powder | ~50 WHP | Shops, Chests |
| Armband Repair Powder | ~50 WHP | Shops, Chests |
| Ridepod Repair | ~100 WHP | Invented / Cedric |

---

## Character Weapon Loadouts

### Max (Melee + Ranged + Steve)
| Slot | Weapon Types | Notes |
|------|--------------|-------|
| **Right Hand (Melee)** | Wrenches, Hammers, Swords, Drills | Primary DPS; Steve melee separate |
| **Left Hand (Ranged)** | Guns, Cannons, Lasers, Missiles | Ammo = WHP; Steve ranged separate |
| **Steve** | Ridepod (Body/Legs/Arms/Weapons) | **Separate entity**; mount/dismount |

### Monica (Melee + Ranged + Monster)
| Slot | Weapon Types | Notes |
|------|--------------|-------|
| **Right Hand (Melee)** | Swords, Katanas, Special | Standard melee |
| **Left Hand (Ranged)** | Armbands (Magic) | Elemental spells; MP = WHP |
| **Monster Form** | 12 Badges | **Replaces Monica**; own stats/skills |

---

## Weapon Attributes (10 Stats)

| Attribute | Abbrev | Effect |
|-----------|--------|--------|
| **Attack** | ATK | Base damage |
| **Durability** | DUR | Max WHP; decay rate |
| **Flame** | FLA | Fire damage |
| **Chill** | CHI | Ice damage |
| **Lightning** | LIG | Lightning damage |
| **Cyclone** | CYC | Wind damage (vs Flying) |
| **Smash** | SMA | vs Armored (Turtle, Golem) |
| **Exorcism** | EXO | vs Undead |
| **Beast** | BEA | vs Beasts |
| **Scale** | SCA | vs Dragons/Reptiles |

### Attribute Caps
- **Per Weapon Tier** — Higher tier = higher caps
- **Spectrumize cannot exceed cap** — Excess wasted
- **Build Up raises caps** — New tier = new limits

---

## Optimization Strategies

### Early Game (Ch. 1–2)
1. **Focus one melee + one ranged per character**
2. **Spectrumize every crystal** you find → Main weapon
3. **Abs Up SynthSphere ASAP** — Farm from weak enemies
4. **Don't evolve yet** — Level base weapons to +5 for Spheres

### Mid Game (Ch. 3–5)
1. **Build +5 disposable weapons** → Spectrumize → Transfer to mains
2. **Recruit Gerald/Milane/Lin** — SP boosts critical
3. **Steve Fuel** — Invent Energy Pack; Steve = free DPS
4. **Element Matching** — Spectrumize dungeon's dominant element

### Late Game (Ch. 6–8 + Post)
1. **Ultimate Weapon Paths** — Follow Build Up tree to final form
2. **SynthSphere Chaining** — +20 Weapon → Sphere (12 SP) → +20 Another
3. **Steve Ultimate** — Sun & Moon Armor, Jet Hover, Ultimate Cannon
4. **Monster Badges** — Max all 12 for Monica's forms

---

## Reference Data (JSON)

```json
{
  "maxSPPerLevel": {"early": 3, "mid": 4, "late": 5},
  "spectrumizeTransferRate": {"stable": 0.6, "unstable": 0.2},
  "weaponTypes": {
    "Max": {"melee": ["Wrench","Hammer","Sword","Drill"], "ranged": ["Gun","Cannon","Laser","Missile"], "ridepod": true},
    "Monica": {"melee": ["Sword","Katana"], "ranged": ["Armband"], "monster": 12}
  },
  "supportSPBoosts": {
    "Gerald": {"target": "Max Guns", "bonus": 1},
    "Milane": {"target": "Monica Swords", "bonus": 1},
    "Lin": {"target": "Monica Armbands", "bonus": 1, "temp": true},
    "Adel": {"target": "Unequipped", "effect": "WHP_Decay_Slow"}
  },
  "durabilityLossOnBreak": 0.10,
  "buildUpResetLevel": true,
  "detachCost": 0
}
```

---

## Design Analysis

### Improvements Over DC1
- **SP > Slots** — Flexible; no "wasted slot" frustration
- **Universal Spectrumize** — Every item has potential use; no vendor trash
- **Visible Trees** — Player agency; no wiki required
- **Forgiving Durability** — Removes "fear of using best weapon"
- **Detach Free** — Encourages experimentation
- **Steve** — Entire second progression system; deep customization

### Remaining Issues
- **SP Scarcity Mid-Game** — Before Gerald/Milane, SP tight
- **Synth Cost Opacity** — Item Synth Cost not shown until Spectrumized
- **Steve Fuel Management** — Extra resource to track; can stall Steve use
- **Armbands Weak** — Monica's ranged underpowered vs Max's guns
- **Grind for Ultimate** — +20 weapons need massive ABS; Demon Shaft required
