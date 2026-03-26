# Copilot Instructions — Avian Pokémon ROM Hack
### Based on `pokeemerald-expansion` (RHH, v1.15.0)

---

## Project Intent

This project is an **avian-themed ROM hack** built on the `pokeemerald-expansion`
decompilation. Real European bird species replace bird-like Pokémon using their
**existing species slots** — no new species IDs are created. The Pokémon battle
system is kept intact; only species identity, stats, moves, and sprites change.

**Design rules (always follow these):**
- Reuse existing species slots — do NOT add new `SPECIES_` constants
- Base stats must reflect real bird biology (see stat philosophy below)
- Learnsets use existing Gen 3 moves chosen to reflect real ecology
- Types: always Flying + one secondary type reflecting the bird's ecology
- Keep catch rate, EV yield, gender ratio, egg groups unless clearly wrong
- When uncertain, flag it — never silently guess at struct fields

---

## Confirmed Repo Structure (expansion layout)

> ⚠️ This repo does NOT use one-file-per-species for base stats.
> It uses centralised family files. Always edit those, not individual files.

### 1. Species Data (stats, typing, abilities, name, Pokédex)
```
src/data/pokemon/species_info/
    gen_1_families.h    ← Pidgey, Pidgeot lines
    gen_2_families.h    ← Murkrow, Honchkrow, Natu, Xatu lines
    gen_3_families.h    ← Taillow, Swellow, Wingull, Pelipper lines
```
Each family block controls: base stats, typing, abilities, growth rate,
catch rate, species name string, category string, Pokédex text,
height, weight, evolution method, and sprite symbol pointers.

### 2. Level-Up Learnsets
```
src/data/pokemon/level_up_learnsets/
    learnsets.h         ← Generation tables; active set selected in:
src/pokemon.c           ← Line ~958–977 via P_LVL_UP_LEARNSETS flag
```
> Do NOT create per-species learnset files. Edit the generation table
> entries directly and verify the active flag in `pokemon.c`.

### 3. Teachable & Egg Moves
```
src/data/pokemon/teachable_learnsets.h   ← TM/HM/tutor move compatibility
src/data/pokemon/egg_moves.h             ← Egg move pools
```
These are separate from level-up data and must be updated for
ecologically accurate move availability.

### 4. Sprite Assets
```
graphics/pokemon/[species_name]/
    front.png           ← 64×64px, indexed PNG, max 16 colors
    back.png            ← 64×64px, indexed PNG, max 16 colors
    icon.png            ← 32×64px (two 32×32 frames), indexed PNG
    normal.pal          ← Palette file
    shiny.pal           ← Shiny palette (required even if identical)
    footprint.png       ← Small footprint sprite
    anim_front.png      ← Optional: idle animation frame
```
Sprite symbols are wired into:
```
include/graphics.h      ← Read-only; verify symbol names match
src/graphics.c          ← Line ~2096–2105 for icon palette slot behavior
```

### 5. Forms & Evolution Consistency
```
src/data/pokemon/form_species_tables.h   ← Check for Mega/form entries
```
> When replacing an evolutionary line (e.g. Pidgey → Robin), replace
> ALL members of the line for biological coherence:
> Pidgey → Pidgeotto → Pidgeot must all become the same species line.

---

## Species Roster

The active species roster lives in **`docs/avian_roster.md`**.
Always consult that file for the current replacement targets, their
status, and approved stat/learnset drafts before making any edits.
Do not hardcode species decisions here.

---

## Stat Design Philosophy

Map real bird biology to Pokémon stats using these guidelines:

| Trait | Stat |
|---|---|
| Body size (large = more HP) | HP |
| Strike force / predatory | Attack |
| Dense plumage / armoured | Defense |
| Intelligence / complex song | Sp. Atk |
| Wariness / threat detection | Sp. Def |
| Flight speed / agility | Speed |

**Reference tiers:**

| Guild | Speed | Attack | Sp.Atk | HP |
|---|---|---|---|---|
| Raptors (buzzard, falcon) | 70–90 | 90–110 | 50–65 | 65–80 |
| Seabirds (gannet, gull) | 55–70 | 70–85 | 60–75 | 75–95 |
| Corvids (crow, raven) | 85–95 | 65–75 | 80–95 | 60–75 |
| Owls (barn owl) | 50–65 | 65–80 | 70–85 | 65–80 |
| Passerines (sparrow, robin) | 60–85 | 35–55 | 35–55 | 40–55 |
| Aerial hunters (swallow) | 110–125 | 65–75 | 45–55 | 55–65 |

