# Master Prompt: Avian Dialogue Overhaul

I am executing a complete rebranding of the in-game dialogue. All text must be updated to reference birds, flying, feathers, or avian behaviors with a specific focus on **Ornithological Education**. The goal is to teach the player real scientific facts about birds through NPC interactions and trainer battles.

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

- **Trainer (General):** Bird Keeper, Aviator, Ornithologist, Raptor Specialist.
- **Pokémon (Text):** Avimon.
- **Journey/Adventure:** Migration, Flight Path, Sky-bound quest.
- **Gym Badge:** Crest, Feather.
- **Poké Ball:** Nesting Sphere.
- **Run/Sprint:** Take flight, Soar.
- **See/Look:** Spy, Spot, Observe from above.
- **Battle (Verbs):** Clash, Swoop, Strike, Compete for territory, Territory Dispute, Field Study, Territory Dispute.
- **Win/Lose (Verbs):** Prevail, Fledgling success / Grounded, Forced to roost.

---

## 1. THEMATIC & EDUCATIONAL RULES
- **Educational Integration:** When a trainer or NPC speaks, try to weave in a real scientific fact about birds that fits the context.
  - *Example (Youngster):* Instead of "I like shorts," use "Did you know some birds like the Alpine Swift can fly for six months without landing?"
  - *Example (Fisherman):* Instead of "I'm a great fisherman," use "I study the Kingfisher; they have specialized eyes to see prey through the water's glare."
- **Tone:** Informative, curious, and respectful of nature.

## 2. SCIENTIFIC FACT REPLACEMENT GUIDE
- **Speed/Agility:** Mention the Peregrine Falcon’s dive speed (over 320 km/h).
- **Migration:** Mention the Arctic Tern’s incredible journey from pole to pole.
- **Intelligence:** Mention Corvids (crows/ravens) and their ability to use tools.
- **Anatomy:** Mention hollow bones for flight or the unique structure of owl feathers for silent flight.

---

### Task Instructions
Review the added files. Rewrite every human-readable sentence to adhere to the Avian theme, following the safeguards listed above. Ensure the sentences remain grammatically correct and coherent within their original context. Review the `.string` entries in the added files. Rewrite them to be educational and avian-themed. Ensure the dialogue still makes sense for the game's progression while acting as a "mini-lesson" in ornithology.