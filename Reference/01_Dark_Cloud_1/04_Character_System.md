# Dark Cloud 1 — Character System

## Overview
6 playable characters, each with unique weapon type, traversal ability, and stat growth via consumables (no EXP/levels). Only Toan can collect Atla.

---

## Character Roster

| Character | Weapon | Range | Traversal | Joins | Role |
|-----------|--------|-------|-----------|-------|------|
| **Toan** | Swords/Daggers | Melee | — | Start | Main; Atla collector |
| **Xiao** | Slingshots | Ranged | **Jump** (gaps) | Ch. 1 (Norune) | Mobility, ranged DPS |
| **Goro** | Hammers/Axes | Melee | **Break Rocks** | Ch. 2 (Matataki) | Heavy damage, rock puzzles |
| **Ruby** | Magic Rings | Ranged | **Fly** (short hover) | Ch. 3 (Queens) | Elemental magic, flight |
| **Ungaga** | Staves/Spears | Melee | **Sandwalk** (quicksand) | Ch. 4 (Muska Lacka) | Reach, desert nav |
| **Osmond** | Guns/Blasters | Ranged | **Unlock Doors** | Ch. 5 (Yellow Drops) | High damage, keys |

---

## Stat System

### No Experience / Levels
- **Characters never gain XP**
- **Stats increased ONLY via consumables** (finite supply)

### Core Stats
| Stat | Function | Max Source |
|------|----------|------------|
| **HP** | Health pool | Fruit of Eden (+10), Mellow Banana (heals, -2 thirst) |
| **Defense** | Damage reduction | Defense Up items (Stamina Drink, etc.) |
| **Thirst Max** | Water capacity | Gourds (+1 each, cap 10) |
| **Thirst Rate** | Drain speed | Fixed per char (ranged drain faster) |

### Stat Items (Finite)
| Item | Effect | Locations |
|------|--------|-----------|
| **Fruit of Eden** | +10 Max HP (1 char) | Dungeon chests, Georama rewards, shops (late) |
| **Gourd** | +1 Max Thirst (all chars) | Dungeon chests, shops |
| **Stamina Drink** | +5–7 Defense (temp) / +Def perm (rare) | Shops, chests |
| **Mellow Banana** | Full heal, -2 Thirst | Shops, drops |

### Allocation Strategy
- **~60 Fruits of Eden** total in game → Not enough to max all 6 chars
- **~15 Gourds** → Can max thirst for all
- **Priority**: Toan (always in party) + 1–2 mains
- **Save-scum** Defense items for +7 rolls (reload if +5)

---

## Traversal Abilities (Dungeon Navigation)

| Character | Ability | Dungeon Usage |
|-----------|---------|---------------|
| **Xiao** | Jump | Cross gaps, reach high chests, skip rooms |
| **Goro** | Hammer Swing | Break cracked walls/rocks → shortcuts, secret rooms |
| **Ruby** | Float | Cross gaps, avoid floor traps, reach floating items |
| **Ungaga** | Sandwalk | Walk on quicksand (Muska Lacka, Moon Sea) |
| **Osmond** | Key Shot | Shoot locked doors/switches (no key needed) |
| **Toan** | Atla Absorb | **Only** character who can collect Atla spheres |

> **Design Note**: Party of 3 max (Toan + 2). Must swap for traversal puzzles.

---

## Combat Styles

### Melee (Toan, Goro, Ungaga)
| Char | Style | Charge Attack | Notes |
|------|-------|---------------|-------|
| **Toan** | Fast 3-hit combo | Spin Slash (AoE, high WHP cost) | Balanced; best weapon variety |
| **Goro** | Slow 2-hit + overhead | Ground Smash (AoE, breaks guard) | Highest single-hit damage |
| **Ungaga** | Wide sweep | Spinning Staff (360°, multi-hit) | Best crowd control |

### Ranged (Xiao, Ruby, Osmond)
| Char | Style | Charge Attack | Notes |
|------|-------|---------------|-------|
| **Xiao** | Rapid pellets | Power Shot (piercing, high dmg) | Fastest attack speed |
| **Ruby** | Elemental rings | Charged Spell (element AoE) | Element swap via ring; low WHP |
| **Osmond** | Single shots | Burst Fire (3-round) | Highest range; ammo management |

---

## Duel System (QTE)

### Trigger
- Random chance on enemy encounter (~5–10%)
- Certain story bosses (mandatory)

### Mechanics
- Button sequence appears (△ ○ × □ + directions)
- **Time limit**: ~3–5 seconds
- **Success**: Massive damage / instant kill / item drop
- **Failure**: Damage to player; enemy unaffected

### Overseas Version
- More Duel encounters added
- Slightly longer input windows

---

## Party Management

### Active Party
- **3 characters max** (Toan always slot 1)
- Switch anytime in dungeon (L1/R1 cycle)
- Only active char gains ABS for equipped weapon
- Inactive chars: no ABS, no thirst drain, no HP loss

### Support Characters (DC2 only — not in DC1)
- DC1 has no support character system

---

## Character Quests / Unlocks

| Character | Unlock Condition | Personal Quest |
|-----------|------------------|----------------|
| **Xiao** | Toan uses Changing Potion on cat | Find true form; catgirl lore |
| **Goro** | Rebuild Matataki 100% requests | Hunter pride; Battle Axe reward |
| **Ruby** | Rebuild Queens; defeat Shipwreck boss | Genie freedom; Witch Parfait |
| **Ungaga** | Rebuild Muska Lacka; Sun/Moon Temple | Desert warrior; Sun Giant |
| **Osmond** | Reach Yellow Drops; collect robot parts | Moon People; Sun Giant pilot |

---

## Stat Growth Reference (JSON)

```json
{
  "characters": [
    {"name": "Toan", "baseHP": 80, "baseDef": 10, "thirstRate": 1.0, "weaponType": "Sword"},
    {"name": "Xiao", "baseHP": 60, "baseDef": 8, "thirstRate": 1.3, "weaponType": "Slingshot"},
    {"name": "Goro", "baseHP": 120, "baseDef": 15, "thirstRate": 0.8, "weaponType": "Hammer"},
    {"name": "Ruby", "baseHP": 50, "baseDef": 5, "thirstRate": 1.5, "weaponType": "Ring"},
    {"name": "Ungaga", "baseHP": 100, "baseDef": 12, "thirstRate": 1.0, "weaponType": "Staff"},
    {"name": "Osmond", "baseHP": 70, "baseDef": 10, "thirstRate": 1.2, "weaponType": "Gun"}
  ],
  "maxFruitsOfEden": 60,
  "maxGourds": 15,
  "thirstCap": 10
}
```

---

## Design Analysis

### Strengths
- **Distinct roles** — Each char solves specific traversal/combat problems
- **No level grind** — Stat items = exploration rewards
- **Weapon-centric** — Gear progression feels more tangible than levels
- **Party puzzle** — Swapping for obstacles encourages using all chars

### Weaknesses
- **Toan mandatory** — Atla collection forces him in party always
- **Ranged chars fragile** — Low HP/Def + fast thirst = glass cannons
- **Ruby underpowered** — Ring WHP too low; magic damage doesn't scale well
- **Osmond late** — Joins Ch. 5; gun ammo expensive; limited use time

### DC2 Evolution
- **2 protagonists** (Max/Monica) with dual weapon types each
- **Ridepod** — Customizable mech replaces 4th–6th character slots
- **Monster Transformation** — Monica gains 12 forms (traversal + combat)
- **Support NPCs** — Passive bonuses (drop rates, synth points, etc.)

