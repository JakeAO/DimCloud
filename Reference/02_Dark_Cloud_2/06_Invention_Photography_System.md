# Dark Cloud 2 — Invention & Photography System

## Overview
**Photography → Ideas → Inventions** is a unique crafting pipeline. Photograph objects in world → Combine 3 photos into Idea Card → Gather materials → Build Invention. Powers Ridepod upgrades, weapons, items, and Georama unlocks.

---

## Pipeline

```
WORLD OBJECTS
    │
    ▼
CAMERA (Equip → Aim → ×) → PHOTOGRAPH (30 max in album)
    │
    ├─▶ REGULAR PHOTO → 2 Photo Points
    └─▶ SCOOP PHOTO (Rare/Hidden) → 5 Photo Points
    │
    ▼
IDEA BOARD (Menu → Make → New Invention)
    │
    ├─▶ Drag 3 Photos → COMBINE → IDEA CARD (if valid combo)
    │       │
    │       └─▶ Invalid = "Can't think of anything..."
    │
    ▼
INVENTION LIST (Menu → Make → Invention List)
    │
    ├─▶ Select Idea → Shows REQUIRED MATERIALS
    │
    ▼
GATHER MATERIALS (Buy / Dungeon / Invent / Georama)
    │
    ▼
ASSEMBLE (Menu → Make → Assemble)
    │
    ▼
INVENTION COMPLETE → Item / Part / Weapon / Blueprint Unlock
```

---

## Camera Mechanics

### Acquisition
- **Chapter 1**: Cedric gives Camera after Ridepod tutorial
- **Equip** — Item Menu → Camera → Equip to Item Slot
- **Use** — Hold L1 (aim) → × (shoot); Right stick = zoom

### Photo Limits
| Limit | Value | Expansion |
|-------|-------|-----------|
| **Album Capacity** | 30 photos | Move to Idea Book (unlimited) |
| **Idea Book** | Unlimited | Select photos → △ → "Move to Book" |
| **Photo Points** | 750 total | Level 1–8; Donny rewards per level |

### Photo Types
| Type | Points | Identification | Examples |
|------|--------|----------------|----------|
| **Regular** | 2 | Blue border | Chairs, trees, machines, enemies, NPCs |
| **Scoop** | 5 | Gold border + "SCOOP!" | Hidden rooms, rare enemies, specific angles, Georama-dependent |

### Photo Subjects (Categories)
| Category | Examples | Invention Relevance |
|----------|----------|---------------------|
| **Furniture** | Chair, Table, Bed, Lamp | House parts, Ridepod interior |
| **Machinery** | Gear, Pipe, Motor, Constructor | Ridepod parts, Weapons |
| **Nature** | Tree, Flower, River, Rock | Georama pieces, Fuel |
| **Enemies** | Specific monsters | Monster Badge items, Weakness items |
| **NPCs** | Shopkeepers, Villagers | Recruitment clues, Quest items |
| **Georama** | Placed buildings, Future versions | Advanced blueprints |
| **Future** | Future-era objects | Late-game inventions |

---

## Idea Combination Logic

