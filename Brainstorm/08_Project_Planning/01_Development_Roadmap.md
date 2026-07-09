# Brainstorm: Project Planning — Successor Development Roadmap

*All content is theorycraft/non-canon for a spiritual successor.*

---

## Project Overview

| Attribute | Value |
|-----------|-------|
| **Codename** | DimCloud |
| **Genre** | Action RPG + World Simulation + Community Platform |
| **Target Platforms** | PC (Win/Linux), PS5, Xbox Series, Switch 2 |
| **Engine** | Custom v5.0 (Mesh Shaders + RT + Compute + ECS) |
| **Team Size** | 25 Core → 40 Full Production |
| **Timeline** | 36 Months to 1.0 |
| **Budget Class** | AA (Indie-AAA Hybrid) |

---

## Phase Gates

### Phase 0: Pre-Production (Months 0-6)
**Goal**: Architecture locked; Core systems prototyped; Vertical Slice defined

| Week | Deliverable | Owner |
|------|-------------|-------|
| 1-2 | Architecture Doc v1.0; Tech Stack Decisions | Tech Director |
| 3-4 | ECS Framework; Job System; Asset Pipeline | Core Engine |
| 5-8 | Procedural Dungeon Prototype (Room Graph + Population) | Proc Systems |
| 9-12 | Weapon System Prototype (ABS + SP + Spectrumize) | Systems |
| 13-16 | Georama Prototype (Grid + Blueprints + Conditions) | Systems |
| 17-20 | Vertical Slice: Dungeon → Loot → Build → Next Dungeon | All |
| 21-24 | Architecture Review; Phase Gate Decision | Leadership |

**Exit Criteria**: 
- [ ] 30-min playable loop (Dungeon → Georama → Dungeon)
- [ ] All core systems communicating via Event Bus
- [ ] Deterministic replay working
- [ ] Team velocity > 20 pts/sprint

---

### Phase 1: MVP — Core Loop (Months 6-12)
**Goal**: Full DC1-equivalent loop playable; DC2 systems scaffolded

| Sprint | Focus | Key Features |
|--------|-------|--------------|
| 1-2 | Dungeon Polish | 6 Themes; 15 Floors; Key Enemy; Back-Doors; Medals |
| 3-4 | Weapon System | ABS; SP; Spectrumize; Build Up; SynthSphere; Visible Trees |
| 5-6 | Georama 1.0 | Grid; Blueprints; Materials; CP; 10 Conditions; Future Chests |
| 7-8 | Character System | 2 Protagonists (Melee/Ranged); Traversal; Swap |
| 9-10 | Ridepod Scaffold | Frame/Legs/Arms/Weapons; Fuel; Invention Parts |
| 11-12 | Monster Transform Scaffold | 4 Badges; Gift Capsule; Evolution |
| 13-14 | Invention/Photo Scaffold | Camera; 3-Photo → Idea → Blueprint → Materials → Assemble |
| 15-16 | Fishing/Spheda Scaffold | Rods; Bait; Aquarium (Rec); Distortion Repair |
| 17-18 | Support NPCs | 4 Recruitable; Passive Buffs (SP/Map/Keys) |
| 19-20 | Polish + Phase Gate | 2-Hour Playtest; Bug Bash; Performance Target |

**MVP Exit Criteria**:
- [ ] 6 Dungeons × 15 Floors = 90 Floors playable
- [ ] 6 Georama Areas (Past/Future pairs)
- [ ] 100+ Weapons with full Evolution Trees
- [ ] 50 Inventions; 10 Ridepod Parts; 4 Transform Forms
- [ ] 30-min Session Loop without critical bugs
- [ ] 60 fps @ 1080p on target hardware

---

### Phase 2: Alpha — Feature Complete (Months 12-18)
**Goal**: Full DC2 feature parity (minus Time Travel Georama)

| Month | Focus | Key Deliverables |
|-------|-------|------------------|
| 13-14 | Dual Protagonist Deep | Max (Wrench/Gun/Steve) + Monica (Sword/Armband/Monster) |
| 15-16 | Ridepod Deep | Full Customization; Parts Spectrumize; Fuel System |
| 17-18 | Monster Transform Deep | 12 Badges; Evolution Branches; Moon/Sun Meta-Badges |
| 19-20 | Invention/Photo Complete | 130 Inventions; Scoop Photos; Idea Board; Blueprint Unlocks |
| 21-22 | Fishing/Finny Frenzy Complete | 3 Aquarium Types; 42 Breeding Combos; Racing Tiers |
| 23-22 | Medal System Complete | 396 Medals; Time Trial/Wipeout/Spheda/Fish/NoHeal/Weapon |
| 23-24 | Support NPCs Complete | 10 NPCs; Recruitment Quests; Passive/Active/Ultimate Skills |
| 25-24 | Time Travel Georama | Past Build → Future Alteration; Future Chests; Era Swap |
| 25-26 | Polish + Alpha Gate | Full Playthrough; 20+ Hours; No Progression Blockers |

