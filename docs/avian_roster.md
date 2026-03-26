# Avian Roster — Species Replacement Design Document

This is the living design document for the avian ROM hack.
It tracks which real bird replaces which Pokémon, the implementation
status of each, and the approved stat/learnset/sprite decisions.

> When adding a new species: fill in the Planning columns first,
> then move it to In Progress only when you open a Copilot Edits session for it.
> Move to Done only after `make -j4` passes and the species is testable in-game.

---

## Status Key

| Symbol | Meaning |
|---|---|
| 🔴 Planned | Design decided, not started |
| 🟡 In Progress | Copilot edits open, files being changed |
| 🟢 Done | Compiles, tested in-game |
| ⚪ Backlog | Under consideration, not yet designed |

---

## Active Roster

### Line 1 — Taillow / Swellow (Gen 3 — `gen_3_families.h`)

| Slot | Original | Real Bird | Scientific Name | Type | Status |
|---|---|---|---|---|---|
| SPECIES_TAILLOW | Taillow | House Sparrow | *Passer domesticus* | Normal/Flying | 🟡 In Progress |
| SPECIES_SWELLOW | Swellow | Barn Swallow | *Hirundo rustica* | Normal/Flying | 🟡 In Progress |

**Sprite placeholder:** Use `graphics/pokemon/taillow/` and `graphics/pokemon/swellow/` as recolour bases.
**Community sprite sources to check:** Team Aqua Asset Repo → search "sparrow", "swallow"

#### House Sparrow (SPECIES_TAILLOW)
```
HP:     45    Small body, not robust
Atk:    40    Weak beak, seed-cracker
Def:    30    No armour, light bird
SpAtk:  30    Not a vocal specialist
SpDef:  35    Alert, but fragile
Spd:    85    Fast, erratic flight
BST:    265
```
**Learnset draft:**
| Level | Move | Rationale |
|---|---|---|
| 1 | Peck | Basic beak attack |
| 1 | Growl | Territorial chirping |
| 9 | Quick Attack | Fast, darting movement |
| 13 | Wing Attack | Aerial strike |
| 19 | Echoed Voice | Repetitive house sparrow call |
| 25 | Facade | Tough despite small size |
| 31 | Roost | Perching/resting behaviour |
| 37 | Double-Edge | Desperate scrappy fighter |

**Egg moves:** Foresight, Feather Dance, Mirror Move
**TMs of note:** Aerial Ace, Return, Protect, Attract, Facade

**Pokédex entry:**
```
"A quarrelsome bird that thrives near human settlements.
It rolls in dry dust or sand to rid its feathers of parasites."
```
**Height:** 0.2m | **Weight:** 0.3 kg
**Catch rate:** keep original (200) | **Growth rate:** keep original (Erratic)

---

#### Barn Swallow (SPECIES_SWELLOW)
```
HP:     60    Lean but enduring migrant
Atk:    70    Precise aerial hunter
Def:    45    Light, not defensive
SpAtk:  50    Occasional song
SpDef:  45    Agile evasion
Spd:    120   One of Europe's fastest small birds
BST:    390
```
**Learnset draft:**
| Level | Move | Rationale |
|---|---|---|
| 1 | Peck | Basic attack |
| 1 | Quick Attack | Instantly fast |
| 17 | Wing Attack | Aerial sweep |
| 21 | Aerial Ace | Never misses — mirrors the swallow's precision |
| 27 | Agility | Migration speed, rapid acceleration |
| 33 | Double-Edge | Long-distance migrant toughness |
| 40 | Brave Bird | Peak aerial dive |
| 47 | Air Slash | Cutting through air at speed |

**Egg moves:** Pursuit, Endeavour, Refresh
**TMs of note:** Aerial Ace, Steel Wing, Protect, Hyper Beam

**Pokédex entry:**
```
"A streamlined bird that travels thousands of kilometres each year
between Europe and sub-Saharan Africa. It catches all its prey mid-flight."
```
**Height:** 0.2m | **Weight:** 0.2 kg
**Catch rate:** keep original (45) | **Growth rate:** keep original (Slow)

---

### Line 2 — Wingull / Pelipper (Gen 3 — `gen_3_families.h`)

| Slot | Original | Real Bird | Scientific Name | Type | Status |
|---|---|---|---|---|---|
| SPECIES_WINGULL | Wingull | Herring Gull | *Larus argentatus* | Water/Flying | 🔴 Planned |
| SPECIES_PELIPPER | Pelipper | Northern Gannet | *Morus bassanus* | Water/Flying | 🔴 Planned |

**Sprite placeholder:** `graphics/pokemon/wingull/` and `graphics/pokemon/pelipper/`

#### Herring Gull (SPECIES_WINGULL) — draft stats
```
HP: 50 | Atk: 45 | Def: 40 | SpAtk: 55 | SpDef: 40 | Spd: 75 | BST: 305
```
**Notes:** Opportunistic feeder, loud, aggressive around food. Lean into
Growl/Screech variants, Water-type moves, and scavenging flavour.