---

## Learnset Design Rules

When designing level-up learnsets, follow these ecological mappings:

| Bird type | Preferred move categories |
|---|---|
| Raptors | Aerial Ace, Slash, Agility, Scary Face, Brave Bird |
| Seabirds | Surf (thematic), Mist, Stockpile, Spit Up, Roost |
| Corvids | Torment, Taunt, Faint Attack, Night Shade, Nasty Plot, Mimic |
| Owls | Hypnosis, Confusion, Future Sight, Night Shade, Reflect |
| Passerines | Growl, Sing, Echoed Voice, Quick Attack, Facade, Roost |
| Swallows | Quick Attack, Agility, Double-Edge, Arial Ace, Endure |

**Always use moves that already exist in the Gen 3 move table.**
Do not create new moves.

---

## Pokédex Entry Style Guide

Write Pokédex entries in the style of Gen 3 (short, two sentences max,
flavour-first). Reference one real biological fact per entry.

**Template:**
```
"[Striking observable behaviour or appearance]. [One ecological or
biological fact grounded in reality, written as in-world flavour.]"
```

**Example:**
```
"A small, quarrelsome bird found near human settlements.
It bathes in dust to rid itself of parasites."
```

---

## Sprite Pipeline Requirements

Source PNGs must meet these specs before dropping into `graphics/pokemon/`:

- **Format:** Indexed PNG (not RGBA, not greyscale)
- **Color depth:** Max 16 colors including the transparency color
- **Front/back size:** Exactly 64×64 pixels
- **Icon size:** Exactly 32×64 pixels (two 32×32 animation frames stacked)
- **Transparency:** Color index 0 must be the background/transparent color
- **Tool:** Use **Aseprite** or **GIMP** (indexed mode) to prepare sprites

**Community sprite sources (check these first):**
- [Team Aqua's Asset Repo](https://github.com/Pawkkie/Team-Aquas-Asset-Repo)
- RHH Discord `#resources` and `#custom-sprites` channels
- PokéCommunity "Fakemon Sprite" showcase threads

**Placeholder fallback sprites** — for each target bird, the closest
existing sprite to recolour is listed in `docs/avian_roster.md`
under the Sprite column. Use the original Pokémon's sprite folder
as a recolour base until a proper community sprite is sourced.

---

## Complete Edit Checklist (per species replacement)

Use this checklist for every bird added. Check off each item:

**Data files:**
- [ ] Species block in the correct `gen_X_families.h` — name, stats, types, abilities
- [ ] Pokédex entry text updated in same block
- [ ] Height and weight updated to real bird values
- [ ] Level-up learnset entry in `learnsets.h`
- [ ] TM/tutor compatibility in `teachable_learnsets.h`
- [ ] Egg moves updated in `egg_moves.h`
- [ ] Evolutionary line is fully replaced (all members, not just one)
- [ ] `form_species_tables.h` checked for any Mega/form references

**Sprite files:**
- [ ] `front.png` — 64×64, indexed, 16 colors
- [ ] `back.png` — 64×64, indexed, 16 colors
- [ ] `icon.png` — 32×64, indexed, 16 colors
- [ ] `normal.pal` present
- [ ] `shiny.pal` present
- [ ] `footprint.png` present

**Verification:**
- [ ] `make -j4` compiles without errors
- [ ] Species appears correctly in battle and summary screen
- [ ] Wild encounter on at least one route updated to test in-game

---

## Workflow & Safety Rules

- **Always commit before starting a new edit session** so you can roll back
- **Edit one evolutionary line at a time**, compile, then move to the next
- **Never guess at struct field names** — read the existing entry for that
  family first to confirm the exact field layout before editing
- **Do not rename `SPECIES_` constants** — the slot reuse strategy depends
  on keeping original IDs intact throughout the codebase
- When a field's correct value is ambiguous, **leave a `// TODO:` comment**
  rather than inserting a placeholder value silently
