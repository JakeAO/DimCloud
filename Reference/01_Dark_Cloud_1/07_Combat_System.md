# Dark Cloud 1 — Combat System

## Overview
Real-time action combat with Zelda-style lock-on, charge attacks, and QTE "Duels". 6 characters with distinct weapon types and ranges.

---

## Core Controls (PS2)

| Input | Action |
|-------|--------|
| **○ (Circle)** | Lock-on / Cycle targets |
| **× (Cross)** | Attack (tap = combo, hold = charge) |
| **□ (Square)** | Use equipped item (water, repair, bomb) |
| **△ (Triangle)** | Character menu / Switch (hold) |
| **L1** | Guard / Block |
| **R1** | Strafe (while locked) |
| **L2/R2** | Camera adjust |
| **Select** | Georama Mode |
| **Start** | Pause / Main Menu |

---

## Lock-On System

### Mechanics
- **○** → Locks to nearest enemy in forward cone
- **○ (held)** → Cycle targets (L1/R1 also cycle)
- **Lock range** — ~15m; breaks if enemy leaves range or dies
- **Camera** — Centers on locked target; right stick adjusts offset

### Lock-On Benefits
| Benefit | Detail |
|---------|--------|
| **Auto-facing** | Character always faces target |
| **Strafe** | L1 + move = circle strafe |
| **Charge aim** | Charge attack homes slightly |
| **Target info** | Enemy name, HP bar, element weakness shown (after scan) |

---

## Attack Types

### Basic Combo (Tap ×)
| Character | Hits | Properties |
|-----------|------|------------|
| **Toan** | 3 | Fast, forward-moving, 3rd hit knockback |
| **Xiao** | 4 | Rapid pellets; last hit multi-shot |
| **Goro** | 2 | Slow, high damage, overhead smash |
| **Ruby** | 3 | Ring projectiles; element follows ring |
| **Ungaga** | 3 | Wide 180° sweeps; 3rd hits behind |
| **Osmond** | 1 | Single shot; hold for rapid fire |

### Charge Attack (Hold × → Release)
| Character | Charge Time | Effect | WHP Cost |
|-----------|-------------|--------|----------|
| **Toan** | 1.5s | Spin Slash (360° AoE, 5 hits) | 2 |
| **Xiao** | 1.0s | Power Shot (piercing, 3× dmg) | 1 |
| **Goro** | 2.0s | Ground Smash (AoE stun, 4× dmg) | 3 |
| **Ruby** | 1.5s | Elemental Burst (ring element AoE) | 2 |
| **Ungaga** | 1.5s | Whirlwind Staff (multi-hit, vacuum) | 2 |
| **Osmond** | 1.0s | Burst Fire (5 rounds, spread) | 2 |

---

## Guard & Dodge

### Guard (Hold L1)
- **Blocks** frontal melee/ranged
- **Reduces** damage by 75% (melee), 50% (magic)
- **No WHP cost** — but weapon doesn't lose WHP on block
- **Perfect Guard** — Release L1 *exactly* on impact → Parry → Enemy stunned 2s

### Dodge (L1 + Direction ×)
- **Quick step** — 3m; 10-frame invincibility (frames 3–13)
- **No resource cost**
- **Can't dodge** while attacking (animation lock)

---

## Duel System (QTE)

### Trigger
- **Random** on enemy encounter (~5% chance)
- **Forced** on story bosses, mini-bosses
- **Visual** — Screen flashes; "DUEL" text; camera zooms

### Mechanics
| Phase | Input | Window | Fail State |
|-------|-------|--------|------------|
| **Prompt** | × / ○ / □ / △ / ←/→/↑/↓ | 1.5s | Enemy free attack |
| **Sequence** | 3–6 inputs | 1.0s each | Duel ends; normal combat |
| **Success** | All correct | — | Massive damage + ABS bonus |

### Duel Rewards
| Result | Reward |
|--------|--------|
| Perfect | 2× ABS, rare drop chance +20% |
| Success | 1.5× ABS |
| Fail | Normal combat; enemy enraged |

---

## Enemy Weakness System

### Elemental Weakness
| Element | Strong vs | Weak vs |
|---------|-----------|---------|
| **Fire** | Beast, Plant | Water, Armored |
| **Ice** | Fire, Dragon | Fire, Armored |
| **Lightning** | Water, Machine | Earth, Dragon |
| **Wind** | Flying, Plant | Earth, Heavy |
| **Holy** | Undead, Demon | Dark, Machine |

