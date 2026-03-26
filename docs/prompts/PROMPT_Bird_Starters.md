# Copilot Edits Prompt — European Bird Starters

## Instructions
1. Create a new branch: `git checkout -b edit-bird-starters`
2. Open **Copilot Edits** (Ctrl+Shift+I)
3. Add these files to the working set:
   - `src/data/pokemon/species_info/gen_3_families.h`
   - `src/data/pokemon/level_up_learnsets/gen_3.h`
   - `include/constants/pokemon.h`

---

## The Prompt
I am replacing the Hoenn Starters with European bird species. Please apply the following changes to the species data.

**STRICT RULES:**
- `.speciesName` MAX 10 characters.
- `.categoryName` MAX 11 characters.
- DO NOT change constants like `SPECIES_TREECKO`.

### 1. SPECIES_TREECKO → Eurasian Bullfinch
- .speciesName = _("Bullfinch")
- .categoryName = _("Finch")
- .bodyColor = BODY_COLOR_RED
- .description = COMPOUND_STRING(
    "A bulky finch with a bright pinkish\n"
    "breast. It is often seen in pairs\n"
    "feeding on the buds of fruit trees\n"
    "in European orchards.")

### 2. SPECIES_TORCHIC → European Robin
- .speciesName = _("Robin")
- .categoryName = _("Redbreast")
- .bodyColor = BODY_COLOR_RED
- .description = COMPOUND_STRING(
    "Famous for its orange-red breast,\n"
    "this bird is a frequent visitor to\n"
    "gardens. It is highly territorial\n"
    "and sings year-round.")

### 3. SPECIES_MUDKIP → Common Kingfisher
- .speciesName = _("Kingfisher")
- .categoryName = _("Diver")
- .bodyColor = BODY_COLOR_BLUE
- .description = COMPOUND_STRING(
    "A blue flash over the water. It\n"
    "perches motionless before diving\n"
    "at high speeds to catch small\n"
    "fish in fresh water.")

---

## Implementation Task: The Starter Menu
In `include/constants/pokemon.h`, ensure that the constants for the starters still point to these species slots so the Professor Bird intro sequence functions correctly.