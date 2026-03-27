# Master Prompt: Avian Dialogue Overhaul

I am executing a complete rebranding of the in-game dialogue. All text must be updated to reference birds, flying, feathers, or avian behaviors.

## CRITICAL SAFEGUARDS (DO NOT VIOLATE)

### 1. Edit Scope (Strict)
- Only modify text inside `_("...")` or `COMPOUND_STRING("...")`.
- Do not alter anything outside these string macros.

### 2. Preserve Control Codes
- Never change, remove, or add formatting/control codes such as:
  - `\n`, `\p`, `\l`, `$`, `\$`, `\v0`
- These are required for text flow and engine behavior.

### 3. Preserve Variables
- Do not modify or remove variables, including:
  - `{PLAYER}`, `{STR_VAR_1}`, `{RIVAL}`, etc.

### 4. Preserve Script Structure
- Do not rename or modify script labels (e.g., `EventScript_...`).
- Do not alter commands like `msgbox`.

### 5. Preserve Constants
- Do not change constants such as `ITEM_POTION` or similar identifiers.

### 6. Text-Only Changes
- Only rewrite the human-readable dialogue/content inside valid string macros.
- Do not alter logic, structure, or non-text elements.

---

### Avian Replacement Dictionary (Examples)

Use these suggestions as inspiration, but maintain natural sentence flow:

- **Trainer (General):** Bird Keeper, Aviator, Raptor Specialist.
- **Pokémon (Text):** Avimon.
- **Journey/Adventure:** Migration, Flight Path, Sky-bound quest.
- **Gym Badge:** Crest, Feather.
- **Poké Ball:** Nesting Sphere.
- **Run/Sprint:** Take flight, Soar.
- **See/Look:** Spy, Spot, Observe from above.
- **Battle (Verbs):** Clash, Swoop, Strike, Compete for territory, Territory Dispute.
- **Win/Lose (Verbs):** Prevail, Fledgling success / Grounded, Forced to roost.

---

### Task Instructions
Review the added files. Rewrite every human-readable sentence to adhere to the Avian theme, following the safeguards listed above. Ensure the sentences remain grammatically correct and coherent within their original context.