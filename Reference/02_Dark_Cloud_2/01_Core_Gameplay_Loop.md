# Dark Cloud 2 — Core Gameplay Loop

## Overview
DC2 evolves the DC1 loop with **time travel causality**: Past Georama → Future Dungeon changes. Dual protagonists (Max/Monica), Ridepod, Invention system, and Medal objectives create a denser systems web.

---

## The Core Loop (Visual)

```
┌─────────────────────────────────────────────────────────────────────┐
│                        DUNGEON FLOOR                                │
│  • Procedural layout (themed)                                       │
│  • Real-time combat (Max: Wrench/Gun/Ridepod | Monica: Sword/Armband/Monster) │
│  • Medal Objectives: Time Trial / Wipeout / Spheda / Fishing       │
│  • Geostones → Carpenterion → Blueprints                           │
│  • Photography → Ideas → Inventions                                 │
│  • Defeat Key Enemy → Floor Key → Next Floor                       │
└────────────────────────────┬────────────────────────────────────────┘
                             │ Exit / Save
                             ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      GEORAMA (Past Era)                             │
│  • Place blueprints using Materials (bought/found)                 │
│  • Meet Conditions (Culture Points, Population, Specific Buildings) │
│  • Changes PROPAGATE TO FUTURE → Alters Future Dungeon/State       │
│  • 100% Conditions → Rewards (HP/Def items, Blueprints, Medals)    │
└────────────────────────────┬────────────────────────────────────────┘
                             │ Time Travel (Atlamillia)
                             ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    FUTURE ERA (Monica's Time)                       │
│  • See results of Past Georama                                      │
│  • Future Dungeons altered (layout, enemies, loot)                 │
│  • Chests with HP/Def items appear when Past 100%                  │
│  • Story progression                                                │
└────────────────────────────┬────────────────────────────────────────┘
                             │
                             ▼
                    (LOOP REPEATS PER CHAPTER)
```

---

## Chapter Structure

| Chapter | Past Location | Future Location | Key Systems Unlocked |
|---------|---------------|-----------------|---------------------|
| 1 | Palm Brinks (Sewers) | Palm Brinks Future | Ridepod (Steve), Camera, Invention |
| 2 | Sindain | Sindain Future | Monster Transformation (Flora), Georama 2.0 |
| 3 | Balance Valley | Balance Valley Future | Spheda, Lin (Support), Spheda Medals |
| 4 | Veniccio | Veniccio Future | Fishing, Finny Frenzy, Aquarium |
| 5 | Heim Rada | Heim Rada Future | Fire Squall hazard, advanced Georama |
| 6 | Ixion (Train) | Moon Flower Palace | Time travel core, final prep |
| 7 | Moon Flower Palace | — | Final dungeon, true ending |
| 8 | Zelmite Mines (Post-game) | — | 100-floor challenge, ultimate weapons |

---

## Loop Mechanics Deep Dive

### Dungeon Phase
| Mechanic | DC1 | DC2 |
|----------|-----|-----|
| **Floors** | 10–20 | 10–25 per dungeon |
| **Key Enemy** | Yes | Yes (but Donny unlocks all doors) |
| **Medals** | No | **4 per floor** (Time, Wipeout, Spheda/Fish, Special) |
| **Geostones** | Atla (direct pieces) | **Geostones → Blueprints → Materials → Build** |
| **Photography** | No | **Ideas for Inventions** |
| **Ridepod** | No | **Steve** — separate weapon platform |
| **Monster Form** | No | **Monica** — 12 transformations |
| **Support Chars** | No | **Recruitable NPCs** — passive bonuses |

### Georama Phase (Past)
```
Geostone (Dungeon) 
    │
    ▼
Carpenterion (Steve's Database) → Unlocks BLUEPRINTS
    │
    ▼
Gather MATERIALS (Buy / Dungeon / Invent)
    │
    ▼
PLACE Blueprint on Map → Costs POLYN (currency) → Grants CULTURE POINTS
    │
    ▼
Meet CONDITIONS (10 per area):
  • Population ≥ X
  • Culture Points ≥ Y
  • Specific Buildings (Factory, Tree, River)
  • Specific NPCs living in specific houses
    │
    ▼
FUTURE ALTERED:
  • New dungeon paths open
  • Enemy types change
  • Chests appear (HP/Def items)
  • Shops stock new items
```

### Future Phase
- **Visit Future** → See Georama results
- **Collect Future Chests** → Permanent HP/Def upgrades (finite, like DC1 Fruits/Gourds)
- **Future Dungeons** — Altered by Past choices; new Geostones for next Past area
- **Story advances** → Next Chapter unlocks

---

## Dual Protagonist System

| Aspect | **Max** (Present) | **Monica** (Future) |
|--------|-------------------|---------------------|
| **Melee** | Wrench / Hammer | Sword |
| **Ranged** | Gun / Blaster | Armband (Magic) |
| **Special** | **Ridepod (Steve)** | **Monster Transformation** |
| **Traversal** | Steve: Jet/Propeller legs, hover | Monster: Fly, Swim, Dig, etc. |
| **Invention** | Camera → Ideas → Inventions | — |
| **Georama** | Builds Past | Benefits from Past builds |
| **Story Role** | Inventor, fixes Steve | Princess, restores timeline |

