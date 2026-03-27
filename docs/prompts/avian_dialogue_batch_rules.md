# Avian Dialogue Batch Rules

## Edit Boundary
- Edit only quoted text inside `.string "..."`, `_ ("...")` style macros (when present as `_ ( )` without space in source), and `COMPOUND_STRING("...")`.
- Do not edit labels, commands, constants, directives, or script structure.

## Hard Preservation
- Preserve all control flow tokens exactly: `\n`, `\p`, `\l`, `$`, and any explicit pause/wait tokens.
- Preserve all placeholders exactly and in order: `{PLAYER}`, `{STR_VAR_1}`, `{STR_VAR_2}`, `{STR_VAR_3}`, `{KUN}`, and similar.
- Leave Japanese strings unchanged.

## Style Targets
- Keep dialogue natural and concise for game windows.
- Add avian/ornithology framing with context-appropriate educational facts.
- Avoid repetition of the same fact across adjacent strings.
- Keep progression fit: early game = simpler facts; late game = deeper facts.

## Batch QA
1. Verify only string payloads changed.
2. Verify placeholder parity file-by-file.
3. Verify control-code parity file-by-file.
4. Build check after each completed batch cluster.
