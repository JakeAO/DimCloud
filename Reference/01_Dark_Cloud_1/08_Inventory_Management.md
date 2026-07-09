# Dark Cloud 1 — Inventory & Resource Management

## Overview
Limited inventory space + consumable dependencies (water, repair, healing) create constant tactical pressure. Management is a core skill.

---

## Inventory System

### Slot Limits
| Upgrade | Slots | Source |
|---------|-------|--------|
| **Base** | 20 | Start |
| **Pocket** | +10 each | Dungeon chests (8 total → 100 max) |
| **Max** | 100 | 8 Pockets found |

### Stacking Rules
| Item Type | Max Stack | Notes |
|-----------|-----------|-------|
| **Weapons** | 1 per slot | Equipped doesn't count |
| **Attachments** | 99 | Crystals, elements, utilities |
| **Water** | 20 | Regular / Tasty / Premium separate |
| **Repair Powder** | 20 | |
| **Healing** | 3–20 | Varies by item |
| **Status Cures** | 10–20 | |
| **Gourds / Fruits** | 3–5 | Stat items don't stack high |
| **Atla Pieces** | 1 each | Assembled = 1 slot |
| **Key Items** | 1 each | Story items |

---

## Resource Categories

### 1. Thirst Management (Critical)

#### Thirst Mechanics
- **Drain**: 1 drop per ~10 seconds in dungeon
- **Zero Thirst**: HP -1/sec until drink or death
- **Max Thirst**: 10 drops (base 5; +1 per Gourd, all chars share)

#### Water Items
| Item | Thirst Restored | Cost | Stack | Sources |
|------|-----------------|------|-------|---------|
| **Regular Water** | 3 | 10 G | 20 | Shops, chests |
| **Tasty Water** | 5 | 30 G | 20 | Shops, chests |
| **Premium Water** | Full (10) | 100 G | 10 | Late shops, rare chests |
| **Healing Spring** | Full HP + Thirst | Free | — | 1–2 per dungeon |

#### Strategy
- **Early game**: Carry 15 Regular + 5 Tasty
- **Mid game**: 10 Tasty + 5 Premium
- **Late game**: 10 Premium + Springs memorized
- **Emergency**: Mellow Banana (full HP, -2 Thirst) — last resort

### 2. Weapon Maintenance

#### Repair Items
| Item | WHP Restored | Cost | Stack | Notes |
|------|--------------|------|-------|-------|
| **Repair Powder** | ~30 | 50 G | 20 | Universal |
| **Gun Repair Powder** | ~30 | 80 G | 20 | Osmond only |
| **Ring Repair Powder** | ~30 | 80 G | 20 | Ruby only |

#### WHP Thresholds
| WHP % | Action |
|-------|--------|
| >50% | Safe |
| 20–50% | Monitor; repair at next safe moment |
| <20% | **Beep warning**; repair immediately |
| 0 | **Broken** — Weapon destroyed (JP) / Kept at 0 (Overseas) |

#### Repair Strategy
- **Carry**: 10–15 Repair Powder per run
- **Hotkey**: Assign to D-pad for mid-combat repair
- **Shop repair**: Cheaper for high-WHP weapons (cost ∝ max WHP)

### 3. Healing & Status

#### Healing Items
| Item | HP Restored | Thirst Effect | Cost | Stack |
|------|-------------|---------------|------|-------|
| **Bread** | 30 | 0 | 20 G | 20 |
| **Cheese** | 60 | 0 | 50 G | 20 |
| **Mellow Banana** | **Full** | **-2** | 150 G | 5 |
| **Fruit of Eden** | Full + Max HP+10 | 0 | N/A | 3 |
| **Stamina Drink** | 0 | 0 | 300 G | 10 | Temp Atk/Def + |

#### Status Cures
| Item | Cures | Cost | Stack |
|------|-------|------|-------|
| **Antidote** | Poison | 30 G | 20 |
| **Holy Water** | Curse, Undead debuff | 50 G | 20 |
| **Softener** | Petrify | 200 G | 10 |
| **Smelling Salts** | Confusion, Sleep | 40 G | 20 |
| **Mighty Healing** | **All** + Full HP | 1150 G | 5 |

---

## Loadout Templates

### Early Game (Dungeon 1–2)
| Slot | Item | Qty |
|------|------|-----|
| 1–3 | Weapons (Main + 2 Backup) | 3 |
| 4–6 | Repair Powder | 15 |
| 7–9 | Regular Water | 15 |
| 10 | Tasty Water | 5 |
| 11 | Bread | 10 |
| 12 | Cheese | 5 |
| 13 | Antidote | 5 |
| 14 | Holy Water | 3 |
| 15–18 | Attachments (Abs Up, Element) | 4 |
| 19–20 | Empty (Atla pickups) | 2 |

