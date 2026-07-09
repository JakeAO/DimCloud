# Dark Cloud Series Reference Index

> **Comprehensive documentation for Dark Cloud (2000) and Dark Cloud 2 / Dark Chronicle (2002) — mechanics, systems, design philosophy.**

---

## Folder Structure

```
Reference/
├── 01_Dark_Cloud_1/           # Dark Cloud (DC1) Systems
├── 02_Dark_Cloud_2/           # Dark Cloud 2 / Dark Chronicle Systems
├── 03_Comparative_Analysis/   # Cross-Game Analysis & Evolution
├── 04_Reference_Sheets/       # Machine-Readable Data (JSON)
├── 05_Lore_Narrative/         # Story, Characters, Worldbuilding
└── 06_Technical_Reference/    # Engine, Hardware, Technical Notes
```

---

## 01_Dark_Cloud_1 — Core Systems

| File | Description |
|------|-------------|
| `01_Core_Gameplay_Loop.md` | Dungeon→Atla→Georama→Hub loop; procedural generation; pacing |
| `02_Georama_System.md` | Atla→Pieces→Placement→Villager Requests→Rewards |
| `03_Weapon_System.md` | ABS, Attachments, Upgrade, Build Up, SynthSphere, WHP, Evolution Trees |
| `04_Character_System.md` | 6 Characters, Traversal, Stat Items (Fruit/Gourd/Defense), Thirst |
| `05_Dungeon_System.md` | 6 Dungeons, Floor Generation, Key Enemy, Back-Doors, Bosses |
| `06_Character_Progression.md` | Finite Stat Allocation, Thirst Management, Save-Scum Strategy |
| `07_Combat_System.md` | Lock-on, Charge, Guard, Duel QTE, Elemental/Anti-Type, Party AI |
| `08_Inventory_Management.md` | Slot Limits, Stacking, Loadout Templates, Economy, QoL |
| `09_Atla_Atlamillia_Lore.md` | Fairy King, Atla Spheres, Atlamillia Stone, Dark Genie |
| `10_Design_Philosophy_Hino_Interviews.md` | Hino Quotes, "Georama RPG", DC1.5 Overseas Version |
| `11_Weapon_Evolution_Charts.md` | Per-Character Weapon Trees with Build Up Requirements |

---

## 02_Dark_Cloud_2 — Core Systems

| File | Description |
|------|-------------|
| `01_Core_Gameplay_Loop.md` | Dual Protagonist, Time Travel, Georama 2.0, Medal/Photo/Fish Systems |
| `02_Georama_Time_Travel.md` | Geostones→Blueprints→Materials→Conditions→Future Alteration |
| `03_Weapon_System_2.0.md` | SP, Spectrumize, SynthSphere, Build Up Trees, Ridepod, Durability |
| `04_Dual_Protagonist_System.md` | Max (Wrench/Gun/Steve) + Monica (Sword/Armband/Monster Forms) |
| `05_Ridepod_Steve_System.md` | Frame/Legs/Arms/Weapons/Fuel; Invention Parts; Customization |
| `06_Invention_Photography_System.md` | Camera→Photos(3)→Idea→Materials→130 Inventions |
| `07_Monster_Transformation.md` | 12 Badges (Gift Capsule/Special), Evolution, Traversal, Moon/Sun |
| `08_Medal_System.md` | 396 Medals (Time/Wipeout/Spheda/Fish/NoHeal/Weapon) → Mayor Need |
| `09_Spheda_Golf.md` | Color-Switch Sphere, Distortion Repair, Physics, Rewards |
| `10_Fishing_Finny_Frenzy.md` | Rods/Bait, Aquarium(3 Types), 42 Breeding Combos, Racing Tiers |
| `11_Support_Characters.md` | 10 Recruitable NPCs → Passive Buffs (SP/Map/Keys/Lures/Badges) |
| `12_Design_Philosophy_Evolution.md` | Hino: "DC2 was the game we wanted to make"; Systems Interlock |
| `13_Weapon_Evolution_Charts.md` | Max/Monica/Steve Trees with Build Up Requirements |

---

## 03_Comparative_Analysis — Evolution & Synthesis

| File | Description |
|------|-------------|
| `01_Systems_Evolution.md` | Core Loop, Weapon, Georama, Character, New Systems, Removed Systems |
| `02_Design_Philosophy_Synthesis.md` | Hino Quotes → 7 Core Pillars → Anti-Pillars → Formula |
| `03_Core_Loop_Comparison.md` | DC1 Linear vs DC2 Causal Web |
| `04_Weapon_System_Evolution.md` | Slots→SP, Hidden→Visible, Break→Condition |
| `05_Georama_Evolution.md` | Placement→Causal Time Travel→Simulation |

---

## 04_Reference_Sheets — Machine-Readable Data (JSON)

