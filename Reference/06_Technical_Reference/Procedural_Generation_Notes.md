# Dark Cloud Series — Procedural Generation Notes

## DC1: Dungeon Generation Architecture

### Core Concept
**"Room Template + Connection Graph + Enemy/Item Population"**

### Room Templates
| Parameter | Value |
|-----------|-------|
| **Templates per Theme** | 20–30 |
| **Room Types** | Start, End, Junction, Dead-end, Large, Small, Secret, Spring, Back-door |
| **Dimensions** | 8×8 to 32×32 tiles (variable) |
| **Exits** | 1–4 (Cardinal directions) |
| **Geometry** | Static mesh + collision; pre-baked lighting |

### Floor Generation Algorithm
```
1. Determine Floor Size (Rooms: 8–15, scales with floor #)
2. Generate Spanning Tree (Rooms as nodes, corridors as edges)
3. Add 1–2 Extra Edges (Create loops; reduce dead-ends)
4. Assign Room Templates (Weighted by type requirements)
5. Place Mandatory Elements:
   - Key Enemy (1 per floor)
   - Atla Spheres (1–3, guaranteed on key floors)
   - Healing Spring (0–1, rare)
   - Back-door Entrance (10% chance)
6. Populate Enemies (Themed table; density scales)
7. Place Chests/Items (Trapped/Locked/Mimic variants)
8. Validate: Key reachable; no isolated rooms; path exists
```

### Theme Parameters (Per Dungeon)
| Dungeon | Theme | Room Count | Enemy Families | Special |
|---------|-------|------------|----------------|---------|
| Divine Beast Cave | Cave | 15 | Beast, Scale | Tutorial |
| Wise Owl Forest | Forest | 15 | Plant, Beast, Insect | River Atla |
| Shipwreck | Water/Ruins | 12 | Aquatic, Undead | Verticality |
| Sun & Moon Temple | Desert/Ancient | 18 | Scale, Undead, Machine | Sun/Moon Switch |
| Moon Sea | Lunar/Cave | 15 | Machine, Scale | Low Gravity |
| Gallery of Time | Abstract | 10 | All (Story) | Handcrafted |
| Demon Shaft | Mixed | 100 | All | Endless |

### Enemy Placement
- **Per Room**: 1–3 groups (2–4 enemies each)
- **Scaling**: Base Level + Floor# × 0.5
- **Elite Variants**: 5% chance (Red aura; 2× HP, 1.5× DMG, 0.5× DMG taken)
- **Key Enemy**: Random selection from floor's spawn list (no visual indicator)

### Atla Distribution
| Dungeon | Total Atla | Avg/Floor | Guaranteed Floors |
|---------|------------|-----------|-------------------|
| Divine Beast Cave | 45 | 3.0 | 5, 10, 15 |
| Wise Owl Forest | 52 | 3.5 | 5, 10, 15 |
| Shipwreck | 38 | 3.2 | 4, 8, 12 |
| Sun & Moon Temple | 65 | 3.6 | 6, 12, 18 |
| Moon Sea | 50 | 3.3 | 5, 10, 15 |

---

## DC2: Dungeon Generation Improvements

### Changes from DC1
| Aspect | DC1 | DC2 |
|--------|-----|-----|
| **Room Variance** | 20–30 templates | **30–40 + prop variance** |
| **Floor Objectives** | Key only | **4 Medals (Time/Wipe/Spheda/Fish)** |
| **Geostones** | Atla (pieces) | **Geostones → Blueprints** |
| **Photography** | None | **Objects → Ideas → Inventions** |
| **Fishing/Spheda** | None | **Per-floor spots** |
| **Medal Tracking** | None | **Per-floor progress UI** |
| **Map Reveal** | Manual | **Donny (Auto-unlock doors/chests)** |

### Floor Generation (DC2)
```
1. Select Seed (Fixed per entry; saved for retry)
2. Generate Graph (Spanning tree + loops)
3. Assign Room Templates (Theme + floor depth)
4. Place Medal Objectives:
   - Time Trial (Target time)
   - Wipeout (All enemies / variant)
   - Spheda (Distortion present?)
   - Fishing (Spot exists?)
   - No Heal / Weapon Specific (Variant)
5. Place Geostones (1–2 per floor; themed)
6. Place Photo Opportunities (Scoops on specific floors)
7. Place Fishing Spots (If medal type)
8. Populate Enemies (Themed + density scaling)
8. Validate all objectives achievable
```

### Seed System (DC2)
- **Per-Floor Seed**: Fixed per dungeon entry
- **Re-entry**: Same layout (enables mastery)
- **Save State**: Emulator save-per-floor = medal farming
- **Community Seeds**: Speedrun/score attack sharing

---

## Reference: Room Template Categories

| Category | Purpose | Exit Count | Typical Props |
|----------|---------|------------|---------------|
| **entrance** | Floor start | 1 | Save point, hint board |
| **exit** | Floor end (key gate) | 1 | Boss door, key slot |
| **junction_4way** | Branching | 3–4 | Central pillar, loot |
| **junction_3way** | T-junction | 3 | Corner cover |
| **corridor_straight** | Linear connection | 2 | Traps, patrol paths |
| **corridor_corner** | Direction change | 2 | Blind corner |
| **room_combat** | Arena | 1–2 | Cover, hazards |
| **room_puzzle** | Mechanic intro | 1–2 | Switches, pressure plates |
| **room_treasure** | Reward | 1 | Chest, mimic chance |
| **room_secret** | Hidden | 1 | Breakable wall, lore |
| **room_spring** | Healing | 1 | Water, particles |
| **room_backdoor** | Bonus | 1–2 | Elite enemies, rare loot |
| **landmark_vertical** | Multi-floor | 2+ | Elevator, shaft, waterfall |
| **landmark_horizontal** | Large vista | 2+ | Bridge, canyon, city view |
| **boss_arena** | Final fight | 1 | Phase triggers, no exits |

---

## Generation Quality Metrics

| Metric | DC1 | DC2 |
|--------|-----|-----|
| **Layout Uniqueness** | 40% | 55% |
| **Dead-end %** | 25% | 15% |
| **Objective Clarity** | Low | Medium |
| **Replay Value (Seeds)** | None | Manual |
| **Handcrafted Feel** | Low | Medium |
| **Generation Time** | Instant | Instant |
| **Memory Overhead** | Low | Low |