### Switching
- **Real-time** — L1/R1 cycle (Max ↔ Monica ↔ Steve)
- **Shared inventory** — Items, weapons, medals shared
- **Separate weapon XP** — Each weapon tracks own ABS/SP
- **Separate HP/Thirst** — But shared healing items

---

## Medal System (Per Floor Objectives)

| Medal Type | Requirement | Reward |
|------------|-------------|--------|
| **Time Trial** | Clear floor < X seconds | Mayor Need currency |
| **Wipeout** | Defeat ALL enemies (variant per chapter) | Mayor Need currency |
| **Spheda** | Repair distortion on floor | Mayor Need currency |
| **Fishing** | Catch fish ≥ target length | Mayor Need currency |
| **No Heal** | Clear without healing items | Mayor Need currency |
| **Weapon Specific** | Clear using only Max's Wrench / Gun / Steve / Monica's Sword / Armband | Mayor Need currency |

### Mayor Need Exchange
- **396 Total Medals** in game
- **Trade** for: Rare materials, ultimate weapon blueprints, Ridepod parts, costumes
- **Grind target** — Completionists farm specific floors for specific medals

---

## Support Characters (Recruitable NPCs)

| NPC | Recruit Condition | Passive Bonus |
|-----|-------------------|---------------|
| **Cedric** | Story (Ch. 1) | Weapon repair (free) |
| **Pau** | Ch. 2 Georama | Shows full dungeon map |
| **Donny** | Ch. 2 Photo Lv. 3 | **Unlocks ALL doors/chests** |
| **Gerald** | Ch. 3 Georama | +1 SP for Max's Guns |
| **Milane** | Ch. 3 Georama | +1 SP for Monica's Swords |
| **Lin** | Ch. 3 Story | +1 SP for Monica's Armbands (temp) |
| **Adel** | Ch. 4 Georama | Slows WHP decay for unequipped weapons |
| **Olivie** | Win Finny Frenzy | Sells all Lures |
| **Claire** | Ch. 5 Georama | Sells Gift Capsules (Monster badges) |
| **Woody** | Jurak Mall | Tailor (costumes, Gift Capsules) |

> **Party Limit**: 3 active (Max + Monica + 1 Support). Swap anytime.

---

## Systems Interlock Map

```
DUNGEON
  ├─ Enemies → ABS → Weapon Levels → SP → Synthesis
  ├─ Enemies → Synth Drops → Spectrumize → Synth Spheres
  ├─ Geostones → Carpenterion → Blueprints → GEORAMA
  ├─ Photography → Ideas (3 photos) → Inventions → Items/Parts
  ├─ Fishing → Fish → Aquarium → Breed → Finny Frenzy → Olivie
  ├─ Spheda → Medals → Mayor Need → Rare Items
  ├─ Medals (all) → Mayor Need → Ultimate Blueprints
  └─ Key Enemy → Floor Key → Progress

GEORAMA (Past)
  ├─ Materials (buy/find/invent) + Polyn → Build
  ├─ Culture Points → Unlock Conditions
  ├─ NPC Placement → Requests → Bonuses
  └─ 100% Conditions → Future Changes → Future Chests (HP/Def)

FUTURE
  ├─ Future Chests → Permanent Stats (Finite)
  ├─ Future Dungeons → New Geostones → Next Past Area
  └─ Story → Next Chapter

INVENTION
  ├─ Camera → Photos (30 max) → Idea Board (3 = Idea)
  ├─ Idea + Materials → Invention (Ridepod parts, Weapons, Items)
  └─ Scoop Photos (rare) → Unique Inventions

MONSTER TRANSFORMATION
  ├─ Gift Capsule (3× item) → Throw at Monster → Badge Drop
  ├─ Badge → Transform → Gain Monster Abilities
  ├─ Badge ABS → Badge Levels → Evolution (Himarra → Mandora/Scarecrow)
  └─ Moon/Sun Badges (Photo levels) → Duration / Stat Boosts
```

---

## Progression Resources (Finite)

| Resource | Total | Use | DC1 Equivalent |
|----------|-------|-----|----------------|
| **Future HP Chests** | ~30 | +10 Max HP (char-specific) | Fruit of Eden |
| **Future Def Chests** | ~25 | +5–7 Defense (char-specific) | Defense Items |
| **Gourds (Thirst)** | ~15 | +1 Max Thirst (all) | Gourds |
| **Pockets (Inv)** | ~10 | +10 Inventory slots | Pockets |
| **Synth Spheres (Max)** | Infinite (farmable) | Weapon stat transfer | SynthSphere |

> **Key Difference**: DC2 Future Chests are **guaranteed** by Georama 100% — no RNG hunting.

---

## Design Philosophy: "Everything Connects"

> **Akihiro Hino (Level-5 CEO):**
> "Dark Cloud 2 was the game we wanted to make the first time. The overseas version of Dark Cloud 1 was like 1.5 — we fixed things there. But DC2 rebuilt everything: engine, systems, philosophy. The core idea: **every system feeds every other system**."

### Interlock Examples
1. **Dungeon → Georama → Future Dungeon** — Causal loop
2. **Weapon → Spectrumize → SynthSphere → Other Weapon** — Cross-build economy
3. **Photo → Invention → Ridepod Part → Dungeon Speed → Medals → Blueprint** — 5-system chain
4. **Fishing → Breed → Finny Frenzy → Olivie → Lures → Better Fish** — Self-contained loop
5. **Monster Badge → Transform → Talk to Monsters → Quests → Georama NPCs** — Social loop