### Mid Game (Dungeon 3–4)
| Slot | Item | Qty |
|------|------|-----|
| 1–4 | Weapons (Main + 3 Backup) | 4 |
| 5–8 | Repair Powder | 15 |
| 9 | Gun/Ring Repair | 5 |
| 10–12 | Tasty Water | 15 |
| 13–14 | Premium Water | 5 |
| 15 | Mellow Banana | 3 |
| 16 | Cheese | 10 |
| 17 | Stamina Drink | 3 |
| 18 | Holy Water | 5 |
| 19 | Antidote | 5 |
| 20–24 | Attachments | 5 |
| 25–28 | Empty | 4 |

### Late Game (Dungeon 5–6 + Demon Shaft)
| Slot | Item | Qty |
|------|------|-----|
| 1–5 | Weapons (Main + 4 Backup) | 5 |
| 6–10 | Repair Powder | 20 |
| 11 | Gun/Ring Repair | 10 |
| 12–14 | Premium Water | 15 |
| 15 | Mellow Banana | 5 |
| 16 | Mighty Healing | 3 |
| 17 | Stamina Drink | 5 |
| 18 | Holy Water | 10 |
| 19–25 | Attachments (Abs Up, Crystals) | 7 |
| 26–30 | Empty | 5 |

---

## Inventory Management Tactics

### The "Atla Buffer" Rule
- **Always keep 3–5 empty slots** for Atla spheres
- Atla cannot be stacked; each piece = 1 slot
- Full inventory = can't collect Atla = wasted dungeon run

### Attachment Rotation
| Phase | Strategy |
|-------|----------|
| **Grinding** | Abs Up + Element matching dungeon |
| **Boss Prep** | Anti-Type crystal + Abs Up |
| **Between Floors** | Swap to next floor's element |
| **Weapon Upgrade** | Attach all → Upgrade → Slots freed |

### Sell vs. Keep
| Sell Immediately | Keep Always |
|------------------|-------------|
| Low-level weapons (after SynthSphere) | Abs Up attachments |
| Duplicate weak attachments | Anti-Type crystals for current dungeon |
| Excess water (if >15 slots) | Repair Powder (min 10) |
| Bread (once Cheese affordable) | Mellow Banana (3+) |

### Village Shop → Upgrade weapon between runs
3. **Georama** → Place pieces → Talk to villagers → Get requests
4. **Shop** → Sell loot → Buy water/repair/attachments
5. **Weapon Menu** → Attach → Upgrade → Check Build Up
6. **Inventory** → Consolidate → Ensure 5+ empty slots
7. **Save** → Next Dungeon

---

## Economy

### Income Sources
| Source | Avg/Run | Notes |
|--------|---------|-------|
| Enemy drops | 500–2000 G | Scales with floor |
| Chest gold | 100–500 G | |
| Sell attachments | 50–500 G | Crystals sell well |
| Sell weapons | 100–5000 G | +Level weapons = more |
| Georama rewards | 0–10000 G | One-time per village |

### Major Expenses
| Item | Cost | Frequency |
|------|------|-----------|
| Repair Powder | 50 G | Every run (10–20) |
| Water | 10–100 G | Every run (15–20) |
| Attachments | 100–5000 G | As needed |
| Weapon synthesis | 0 G | Free (uses items) |
| Pocket (inventory +10) | N/A | Found only |

### Money Management
- **Never broke** — Gold accumulates fast; no gold sinks except shops
- **Late game** — 100k+ G common; buy Premium Water freely
- **Demon Shaft** — Best gold farm (100 floors × drops)

---

## Quality of Life (Overseas / DC2 Improvements)

| Feature | DC1 JP | DC1 Overseas | DC2 |
|---------|--------|--------------|-----|
| **Stack sizes** | Low (3–20) | Same | **99 for most** |
| **Auto-sort** | No | No | **Yes (Select)** |
| **Quick stack** | No | No | **△ on item** |
| **Storage chest** | No | No | **Village warehouse** |
| **Equip compare** | No | No | **Yes** |
| **Sell multiples** | One by one | One by one | **Stack sell** |

---

## Design Analysis

### Strengths
- **Tension** — Resource scarcity forces engagement with systems
- **Preparation ritual** — Loadout planning = strategic fun
- **Trade-offs** — Water vs. Repair vs. Attachments vs. Atla space

### Weaknesses
- **Busywork** — Menu diving every 2 floors
- **No storage** — Must carry everything or lose it
- **Stack limits arbitrary** — Why 20 water but 99 crystals?
- **No auto-repair** — Manual repair every ~30 hits

### DC2 Fixes
- **Stack 99** on consumables
- **Warehouse** in each town
- **Auto-sort** button
- **Repair all** at shop
- **Ridepod fuel** separate from weapon WHP

