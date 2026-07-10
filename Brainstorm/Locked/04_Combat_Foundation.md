# Locked: Combat Foundation & Stance Matrix

*Canonical combat design for DimCloud. Do not modify without explicit discussion.*

---

## Decision Summary

| # | Decision | Status |
|---|----------|--------|
| 1 | One distinct weapon **per stance** → 9 weapons total (3 heroes × 3 stances) | ✅ Locked |
| 2 | Each weapon has its **own Weapon Legacy** (Memory / Evolution / Memory Core) | ✅ Locked |
| 3 | Universal move kit shared by all 9 weapons | ✅ Locked |
| 4 | Stances differ by **archetype pros/cons**, not by selectable abilities | ✅ Locked |
| 5 | Stance archetypes: Melee / Ranged / Special | ✅ Locked |

---

## The 9 Weapons

| Hero | Melee Weapon | Ranged Weapon | Special Weapon |
|------|--------------|---------------|----------------|
| **Evoker** | Rune Blade | Spell Bolt (wand/staff) | Elemental Cast (grimoire) |
| **Machinist** | Wrench-Hammer | Sidearm (launcher) | Gadget Deploy (toolkit) |
| **Cyborg** | Arm-Blade | Drone Swarm (emitter) | Overload (cyber-core) |

Each weapon grows independently via the Weapon Legacy system (see `Locked/01_Design_Pillars.md` Pillar 1).

---

## Universal Move Kit (all 9 weapons)

A consistent control language across every weapon:

| Move | Function | Notes |
|------|----------|-------|
| **Light Attack** | Fast, low damage, combo starter | Builds combo meter |
| **Heavy Attack** | Slow, high damage, stance-flavored property | Melee: knockback · Ranged: pierce · Special: status apply |
| **Charged Attack** | Hold to channel, powerful release | Consumes Stamina/Charge |
| **Block / Parry** | Defensive | Effectiveness scales with stance (Melee best) |
| **Dodge / Roll** | Mobility, i-frames | Universal escape tool |
| **Stance Swap** | Instant switch among a hero's 3 weapons | L1/R1; cooldown TBD |
| **Resonance Ultimate** | Spend shared Resonance resource | Big signature effect per weapon |

> The **Light / Heavy / Charged** attack triangle satisfies Sets of 3 *within* the universal kit.

---

## Stance Archetype Profiles

Differentiation comes from archetype, not loadouts:

### Melee
- **+** High close-range ATK & DEF; best Block/Parry; strong crowd control (knockback)
- **−** Short range; few/no ranged options; vulnerable to flyers & ranged enemies

### Ranged
- **+** Long range; kiting; weak-point targeting; safe damage
- **−** Lower DEF; poor Block; punished if surrounded / in melee

### Special
- **+** Unique utility (deploy / hijack / cast); applies **status effects**; often AoE or persistent field
- **−** Resource-gated; situational; lower raw DPS; premium on positioning/timing

---

## Resonance (Ultimate Resource)

| Property | Rule |
|----------|------|
| **Scope** | Per **hero**, shared across that hero's 3 stances |
| **Build — consecutive hits** | Each landed hit adds Resonance |
| **Build — combo bonus** | Longer combos build Resonance *faster* |
| **Build — perfect defense** | Perfect Dodge / Perfect Block grant bonus Resonance |
| **Decay** | Resonance **drains over time** when not building |
| **Decay — on hit** | Taking hits drains Resonance |
| **Spend — Resonance Finisher** | Drains **all** banked Resonance to empower a combo finishing move |
| **Finisher scaling** | Higher banked value → stronger / different Finisher (tiered thresholds; candidate: 3 tiers to satisfy Sets of 3) |

> Design intent: the stance-swap is meaningful — bank Resonance on one weapon, unleash the Finisher on the stance whose Ultimate best fits the moment.

---

## Defensive System (2-Option Model)

Two defensive options — **Block** and **Dodge** — each with a **Perfect** variant. Perfect actions grant Resonance and reduce enemy Stamina; normal Block *drains* Resonance.

| Option | Normal | Perfect Variant | Cost | Reward |
|--------|--------|-----------------|-------|--------|
| **Block** (hold) | Damage reduction / negation | **Perfect Block** (= Parry): full damage negation | Stamina **+ Resonance loss** (normal) · Stamina only (perfect) | Perfect: **+Resonance, −Enemy Stamina** |
| **Dodge** (roll) | Damage avoidance via i-frames | **Perfect Dodge**: avoidance via i-frames | Stamina (both) | Perfect: **+Resonance, −Enemy Stamina** |

### Rules
- **Block** — Damage reduced/negated in exchange for **Stamina loss and Resonance loss**. (Holding block while Resonance is banked bleeds the ultimate resource — blocking is safe but taxes your Finisher.)
- **Perfect Block (Parry)** — Full damage negation in exchange for **Stamina loss only**. Grants **Resonance**; **reduces enemy Stamina**.
- **Dodge** — Damage avoidance in exchange for **Stamina loss**; grants an **i-frame window**.
- **Perfect Dodge** — Damage avoidance in exchange for **Stamina loss**; **i-frame window** + grants **Resonance**; **reduces enemy Stamina**.

### Timing Model (tuning values — subject to playtest)
- **Perfect Block window**: ~200 ms before impact (Melee +50 ms, Ranged −50 ms)
- **Dodge i-frames**: ~300 ms active
- **Perfect Dodge**: initiate within ~150 ms before hit → ~500 ms i-frames + Resonance

### Stance Scaling
- **Block %**: Melee best, Special medium, Ranged weakest (Ranged leans on Dodge).
- **Perfect Block window**: Melee widest, Ranged narrowest.

### Design Intent
- Block = *mitigation with a Resonance tax* — safe but costs your ultimate economy.
- Perfect Block / Perfect Dodge = *skill-expression* — negate cost, refund Resonance, and pressure enemy Stamina.
- Dodge = *mobility* — universal escape, Ranged's primary survival tool.

---

## Weapon Memory — Principle (locked)

| Property | Rule |
|----------|------|
| **Breadth** | Per-weapon Memory tracks a **broad set of telemetry values** — NOT constrained to Sets of 3 |
| **Rationale** | Wide breadth of Memory enables more varied / creative weapon advancement trees |
| **Candidate metrics** | Kill Count, Block Count, Perfect Block, Perfect Dodge, Resonance Finisher Count, Bosses Slain, Biomes Explored, Consecutive-Hit Records, etc. |
| **Scope note on Sets of 3** | The Sets of 3 rule governs *system structure* (choices / phases / sub-components), **not** granular stat/telemetry tracking. Memory metrics are data, not choices. |

> Full Memory design (which metrics gate which evolutions, how Memory Cores form) is **DEFERRED**.

---

## Open Items (not yet locked)

- **Status Effect set** (DEFERRED): likely **unique per character & non-elemental** for Special weapons; **elemental effects** applied via equipped weapon / essences. No set locked yet.
- **Full Weapon Memory / Evolution tree design**: deferred (principle above locked; detail TBD).
