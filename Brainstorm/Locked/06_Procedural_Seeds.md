# Locked: Procedural Seeds

*Canonical procedural-content design for DimCloud. Do not modify without explicit discussion.*

---

## Decision Summary

| # | Decision | Status |
|---|----------|--------|
| 1 | Dungeon generation seeded by **Dungeon Id + Stage Id + Attempt Count** (deterministic, local) | ✅ Locked |
| 2 | **No** multiplayer, seed-sharing, or cross-platform parity requirements | ✅ Locked |
| 3 | 3 Difficulty Tiers (Sets of 3): Standard / Heroic / Mythic | ✅ Locked |
| 4 | Each stage has **3 challenges** drawn from a larger objective-type pool (objectives are content, not a choice → Sets of 3 N/A) | ✅ Locked |
| 5 | Causal link: each era's **Georama world-state** modulates dungeon content (enemy / reward / biome tables) | ✅ Locked |
| 6 | Replay value: tiers + attempt variation support farming (components) and weapon power-leveling | ✅ Locked |

---

## Seed Model (deterministic, local)

- A dungeon stage's layout/variation is generated from:
  ```
  Seed = DungeonId + StageId + AttemptCount
  ```
- Identical seed → identical layout on repeat attempts (**reproducible farming**).
- **No sharing / parity needed** — determinism serves *replay*, not distribution.

---

## Difficulty Tiers (Sets of 3)

| Tier | Effect |
|------|--------|
| **Standard** | Baseline enemy scaling |
| **Heroic** | Increased density / stats; improved rewards |
| **Mythic** | Max scaling; rare essences / legacy fragments |

> Replay incentive: farm specific components, or power-level specific weapons, at the tier that fits the goal.

---

## Objective Challenges

- Each stage exposes **3 challenges** (e.g., clear / time / no-hit).
- Challenges are drawn from a **broad pool** of objective types — *not* limited to 3:
  - Time Trial · No Hit · Character Lock · Stance Lock · Collection (essences) · Photo · Speed · Boss-Only · etc.
- **Sets of 3 does not apply here**: objectives are authored content, not a player choice architecture, so the pool may be wider than 3.

---

## Causal Integration: Georama → Dungeon Content

- Dungeon **content** (enemy table / reward table / biome) is driven by the **era's Georama state** (WFC-collapsed layers + mutators) — not by a separate shareable seed.
- Example: corruption mutator in Distant Past → WFC → Present corrupted biome → Present-era dungeons spawn corrupted enemy tables + corruption essences.
- Dungeon completion → **essences / components** → feed **Weapon Legacy** (Memory, infusion) and **Creative Crafting**.
- Stage **mastery (100%)** → unlocks a **Legacy Blueprint** (Mastery Progression pillar).

---

## Replay Loop

Players replay stages to:
- Farm specific Georama / crafting components
- Power-level specific weapons (Memory telemetry accrues)
- Chase tier challenges / complete the 3 stage objectives

---

## Open Items (not yet locked)

- **Objective pool**: which types ship in MVP vs. post-launch.
- **Attempt Count reset**: per session / per day / manual "new attempt" button.
- **Tier reward differentials**: exact essence / drop multipliers per tier.
- **Brainstorm reconciliation**: `05_Engine_Architecture` Seed JSON (shareable format) and `04_Core_Loops` seed-integration are **superseded** — the local seed model replaces the shareable-seed model.