**Alpha Exit Criteria**:
- [ ] 7 Chapters + Post-Game (Zelmite Mines) playable
- [ ] All 12 Systems interlocked (Event Bus verified)
- [ ] 40-Hour Playthrough tested
- [ ] Save/Load anywhere working
- [ ] Performance: 60 fps @ 1440p (PC) / 30 fps @ 4K (Console)

---

### Phase 3: Beta — Successor Identity (Months 18-27)
**Goal**: DC2 parity + Successor differentiators (Multi-Era, Legacy, Community)

| Month | Focus | Key Differentiators |
|-------|-------|---------------------|
| 25-26 | Multi-Era Georama | 4 Eras (Ancient/Recent/Present/Future); Simultaneous Sim |
| 27-28 | Parametric Blueprints | Slots/Params/Constraints/Outputs/Upgrade Paths |
| 29-30 | Continuous Simulation | Agents/Economy/Ecology/Threats; Offline Progress |
| 31-32 | Legacy Forge | Maxed Weapon → Memory Core → Global Trait Unlock |
| 33-34 | Blueprint Library | Personal/Community; Fork/Remix/Vote/Canon Integration |
| 35-36 | Procedural Seeds | Seed Format; Daily/Weekly; Creator Tools; Remix |
| 37-36 | Ripple Causality | Past Action → Present State → Future Outcome Visualizer |
| 37-38 | Companion Synergy | Mech+Transform+NPC Pair Bonuses; Legion Mode |
| 39-40 | Creative Crafting v2 | Scan→Analyze→Blueprint→Simulate→Fabricate→Deploy |
| 41-42 | Mastery Tracks | 7 Tracks; Cross-Track Synergies; Respec System |
| 43-44 | Polish + Beta Gate | 60-Hour Playtest; Community Alpha; Performance Targets |

**Beta Exit Criteria**:
- [ ] 4 Eras simultaneously simulated
- [ ] 100+ Parametric Blueprints
- [ ] 24-Hour Offline Progress visible
- [ ] 100+ Legacy Traits unlockable
- [ ] 10,000+ Community Blueprints seeded
- [ ] 100+ Procedural Seeds in rotation
- [ ] 60 fps @ 4K (PC Ultra) / 60 fps @ 1440p (Console)

---

### Phase 4: 1.0 — Spiritual Successor Identity (Months 27-36)
**Goal**: Launch-ready; Living Platform foundation

| Month | Focus | Launch Criteria |
|-------|-------|-----------------|
| 37-38 | Community Platform | Blueprint Hub; Seed Vault; Canon Voting; Mod Portal |
| 39-40 | Mod Support | Lua/WASM Sandbox; Asset Pipeline; Curated Workshop |
| 41-40 | Seasonal Content | Quarterly Seed Rotations; Themed Events; Canon Updates |
| 41-42 | Accessibility | Full Remapping; Visual/Audio Options; Difficulty Modifiers |
| 41-42 | Localization | EFIGS + CN/KR/JP; Cultural Adaptation |
| 41-42 | Certification | Console Cert; Steam Deck Verified; Steam Deck Verified |
| 43-44 | Launch Prep | Marketing Assets; Press Builds; Server Stress Test |
| 45-46 | **LAUNCH** | **Day 1 Patch Ready; Live Ops Team Handoff** |

**1.0 Exit Criteria**:
- [ ] Metacritic Target: 85+
- [ ] Steam Reviews: Very Positive (>85%)
- [ ] D7/D30 Retention: 45% / 25%
- [ ] Blueprint Shares/Month: >10k
- [ ] Seed Completion Rate: >60% (Daily)
- [ ] Legacy Traits Unlocked/Player: >5 by Hour 20
- [ ] Community Canon Designs: >100 by Launch + 6 Months
- [ ] Cross-Pillar Engagement: >70% Players Use 3+ Pillars

---

## Team Ramp Plan

| Phase | Core | Engine | Systems | Content | Tools/QA | Total |
|-------|------|--------|---------|---------|----------|-------|
| Pre-Prod (0-6) | 4 | 4 | 3 | 2 | 2 | **15** |
| MVP (6-12) | 4 | 5 | 6 | 6 | 4 | **25** |
| Alpha (12-18) | 4 | 6 | 8 | 10 | 6 | **34** |
| Beta (18-27) | 5 | 6 | 8 | 12 | 8 | **39** |
| 1.0 (27-36) | 5 | 6 | 8 | 10 | 10 | **39** |

