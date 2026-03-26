# Copilot Edits Prompt — Taillow Line (First Implementation)

## Instructions for use
1. Open **Copilot Edits** in VS Code (Ctrl+Shift+I)
2. Add these files to the working set:
   - `src/data/pokemon/species_info/gen_3_families.h`
   - `src/data/pokemon/level_up_learnsets/learnsets.h`
   - `src/data/pokemon/teachable_learnsets.h`
   - `src/data/pokemon/egg_moves.h`
3. Paste the prompt below into the Copilot Edits input

---

## Notes on the confirmed struct layout
*(read before using the prompt — these are facts extracted from the real file)*

- Field names use `.baseHP`, `.baseAttack`, `.baseDefense`, `.baseSpeed`,
  `.baseSpAttack`, `.baseSpDefense` — no underscores in the stat words
- Species name syntax: `.speciesName = _("Taillow")`
- Category syntax: `.categoryName = _("Tiny Swallow")`
- Description syntax: `.description = COMPOUND_STRING("line one.\n" "line two.\n" "line three.")`
  — each line is a separate quoted string, max ~36 chars per line, 3–4 lines
- **Height units: 0.1m** — so Taillow `.height = 3` means 0.3m
- **Weight units: 0.1kg** — so Taillow `.weight = 23` means 2.3kg
- `.bodyColor` is a named constant e.g. `BODY_COLOR_BLUE` — update to match bird
- **Do NOT touch:** `.cryId`, `.natDexNum`, `.pokemonScale`, `.pokemonOffset`,
  `.trainerScale`, `.trainerOffset`, `.frontPic`, `.frontPicSize`,
  `.frontPicYOffset`, `.frontAnimFrames`, `.frontAnimId`, `.backPic`,
  `.backPicSize`, `.backPicYOffset`, `.backAnimId`, `.palette`, `.shinyPalette`,
  `.iconSprite`, `.iconPalIndex`, `.pokemonJumpType`, `SHADOW(...)`,
  `FOOTPRINT(...)`, `OVERWORLD(...)`, `.isSkyBattleBanned`, `.evolutions`
- **Swellow has NO `.eggMoveLearnset` field** — do not add one

---

## The Prompt

```
I am replacing the Taillow and Swellow species entries with real European
bird species as part of an avian-themed ROM hack. Consult
.github/copilot-instructions.md for all structural rules before making
any changes.

I have already confirmed the exact struct layout from the source file.
Use the field names and syntax exactly as they appear in the existing
Taillow and Swellow blocks — do not invent or rename any fields.

Apply the following changes:

---

SPECIES_TAILLOW → House Sparrow (Passer domesticus)

In gen_3_families.h, change ONLY these fields in the SPECIES_TAILLOW block:

  .baseHP        = 45,
  .baseAttack    = 40,
  .baseDefense   = 30,
  .baseSpeed     = 85,
  .baseSpAttack  = 30,
  .baseSpDefense = 35,
  .bodyColor = BODY_COLOR_BROWN,
  .speciesName = _("House Sparrow"),
  .categoryName = _("Passerine"),
  .height = 2,      // 0.16m real size, rounded to nearest unit
  .weight = 3,      // ~30g real weight
  .description = COMPOUND_STRING(
      "A quarrelsome bird common near human\n"
      "settlements across Europe. It rolls\n"
      "in dry dust or sand to rid its\n"
      "feathers of parasites."),

Leave every other field in the SPECIES_TAILLOW block completely unchanged.

In learnsets.h — find sTaillowLevelUpLearnset and replace its contents:
  LEVEL_UP_MOVE( 1, MOVE_PECK),
  LEVEL_UP_MOVE( 1, MOVE_GROWL),
  LEVEL_UP_MOVE( 9, MOVE_QUICK_ATTACK),
  LEVEL_UP_MOVE(13, MOVE_WING_ATTACK),
  LEVEL_UP_MOVE(19, MOVE_ECHOED_VOICE),
  LEVEL_UP_MOVE(25, MOVE_FACADE),
  LEVEL_UP_MOVE(31, MOVE_ROOST),
  LEVEL_UP_MOVE(37, MOVE_DOUBLE_EDGE),
  LEVEL_UP_END

In teachable_learnsets.h — find sTaillowTeachableLearnset:
  - Add MOVE_ECHOED_VOICE if not already present
  - Remove MOVE_STEEL_WING if present
  - Leave all other entries unchanged

In egg_moves.h — find sTaillowEggMoveLearnset and replace its contents:
  MOVE_FORESIGHT,
  MOVE_FEATHER_DANCE,
  MOVE_MIRROR_MOVE,

---

SPECIES_SWELLOW → Barn Swallow (Hirundo rustica)

In gen_3_families.h, change ONLY these fields in the SPECIES_SWELLOW block:

  .baseHP        = 60,
  .baseAttack    = 70,
  .baseDefense   = 45,
  .baseSpeed     = 120,
  .baseSpAttack  = 50,    // use the simple value, remove the P_UPDATED_STATS conditional
  .baseSpDefense = 45,
  .bodyColor = BODY_COLOR_BLUE,
  .speciesName = _("Barn Swallow"),
  .categoryName = _("Swallow"),
  .height = 2,      // 0.19m real size
  .weight = 2,      // ~19g real weight
  .description = COMPOUND_STRING(
      "A streamlined bird that migrates\n"
      "thousands of kilometres each year.\n"
      "It catches every insect it eats\n"
      "without ever landing."),

Leave every other field in the SPECIES_SWELLOW block completely unchanged.
Do NOT add an .eggMoveLearnset field — the original Swellow has none.

In learnsets.h — find sSwellowLevelUpLearnset and replace its contents:
  LEVEL_UP_MOVE( 1, MOVE_PECK),
  LEVEL_UP_MOVE( 1, MOVE_QUICK_ATTACK),
  LEVEL_UP_MOVE(17, MOVE_WING_ATTACK),
  LEVEL_UP_MOVE(21, MOVE_AERIAL_ACE),
  LEVEL_UP_MOVE(27, MOVE_AGILITY),
  LEVEL_UP_MOVE(33, MOVE_DOUBLE_EDGE),
  LEVEL_UP_MOVE(40, MOVE_BRAVE_BIRD),
  LEVEL_UP_MOVE(47, MOVE_AIR_SLASH),
  LEVEL_UP_END

In teachable_learnsets.h — find sSwellowTeachableLearnset:
  - Leave all entries unchanged

---

Hard rules:
- Do NOT rename or change SPECIES_TAILLOW or SPECIES_SWELLOW constants
- Do NOT change .evolutions, .cryId, .natDexNum, or any sprite/graphic fields
- Do NOT touch pokemonScale, pokemonOffset, trainerScale, trainerOffset
- Do NOT touch SHADOW(), FOOTPRINT(), or OVERWORLD() macros
- If a move constant name is uncertain (e.g. MOVE_ECHOED_VOICE vs
  MOVE_ECHOED_VOICE), check an existing learnset in the same file
  for the correct constant format before writing it
- After completing all edits, output a summary listing:
  1. Every field changed per species
  2. Any move constant names you were uncertain about
  3. Any fields you left a // TODO on and why
```
