# Dark Cloud 1 — Core Gameplay Loop

## The Primary Loop

```
┌─────────────────┐    Atla Spheres     ┌──────────────────┐
│  PROCEDURAL     │ ──────────────────▶ │    GEORAMA       │
│  DUNGEON CRAWL  │                     │  VILLAGE BUILD   │
│                 │ ◀────────────────── │                  │
└─────────────────┘   Next Dungeon      └──────────────────┘
        ▲                                        │
        │         Boss Defeated                  │
        │         Key Obtained                   │
        └────────────────────────────────────────┘
```

### Phase 1: Dungeon Crawl
- **Procedural floors** — Room layouts, enemy placement, Atla positions randomized per entry
- **Key mechanic** — One enemy per floor carries the **Floor Key**; must defeat to progress
- **Resource management** — Thirst (water), WHP (repair powder), HP (healing), inventory space
- **Character switching** — 6 chars, each with unique traversal ability (jump, break rocks, fly, etc.)
- **Back-door areas** — Optional harder floors with better loot

### Phase 2: Georama Reconstruction
- **Atla → Pieces** — Spheres become houses, villagers, trees, rivers, decorations
- **Placement grid** — Tile-based; rotation allowed; adjacency rules for requests
- **Villager Requests** — Each NPC has 1–2 placement wishes (e.g., "near water", "away from X")
- **Completion %** — Three tracks: Collection / Reconstruction / Requests
- **100% Rewards** — Unique items, skills, weapon evolutions (e.g., Goro's Battle Axe → Inferno)

### Phase 3: Progression Gate
- **Boss at dungeon end** — Defeat unlocks next dungeon/area
- **Story advancement** — Cutscenes, new party members, new Georama areas
- **Loop repeats** — 6 main dungeons + final dungeon

---

## Secondary Loops (Nested)

### Weapon Growth Loop (Continuous)
```
Kill Enemies → Earn ABS → Weapon Levels Up
                    │
                    ▼
         Attach Items → Upgrade (absorb) → Stats Permanent
                    │
                    ▼
         Meet Red Stat Reqs → Build Up (Evolve) → New Weapon Lv1
                    │
                    ▼
         Level 5+ → Status Break → SynthSphere → Transfer to New Weapon
```

### Character Stat Loop (Finite)
```
Find Fruit of Eden → +10 Max HP (char-specific)
Find Gourd → +1 Max Thirst (all chars, cap 10)
Find Defense Item → +5-7 Defense (char-specific, save-scum for +7)
```
- **Hard caps** — Not enough items to max all 6 characters
- **Strategic allocation** — Prioritize main party (Toan + 1–2 others)

### Inventory Management Loop (Per Dungeon Run)
```
Prep: Buy water, repair powder, healing, status cures
     │
     ▼
Dungeon: Monitor thirst, WHP, HP, inventory space
     │
     ▼
Exit: Sell loot, repair, reorganize, allocate ABS to weapons
```

---

## Loop Timing & Pacing

| Activity | Typical Duration | Frequency |
|----------|------------------|-----------|
| Single dungeon floor | 5–15 min | Continuous |
| Full dungeon (15–20 floors) | 1.5–3 hrs | 6× main game |
| Georama session | 10–30 min | After each few floors |
| Weapon management | 5–10 min | Every few floors / at save |
| Boss fight | 5–20 min | 1× per dungeon |

---

## Procedural Generation Details

### Floor Structure
- **Room templates** — ~20–30 room types per dungeon theme
- **Connection graph** — Tree/grid hybrid; key room always reachable
- **Enemy tables** — Themed per dungeon; scaled by floor depth
- **Atla distribution** — 1–3 per floor; guaranteed on key floors
- **Special floors** — Healing spring, back-door entrance, mini-boss (fixed positions in generation seed)

### Repetition Mitigation (DC1)
- Limited room variety → visual fatigue by floor 10+
- Same enemy types per dungeon theme
- Overseas version added more room variants + enemy variants

---

## Save/Progression Structure

| Save Point | Location | What Saves |
|------------|----------|------------|
| **Village** | Any time in Georama | Full state |
| **Dungeon Exit** | Using "Exit" item or floor transition | Full state |
| **Quick Save** | Memory card only at village | Full state |
| **Death** | Return to village, lose 50% gold | Progress kept, gold lost |

---

## Design Philosophy: "Georama RPG"

> **Akihiro Hino (Level-5 CEO):**
> "We wanted to make an RPG where the player's actions in the dungeon *visibly change the world*. The Georama system turns abstract loot into tangible world-building. You don't just get a sword — you rebuild someone's home, and they give you that sword as thanks."

### Core Pillars
1. **Dungeon feeds World** — Atla is the currency linking crawl → build
2. **World feeds Dungeon** — Villagers give requests → rewards → better dungeon performance
3. **Visible Progress** — Empty plain → thriving village in 3D; emotional payoff
4. **Player Agency in Reconstruction** — Multiple valid layouts; 100% is optimization puzzle

---

## Comparison to Contemporaries

| Game | Loop Type | World Impact |
|------|-----------|--------------|
| **Diablo II** | Dungeon → Loot → Character Power | None (hub static) |
| **Zelda: OoT** | Dungeon → Item → Progress | Scripted world changes |
| **ActRaiser** | Action → Sim → Action | Sim builds world, unlocks action |
| **Dark Cloud** | **Dungeon → Atla → Georama → Rewards → Dungeon** | **Player-designed persistent world** |