#### Northern Gannet (SPECIES_PELIPPER) — draft stats
```
HP: 85 | Atk: 80 | Def: 65 | SpAtk: 75 | SpDef: 60 | Spd: 60 | BST: 425
```
**Notes:** Iconic vertical plunge-diver. Surf, Dive, and Hydro Pump fit naturally.
High HP reflects the large robust seabird body.

---

### Line 3 — Murkrow / Honchkrow (Gen 2 — `gen_2_families.h`)

| Slot | Original | Real Bird | Scientific Name | Type | Status |
|---|---|---|---|---|---|
| SPECIES_MURKROW | Murkrow | Carrion Crow | *Corvus corone* | Dark/Flying | 🔴 Planned |
| SPECIES_HONCHKROW | Honchkrow | Common Raven | *Corvus corax* | Dark/Flying | 🔴 Planned |

**Sprite placeholder:** `graphics/pokemon/murkrow/` and `graphics/pokemon/honchkrow/`
**Notes:** Corvids are the smartest birds — lean heavily into Taunt, Torment,
Nasty Plot, Mimic. Ravens are larger, more dominant; higher BST and Sp.Atk.

#### Carrion Crow — draft stats
```
HP: 60 | Atk: 65 | Def: 42 | SpAtk: 75 | SpDef: 42 | Spd: 91 | BST: 375
```

#### Common Raven — draft stats
```
HP: 100 | Atk: 80 | Def: 60 | SpAtk: 105 | SpDef: 65 | Spd: 70 | BST: 480
```

---

### Line 4 — Natu / Xatu (Gen 2 — `gen_2_families.h`)

| Slot | Original | Real Bird | Scientific Name | Type | Status |
|---|---|---|---|---|---|
| SPECIES_NATU | Natu | Eurasian Wren | *Troglodytes troglodytes* | Normal/Flying | 🔴 Planned |
| SPECIES_XATU | Xatu | Barn Owl | *Tyto alba* | Psychic/Flying | 🔴 Planned |

**Notes:** Wren is tiny, loud, and surprisingly bold for its size. Barn Owl fits
the Psychic type naturally — silent flight, night vision, eerie presence.
The Natu → Xatu evolution arc becomes Wren → Barn Owl (metamorphic ecological shift).

#### Eurasian Wren — draft stats
```
HP: 40 | Atk: 35 | Def: 30 | SpAtk: 45 | SpDef: 40 | Spd: 65 | BST: 255
```

#### Barn Owl — draft stats
```
HP: 65 | Atk: 65 | Def: 50 | SpAtk: 85 | SpDef: 75 | Spd: 65 | BST: 405
```

---

### Line 5 — Pidgey / Pidgeotto / Pidgeot (Gen 1 — `gen_1_families.h`)

| Slot | Original | Real Bird | Scientific Name | Type | Status |
|---|---|---|---|---|---|
| SPECIES_PIDGEY | Pidgey | European Robin | *Erithacus rubecula* | Normal/Flying | 🔴 Planned |
| SPECIES_PIDGEOTTO | Pidgeotto | Song Thrush | *Turdus philomelos* | Normal/Flying | 🔴 Planned |
| SPECIES_PIDGEOT | Pidgeot | Common Buzzard | *Buteo buteo* | Flying/Normal | 🔴 Planned |

**Notes:** Three-stage line maps well to a size/power progression.
Robin (tiny woodland) → Song Thrush (medium, strong song) → Common Buzzard (large raptor).
The ecological leap from passerine to raptor is unusual but mirrors the original
Pidgey → Pidgeot power jump. Lean into this as flavour.
Check `form_species_tables.h` — Pidgeot has a Mega form entry to handle.

#### European Robin — draft stats
```
HP: 45 | Atk: 40 | Def: 35 | SpAtk: 45 | SpDef: 40 | Spd: 56 | BST: 261
```

#### Song Thrush — draft stats
```
HP: 63 | Atk: 60 | Def: 55 | SpAtk: 65 | SpDef: 50 | Spd: 71 | BST: 364
```

#### Common Buzzard — draft stats
```
HP: 83 | Atk: 100 | Def: 70 | SpAtk: 65 | SpDef: 70 | Spd: 80 | BST: 468
```

---

## Backlog (under consideration)

| Original | Candidate Bird | Notes |
|---|---|---|
| Doduo / Dodrio | Ostrich / Greater Rhea | Flightless angle is interesting |
| Farfetch'd | Eurasian Bittern | Already weird/rare bird energy |
| Delibird | White Stork | Migration + gift/delivery flavour |
| Skarmory | Grey Heron | Tall, angular, wading — already fits |
| Articuno | Snowy Owl | Legendary slot, iconic Arctic bird |
| Zapdos | White-tailed Eagle | Powerful, rare European raptor |
| Moltres | Common Crane | Striking, migratory, not actually fiery — needs rethink |

---

## Changelog

| Date | Change |
|---|---|
| 2026-03-26 | Roster created. Taillow line set to In Progress as first test. |