### Anti-Type Crystals (Weapon Attachments)
| Crystal | Target Family | Damage Mult |
|---------|---------------|-------------|
| **Beast** | Mammals, Beasts | ×1.5 |
| **Scale** | Reptiles, Dragons | ×1.5 |
| **Exorcism** | Undead, Spirits | ×2.0 |
| **Smash** | Armored, Golems | ×1.5 |
| **Cyclone** | Flying, Insects | ×1.5 |

> **Note**: Elemental + Anti-Type stack multiplicatively (e.g., Fire + Beast vs Fire-weak Beast = ×2.25)

---

## Status Effects

| Effect | Source | Duration | Cure |
|--------|--------|----------|------|
| **Poison** | Enemy attacks, traps | 30s (tick 1/s) | Antidote, Spring |
| **Curse** | Dark enemies | Until cured | Holy Water, Spring |
| **Slow** | Ice attacks, traps | 15s | Warmth, Spring |
| **Confusion** | Gas, magic | 10s | Clarity, Spring |
| **Petrify** | Gorgon, basilisks | Instant death if not cured | Softener, Spring |

---

## Party Mechanics

### Active Party
- **3 characters max** (Toan + 2)
- **Switch**: Hold △ → Select portrait → Release
- **Instant swap** — No cooldown; position preserved

### AI Companions (When Not Controlled)
| Behavior | Detail |
|----------|--------|
| **Follow** | Stay near player; auto-attack enemies in range |
| **Guard** | Prioritize blocking; attack only if attacked |
| **Aggressive** | Seek enemies; use charge attacks freely |

> **AI is poor** — Often stuck on geometry; wastes WHP; ignores weaknesses

### Character-Specific Traversal (Combat Utility)
| Char | Ability | Combat Use |
|------|---------|------------|
| **Xiao** | Jump | Avoid ground AoE; reach flying enemies |
| **Goro** | Rock Break | Destroy cover; stun enemies behind |
| **Ruby** | Float | Hover over hazards; aerial attacks |
| **Ungaga** | Sandwalk | Navigate quicksand arenas |
| **Osmond** | Door Shot | Open shortcuts mid-fight |

---

## Damage Formula (Simplified)

```
Final Damage = Base Weapon ATK
  × (1 + STR_Attachment_Bonus)
  × Element_Multiplier (if enemy weak)
  × AntiType_Multiplier (if crystal matches)
  × Charge_Multiplier (1.0 tap / 2.0–4.0 charge)
  × Critical_Multiplier (1.5× base, 2.0× with Critical attachment)
  − Enemy_DEF (reduced by Smash vs armored)
  ± Variance (±5%)
```

---

## Combat Flow Example (Toan vs. Lizard Man)

1. **Lock-on** (○) → See HP, weakness (Ice)
2. **Equip Ice Crystal** on sword (if not already)
3. **Approach** → **Guard** (L1) → **Perfect Guard** on bite
4. **Counter** → 3-hit combo → **Charge** (hold ×)
5. **Release** → Spin Slash hits 3× → Lizard Man dies
6. **Collect ABS** (blue orbs) → Weapon XP +60
7. **Check WHP** → Repair if <20

---

## Overseas Version Improvements
- **Enemy AI** — Less wall-hugging; better pathfinding
- **Duel frequency** — Slightly increased; more variety
- **Camera** — Less jitter on lock-on; better corner handling
- **Hitboxes** — More consistent; fewer "ghost hits"

---

## Design Analysis

### Strengths
- **Simple depth** — 3 buttons create expressive combat
- **Weapon as progression** — Every hit feels meaningful (ABS)
- **Character variety** — Melee/ranged/traversal all matter
- **Duel QTEs** — Tension spikes; reward mastery

### Weaknesses
- **AI companions useless** — Solo play optimal
- **Guard trivializes** — Hold L1 = near-invincible
- **Charge spam** — Spin Slash / Ground Smash solve 90% encounters
- **No stagger system** — Enemies don't flinch reliably

### DC2 Evolution
- **Two protagonists** — Max (melee+gun+Ridepod) + Monica (sword+armband+monster)
- **Ridepod** — Separate vehicle combat mode
- **Monster Transformation** — Monica becomes enemy (new movesets)
- **Medal system** — Objectives per floor (Time, Wipeout, No Heal, Spheda, Fish)

