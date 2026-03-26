# Copilot Edits Prompt — Professor Name Change

## Instructions for use
1. Open **Copilot Edits** in VS Code (Ctrl+Shift+I)
2. Add these files to the working set:
   - `include/constants/global.h`
   - `src/data/text/birch_speech.h`
   - `src/data/text/trainer_class_names.h`
   - `data/maps/LittlerootTown_ProfessorBirchsLab/scripts.inc`
3. Paste the prompt below into the Copilot Edits input

---

## The Prompt

I am rebranding Prof. Birch to "Prof. Bird" to align with the avian theme of this ROM hack. Please apply the following string replacements carefully to ensure the name is updated in the intro speech, the lab scripts, and general dialogue.

Apply the following changes:

1. **In `src/data/text/birch_speech.h`**:
   - Find the string `gText_Birch_Welcome` or any introductory text.
   - Replace "BIRCH" or "Prof. Birch" with "Prof. Bird" while maintaining the existing capitalization and `\n` line breaks.

2. **In `src/data/text/trainer_class_names.h`**:
   - If there is a trainer class or specific name string for `BIRCH`, update it to `BIRD`.

3. **In `data/maps/LittlerootTown_ProfessorBirchsLab/scripts.inc`**:
   - Search for any display text (usually starting with `gText_`) that specifically mentions "Birch".
   - Update those strings to say "Bird". 
   - *Note: Do not change the internal script labels (e.g., `LittlerootTown_ProfessorBirchsLab_EventScript_Birch`), only the text that appears in quotes for the player to read.*

4. **Global Search and Replace (Strings only)**:
   - Scan the added files for the specific pattern `_("BIRCH")` and `_("Birch")`.
   - Replace with `_("BIRD")` and `_("Bird")` respectively.

**Hard Rules:**
- DO NOT change constant definitions like `FACILITY_CLASS_BIRCH` if they are used for logic/indexing, unless you also update every reference in the codebase. To be safe, focus ONLY on the text inside `_(" ")` or `COMPOUND_STRING(" ")`.
- Maintain the exact character length where possible or ensure the new string does not exceed the original line's visual width in the text box.
- Output a summary of which files were modified.