### Role Definitions
| Role | Count | Focus |
|------|-------|-------|
| **Tech Director** | 1 | Architecture; Engine Decisions |
| **Core Engine** | 4 | Memory; Job System; ECS; Asset Pipeline |
| **Rendering** | 3 | Mesh Shaders; RT; Compute; Cel Pipeline |
| **Simulation** | 3 | AI; Economy; Ecology; World State |
| **Procedural** | 3 | Dungeon/World/Seed Systems |
| **Systems Design** | 4 | Weapon/Georama/Companion/Invention/Medal |
| **Content/Level** | 6 | Dungeons; Blueprints; Enemies; Quests |
| **Art/Animation** | 8 | Characters; Environments; VFX; UI |
| **Audio** | 2 | Music; SFX; Adaptive Systems |
| **Tools/Pipeline** | 3 | Graph Editors; Hot-Reload; CI/CD |
| **QA/UR** | 4 | Playtesting; Automation; Accessibility |
| **Production** | 3 | Scheduling; Dependencies; Risk |
| **Community/Live** | 3 | Blueprint Hub; Seasons; Mods; Events |

---

## Budget Allocation (Estimated)

| Category | % of Budget | Notes |
|----------|-------------|-------|
| **Personnel** | 65% | 39 FTE avg × 36 months |
| **Engine/Tools** | 10% | Licenses; Cloud Build; Profiling |
| **Art Outsource** | 8% | High-fidelity assets; Scan cleanup |
| **Audio** | 3% | Composer; Orchestral; Adaptive |
| **QA/Localization** | 5% | 12 Languages; Cert Testing |
| **Marketing/PR** | 5% | Trailers; Events; Influencers |
| **Infrastructure** | 2% | Servers; CDN; Analytics; Mod Hosting |
| **Contingency** | 2% | Risk Buffer |
| **Total** | **100%** | |

---

## Risk Register

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| **Engine Rewrite Delay** | Medium | High | Phase-gated rewrites; Keep v4 fallback |
| **Simulation Performance** | High | High | GPU Agent Compute; LOD Sim Distance |
| **Scope Creep** | High | Medium | Phase Gates; Fixed MVP; Stretch = Post-Launch |
| **Community Content Quality** | Medium | Medium | Automated Validation + Curator Tier |
| **Cross-Platform Cert** | Low | High | Early Devkit Access; Parallel Cert |
| **Key Personnel Loss** | Low | High | Documentation; Bus Factor ≥2 per System |
| **Market Shift** | Low | Medium | Flexible Launch Window; Live Ops Ready |
| **Technical Debt** | Medium | Medium | 20% Sprint Capacity for Refactor |

---

## Success Metrics Dashboard

| KPI | Target | Measurement |
|-----|--------|-------------|
| **Loop Retention (D7/D30)** | 45% / 25% | Analytics |
| **Georama Session Length** | >30 min avg | Analytics |
| **Blueprint Shares/Month** | >10k | Platform |
| **Seed Completion Rate** | >60% (Daily) | Analytics |
| **Legacy Traits/Player (Hr 20)** | >5 | Analytics |
| **Community Canon Designs** | >100 (Launch+6mo) | Platform |
| **Cross-Pillar Engagement** | >70% (3+ Pillars) | Analytics |
| **Steam Reviews** | Very Positive (>85%) | Steam |
| **Metacritic** | 85+ | Aggregator |
| **DLC/Season Pass Attach** | >30% | Platform |

---

## Go/No-Go Decision Points

| Gate | When | Criteria | Authority |
|------|------|----------|-----------|
| **Pre-Prod → MVP** | Month 6 | Vertical Slice playable; Architecture Review passed | Tech Dir + Prod |
| **MVP → Alpha** | Month 12 | 6 Dungeons + 6 Georama playable; 30-min loop | Tech Dir + Prod + Creative Dir |
| **Alpha → Beta** | Month 18 | DC2 Feature Parity; Time Travel Georama working | Tech Dir + Prod + Creative Dir |
| **Beta → 1.0** | Month 27 | All Differentiators working; Community Alpha positive | Studio Head + Publisher |
| **Launch** | Month 36 | Cert Passed; Day 1 Patch Ready; Live Ops Ready | Studio Head + Publisher |

---

## Post-Launch Roadmap (Year 1)

| Quarter | Theme | Content |
|---------|-------|---------|
| **Q1** | "Foundations" | Mod Tools v1; Seasonal Seed Rotation #1; Bug Fixes |
| **Q2** | "Expansion" | New Era (Pleistocene); 20 Blueprints; 5 Seeds; Mod API v2 |
| **Q3** | "Community" | Canon Vote #1 Results; Creator Spotlight; Mod Contest |
| **Q4** | "Legacy" | Major Expansion (New Continent); Cross-Play; Year 1 Review |

---

*"We didn't carry over code from Dark Cloud to Dark Cloud 2. We threw it all away. But we carried over the experience. The next engine must do the same: discard the code, keep the wisdom."* — Akihiro Hino (Paraphrased)