| File | Contents |
|------|----------|
| `DC1_Weapon_Attributes.json` | 10 Attributes, Attachment Types, SynthSphere, Build Up, Durability |
| `DC1_Character_Stats.json` | 6 Characters: HP/Def/Thirst/Traversal/Weapon/Ultimate/Allocation |
| `DC1_Georama_Villager_Requests.json` | 6 Villages, All Requests, 100% Rewards |
| `DC2_Weapon_Attributes.json` | 10 Attributes, SP System, Spectrumize Rates, Build Up, Steve/Monster |
| `DC2_Invention_Recipes.json` | 130 Inventions, Pipeline, Photo Points, Scoops, Key Inventions, Materials |
| `DC2_Monster_Badges.json` | 12 Badges + Moon/Sun: Method, Target, Form, Traversal, Skills, Evolution |
| `DC2_Fish_Breeding.json` | Tank Types, Stat Feeding, 18 Breeding Combos, Finny Frenzy Tiers |
| `DC2_Medal_Requirements.json` | 396 Medals, Chapter Breakdown, Time Trial Tips, Mayor Need Shop |
| `DC2_Georama_Parts.json` | 6 Categories, Area Mechanics, 7 Condition Types, Economy |

---

## 05_Lore_Narrative — Story & World

| File | Description |
|------|-------------|
| `DC1_Story_Characters.md` | Toan, 5 Companions, Seda, Dark Genie, Fairy King, Moon People |
| `DC2_Story_Characters.md` | Max, Monica, Steve, Griffon, Cedric, Lin, Future/Past NPCs |
| `World_Building_Atlamillia_Lore.md` | Three Atlamillia (Sun/Moon/Earth), Time Travel Rules, Galaxy |
| `Timeline_Connections.md` | How DC1→DC2 Connect; Atlamillia Continuity; Seda's Arc |

---

## 06_Technical_Reference — Engine & Hardware

| File | Description |
|------|-------------|
| `PS2_Hardware_Constraints.md` | 32MB RAM, 4MB VRAM, VU0/VU1, GS Bandwidth, DVD Streaming |
| `Procedural_Generation_Notes.md` | Room Templates, Connection Graphs, Enemy Tables, Seed Storage |
| `Level5_Engine_Evolution.md` | DC1 Engine → DC2 Rewrite → Dragon Quest VIII → Rogue Galaxy |
| `Cel_Shading_Rendering.md` | DC2 Cel-Shading Pipeline, Outline, Bloom, Soft Textures, 60fps Target |

---

## Quick Navigation by Topic

### Weapon Systems
- DC1: `01_Dark_Cloud_1/03_Weapon_System.md` + `04_Reference_Sheets/DC1_Weapon_Attributes.json`
- DC2: `02_Dark_Cloud_2/03_Weapon_System_2.0.md` + `04_Reference_Sheets/DC2_Weapon_Attributes.json`
- Evolution: `03_Comparative_Analysis/04_Weapon_System_Evolution.md`

### Georama / Town Building
- DC1: `01_Dark_Cloud_1/02_Georama_System.md` + `04_Reference_Sheets/DC1_Georama_Villager_Requests.json`
- DC2: `02_Dark_Cloud_2/02_Georama_Time_Travel.md` + `04_Reference_Sheets/DC2_Georama_Parts.json`
- Evolution: `03_Comparative_Analysis/05_Georama_Evolution.md`

### Core Loops & Design Philosophy
- `03_Comparative_Analysis/01_Systems_Evolution.md`
- `03_Comparative_Analysis/02_Design_Philosophy_Synthesis.md`
- `03_Comparative_Analysis/03_Core_Loop_Comparison.md`

### Character & Progression
- DC1: `01_Dark_Cloud_1/04_Character_System.md` + `06_Character_Progression.md`
- DC2: `02_Dark_Cloud_2/04_Dual_Protagonist_System.md` + `07_Monster_Transformation.md` + `11_Support_Characters.md`

### Side Systems (DC2)
- Invention/Photo: `02_Dark_Cloud_2/06_Invention_Photography_System.md` + `DC2_Invention_Recipes.json`
- Ridepod: `02_Dark_Cloud_2/05_Ridepod_Steve_System.md`
- Medals/Spheda/Fish: `02_Dark_Cloud_2/08_Medal_System.md` + `09_Spheda_Golf.md` + `10_Fishing_Finny_Frenzy.md`

### Lore & Narrative
- `05_Lore_Narrative/DC1_Story_Characters.md`
- `05_Lore_Narrative/DC2_Story_Characters.md`
- `05_Lore_Narrative/World_Building_Atlamillia_Lore.md`
- `05_Lore_Narrative/Timeline_Connections.md`

### Technical
- `06_Technical_Reference/PS2_Hardware_Constraints.md`
- `06_Technical_Reference/Procedural_Generation_Notes.md`
- `06_Technical_Reference/Level5_Engine_Evolution.md`
- `06_Technical_Reference/Cel_Shading_Rendering.md`

---

## Version & Maintenance

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-07-08 | Initial comprehensive reference from web research |

**Sources**: GameFAQs, IGN, GameSpot, RPGFan, Dark Cloud Wiki, Level-5 Interviews (Famitsu, Siliconera, Polygon), Strategy Guides, Community Wikis (AlmarsGuides, PSNProfiles)

**Note**: All mechanics verified against multiple sources. Japanese/Overseas version differences noted where documented.

---

*May your weapons never break, your thirst never run dry, and your villages flourish across all eras.*