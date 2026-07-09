# Dark Cloud 1 — Character Progression (Stats & Items)

## Overview

**Characters don't level up.** Stat growth comes exclusively from consumable items found in dungeons, Georama rewards, and shops. Finite supply forces allocation strategy.

---

## Stat Categories

| Stat | Max (Typical) | Source | Notes |
|------|---------------|--------|-------|
| **Max HP** | 140–180 | Fruit of Eden (+10) | Char-specific caps |
| **Defense** | 58–68 | Defense Items (+5–7) | Char-specific items; save-scum for +7 |
| **Max Thirst** | 10 drops | Gourd (+1) | Shared cap; 15 Gourds total |
| **Inventory** | 100+ slots | Pocket (+10) | 20 base; 8 Pockets = 100 |

---

## Stat Increase Items

### Fruit of Eden — Max HP +10
| Source | Count |
|--------|-------|
| Dungeon chests | ~30 |
| Georama 100% rewards | ~10 |
| Shops (late game) | 5–10 |
| **Total** | **~45–50** |

**Character Caps (Tested Values):**
| Character | Max HP | Fruits Needed |
|-----------|--------|---------------|
| Toan | 170–180 | 9–10 |
| Goro | 170–180 | 9–10 |
| Ungaga | 180 | 10 |
| Osmond | 160 | 8 |
| Xiao | 140 | 6 |
| Ruby | 140 | 6 |

> **Shortfall**: ~60 fruits needed to max all 6; only ~50 exist. Must choose 4–5 chars to max.

### Gourd — Max Thirst +1 Drop
| Source | Count |
|--------|-------|
| Dungeon chests | ~10 |
| Georama rewards | ~3 |
| Shops | 2 |
| **Total** | **~15** |

- **Cap**: 10 drops (all chars share)
- **Cost**: 1 Gourd = +1 max thirst for **all** characters
- **Strategy**: Max thirst early (survival); extra Gourds low priority

### Defense Items — Char-Specific (+5 to +7)
| Character | Item Name | Sources |
|-----------|-----------|
| Toan | Fluffy Doughnut |
| Xiao | Millefeuille |
| Goro | Grass Cake |
| Ruby | Witch Parfait |
| Ungaga | Stamina Drink |
| Osmond | Carrot Cookie |

**Mechanic**: Random +5, +6, or +7. **Save before use**; reload for +7.
- **Total items**: ~12–15 per character (enough to max with save-scum)
- **Max Defense by Char**: Toan 66, Xiao 64, Goro 68, Ruby 58, Ungaga 59, Osmond 60

### Pocket — Inventory +10 Slots
- **Sources**: Dungeon chests (rare), Georama 100%, late shops
- **Total**: ~8–10 (80–100 extra slots)
- **Priority**: Early game critical; late game abundant

---

## Allocation Strategy

### Recommended Priority (Max 5 Characters)
```
1. Toan (mandatory - Atla collector, main story)
2. Goro (tank, best hammer, Battle Axe → Inferno)
3. Ungaga (high HP, staff reach, desert traversal)
4. Osmond (ranged, guns, late-game DPS)
5. Xiao OR Ruby (choose one ranged)
   → Xiao: jump traversal, slingshot cheap ammo
   → Ruby: magic variety, but fragile, ring WHP terrible
```

### Gimp Strategy (Common)
- **Skip Xiao** — Ruby covers ranged; Xiao's jump rarely required post-Matataki
- **Skip Ruby** — Xiao's slingshot sufficient; Ruby's rings break too fast
- **Result**: 4 maxed chars + 1 partial = comfortable

---

## Thirst Mechanics Deep Dive

### Thirst Consumption
| Action | Thirst Cost |
|--------|-------------|
| Walking (per 10 sec) | 1 drop |
| Running | 1.5× |
| Attacking | 0 (but WHP drops) |
| In menu / paused | 0 |

### Water Items
| Item | Thirst Restored | Cost | Stack |
|------|-----------------|------|-------|
| Regular Water | 3 | 10 G | 20 |
| Tasty Water | 5 | 30 G | 20 |
| Premium Water | Full (10) | 100 G | 10 |
| Mellow Banana | -2 (heals HP) | 80 G | 20 |

### Thirst Management Tips
- **Always carry 10+ water** — Spring floors rare
- **Drink at 3–4 drops** — Don't wait for warning beep
- **Premium Water for boss floors** — Full restore + save inventory slots
- **Mellow Banana emergency** — HP heal when no water; accept thirst cost

---

## HP/Defense Max Reference (JSON)

```json
{
  "maxStats": {
    "Toan": {"hp": 180, "def": 66, "thirst": 10},
    "Xiao": {"hp": 140, "def": 64, "thirst": 10},
    "Goro": {"hp": 180, "def": 68, "thirst": 10},
    "Ruby": {"hp": 140, "def": 58, "thirst": 10},
    "Ungaga": {"hp": 180, "def": 59, "thirst": 10},
    "Osmond": {"hp": 160, "def": 60, "thirst": 10}
  },
  "itemTotals": {
    "fruitOfEden": 50,
    "gourds": 15,
    "pockets": 10,
    "defenseItemsPerChar": 12
  },
  "allocationGap": {
    "fruitsNeededForAll": 60,
    "fruitsAvailable": 50,
    "shortfall": 10
  }
}
```

---

## Design Analysis

### Intentional Scarcity
- **Forces specialization** — Can't max everyone; defines "main party"
- **Replay value** — Different allocations = different playthroughs
- **Georama incentive** — 100% requests give stat items (major source)

### Save-Scumming Defense Items
- **Designed around it** — Random 5–7 range assumes reloads
- **Without save-scum**: Avg +6 → ~10 items to max vs 12–15 needed
- **Modern fix**: Guaranteed +7 on use; remove RNG frustration

### Thirst as "Soft Time Limit"
- **Not true survival** — Water abundant; just inventory tax
- **Could be deeper** — Thirst affects stamina, dodge, crit chance
- **DC2 removed it** — Replaced with medal time trials