### Valid Combinations
- **3 Photos = 1 Idea** (order doesn't matter)
- **Recipe hidden** — Must discover or find clue (Scoop, NPC hint, Book)
- **Multiple recipes per invention** — Different photo sets can yield same Idea
- **Chapter-gated** — Some photos only available in specific chapters/eras

### Discovery Methods
| Method | Description |
|--------|-------------|
| **Experimentation** | Try combos; game says "Can't think of anything" if invalid |
| **Scoop Photos** | Rare photos that *are* the clue (e.g., "Milk Can + Pipe + Belt = Energy Pack") |
| **NPC Hints** | Cedric, Donny, Claire give vague clues |
| **Idea Books** | Found in dungeons; list 1–3 recipes |
| **Georama Conditions** | Future buildings unlock new photo opportunities |

### Example: Energy Pack (First Invention)
```
PHOTO 1: Milk Can (Palm Brinks, street near bakery)
PHOTO 2: Pipe (Palm Brinks, Cedric's shop roof)
PHOTO 3: Belt (Palm Brinks, Sheriff Blinkhorn's belt)
    │
    ▼
IDEA: "Energy Pack" → MATERIALS: Scrap Metal ×20, Thick Hide ×1, Copper ×2
    │
    ▼
ASSEMBLE → Steve's Energy Backpack (Ridepod Fuel +100)
```

---

## Invention Categories

| Category | Count | Examples |
|----------|-------|----------|
| **Ridepod Parts** | ~35 | Legs (Propeller/Jet/Buggy), Arms (Drill/Claw), Weapons (Cannon/Laser), Armor, Fuel |
| **Weapons** | ~20 | Max's Wrenches, Monica's Swords/Armbands, Unique (Fridge, Toy Hammer) |
| **Items** | ~30 | Healing, Status Cures, Bombs, Ammo, Water, Rations |
| **Georama Blueprint Unlocks** | ~15 | Advanced buildings, Future-era pieces |
| **Fishing/Rod Upgrades** | ~10 | Lure Rod, Bait variants, Aquarium tanks |
| **Consumables/Other** | ~20 | Stamina Drink, Mighty Healing, Pocket, Gourd |

**Total Inventions**: **130 unique**

---

## Material Economy

### Material Sources
| Source | Materials |
|--------|-----------|
| **Shops** | Scrap Metal, Copper, Silver, Gold, Cloth, Leather, Wood, Stone |
| **Dungeon Chests** | Rare: Moon Stone, Sun Stone, Luna Stone, Stardust, Poison, Bomb |
| **Georama** | Future shops sell unique materials (after 100% Past) |
| **Invention** | Some materials ARE inventions (recursive) |
| **Fishing** | Fish → Breed → Materials (Scales, Fins) |
| **Monster Drops** | Badge items, Elemental Crystals, Rare Metals |

### Common Material Costs
| Invention Tier | Typical Cost |
|----------------|--------------|
| **Tier 1 (Early)** | Scrap ×10–20, Hide ×1–3, Copper ×1–2 |
| **Tier 2 (Mid)** | Scrap ×30, Silver ×5, Element ×10, Rare Metal ×1 |
| **Tier 3 (Late)** | Moon Stone ×5, Sun Stone ×5, Gold ×20, Luna Stone ×3 |
| **Ultimate** | Stardust ×10, Moon/Sun ×20, Ultimate Metal ×5, Rare Drop ×1 |

---

## Photography Levels & Rewards

| Level | Points Needed | Total Photos (Reg) | Donny Reward |
|-------|---------------|-------------------|--------------|
| 1 | 100 | 50 | Stamina Drink ×3 |
| 2 | 200 | 100 | Repair Powder ×5 |
| 3 | 300 | 150 | **Donny joins party** (Map reveal) |
| 4 | 400 | 200 | Mighty Healing ×3 |
| 5 | 500 | 250 | Pocket (+10 slots) |
| 6 | 600 | 300 | Gourd (+1 Thirst) |
| 7 | 700 | 350 | **Moon Badge** (Monster Transform Duration++) |
| 8 | 750 | 375 | **Sun Badge** (Monster Transform Atk/Def++) |

> **Note**: 750 max points; can miss ~50 points (25 Regular or 10 Scoops) and still hit Level 8.

---

## Scoop Photos (Critical for Completion)

### Characteristics
- **Gold border** + "SCOOP!" text
- **5 Points** (vs 2 Regular)
- **Often missable** — Chapter-specific, Georama-dependent, or one-time
- **Required for unique Inventions** — Some Ideas ONLY from Scoops

### Missable Scoops (Major)
| Scoop | Location | Condition | Missable? |
|-------|----------|-----------|-----------|
| **Blackstone One (Train)** | Ch. 6 Interior | Only Ch. 6–7 | **YES** (Gone Ch. 8) |
| **Fire House** | Blackstone One | Same as above | **YES** |
| **Coal** | Blackstone One | Same as above | **YES** |
| **Geyser** | Heim Rada | Don't seal all with Hardened Mud | **YES** (if sealed) |
| **Future Town Buildings** | Future Areas | Require Past 100% first | Chapter-gated |

### Scoop Strategy
1. **Save before Ch. 6 Train** — Exhaustively photograph everything
2. **Don't seal all Geysers** — Leave one open for photo
3. **Check Future Towns after Past 100%** — New buildings = new Scoops
4. **Talk to Donny often** — He tracks progress; hints at missing

---

## Ridepod Inventions (Steve Parts)

### Part Categories
| Category | Invention Examples | Function |
|----------|-------------------|----------|
| **Legs** | Roller Skates, Propeller, Jet Hover, Buggy | Movement speed, terrain access |
| **Body** | Frame Upgrade, Sun & Moon Armor, Cooling System | HP, Defense, Heat management |
| **Arms** | Drill Arm, Claw Arm, Gripper, Hammer | Melee attack type, interaction |
| **Weapons** | Barrel Cannon, Laser Cannon, Missile Pod, Gatling | Ranged DPS, element |
| **Fuel** | Energy Pack, Energy Pack (Barrel), Solar Panel | Max Fuel, Regen rate |
| **Utility** | Radar, Auto-Repair, Item Finder, Scanner | QoL, Exploration |

### Leg Upgrades (Key Progression)
| Legs | Speed | Terrain | Chapter |
|------|-------|---------|---------|
| Standard | 1.0× | Ground | 1 |
| **Roller Skates** | 1.5× | Ground | 2 (Invent) |
| **Propeller** | 2.0× | Ground + Air (short) | 3 (Invent) |
| **Jet Hover** | 2.5× | Ground + Air + Water | 5 (Invent) |
| **Buggy** | 3.0× | All (harder control) | 7 (Invent) |

> **Time Trial Medals**: Propeller/Jet Hover **essential** for gold times

---

## Weapon Inventions (Unique)

### Max's Unique Weapons
| Weapon | Idea Photos | Materials | Notes |
|--------|-------------|-----------|-------|
| **Fridge** | Refrigerator, Ice, Milk | Moon Stone, Ice Crystal | High Chill; comedy |
| **Toy Hammer** | Toy, Hammer, Spring | Scrap, Copper | High Smash; low ATK |
| **Machinist Wrench** | Constructor, Gear, Blueprint | Silver, Luna Stone | Best mid-game Wrench |

### Monica's Unique Weapons
| Weapon | Idea Photos | Materials | Notes |
|--------|-------------|-----------|-------|
| **Chopper Sword** | Helicopter, Blade, Gear | Sun Stone, Lightning | High Cyclone |
| **Flower Armband** | Flower, Ribbon, Magic Stone | Chill, Holy Crystal | High Exorcism |
| **Star Sword** | Star, Sword, Jewel | Stardust, Holy | Ultimate-ish |

---

## Georama Blueprint Inventions

### Unlock Mechanism
```
INVENTION → "Blueprint: [Building Name]" → Carpenterion → Available in Georama
```

### Key Blueprint Inventions
| Blueprint | Idea Photos | Unlocks |
|-----------|-------------|---------|
| **Windmill** | Windmill, Gear, Wheat | Power generation (Culture+) |
| **Waterwheel** | Waterwheel, River, Wheel | Water control (Culture+) |
| **Factory** | Factory, Smoke, Pipe | Advanced materials shop |
| **Railway** | Train, Track, Station | Fast travel (Future) |
| **Lighthouse** | Lighthouse, Light, Sea | Future dungeon access |
| **Observatory** | Telescope, Star, Dome | Scoop photos (Moon/Sun) |

---

## Invention Completion Tracking

### Menu: Make → Invention List
- **Alphabetical** list of all 130
- **Shows**: Idea Photos (if discovered), Materials, Status
- **Status Icons**:
  - ❓ — Idea not discovered
  - 💡 — Idea known, materials incomplete
  - 🔨 — Ready to assemble
  - ✅ — Completed

### Completion Rewards
| Milestone | Reward |
|-----------|--------|
| 50 Inventions | Pocket (+10) |
| 80 Inventions | Gourd (+1 Thirst) |
| 100 Inventions | Mighty Healing ×5 |
| **130 (All)** | **Platinum Trophy** / **Ultimate Blueprint** |

---

## Optimization Strategy

### Early Game (Ch. 1–2)
1. **Photograph everything** in Palm Brinks (30+ objects)
2. **Prioritize Energy Pack** → Steve Fuel → Steve usable
3. **Roller Skates** → Faster dungeon movement
4. **Save Scoops** — Don't waste album space on Regular if Scoop possible

### Mid Game (Ch. 3–5)
1. **Recruit Donny (Photo Lv. 3)** — Auto-map = faster runs
2. **Propeller Legs** — Time Trial medals
3. **Elemental Weapon Inventions** — Match dungeon weaknesses
4. **Aquarium Invention** — Start Fish Breeding → Finny Frenzy → Olivie

### Late Game (Ch. 6–8)
1. **Jet Hover / Buggy** — Ultimate movement
2. **Sun & Moon Armor** — Steve tankiness
3. **Ultimate Weapon Inventions** — Fridge, Star Sword, etc.
4. **Cleanup** — Photo Album + Idea Book sync; hunt missing Scoops

---

## Design Analysis

### Strengths
- **Discovery Joy** — "I wonder if X+Y+Z works?" → Experimentation
- **World Photography** — Encourages observing environment detail
- **Non-Linear Crafting** — Multiple photo paths to same Invention
- **Ridepod as Crafting Tree** — Visual progression (legs → body → arms → weapons)
- **Scoop Economy** — Rare photos = high value; rewards thoroughness

### Weaknesses
- **Album Management** — 30 limit → constant Book shuffling
- **Trial & Error Fatigue** — "Can't think of anything" × 50 = frustration
- **Missable Scoops** — No warning; perma-loss without guide
- **Material Grind** — Late inventions need Moon/Sun Stones (rare drops)
- **Underused** — Only ~20 Inventions mandatory; 110 optional

### DC1 Comparison
| DC1 | DC2 Invention |
|-----|---------------|
| Shop buy / Dungeon find | **Photo → Idea → Build** |
| Fixed recipes | **Hidden combinatorial recipes** |
| Weapon attachments only | **Ridepod, Weapons, Items, Blueprints** |
| No camera | **Camera as progression tool** |

