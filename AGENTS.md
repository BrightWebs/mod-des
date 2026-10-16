# Instructions for coding agents: Jaycee: Di Immortales

## Required reading order
1. `docs/GUI_DESIGN.md` — **highest-priority targeted Abilities-tab requirements**.
2. `docs/IMPLEMENTATION_CHECKLIST.md`.
3. `docs/ICON_DESIGN_GUIDE.md` and `data/icon_descriptions.json`.
4. `docs/MASTER_DESIGN_BIBLE.md` and `data/abilities.json`.
5. Inspect `references/` images and the **existing mod source and approved UI** before making changes.

## Non-negotiables
- Keep the existing Equip Page and other approved screens intact; only change the specified Abilities-tab regions.
- Replace generic categories with the genuine ability families; retain All Abilities with live unique counts.
- Show each distinct icon in the list, in the selected ability details, and in the equipped slot; one canonical texture ID per ability.
- Selection details: description, mana, cooldown, range, area, cast time, level, modes and applicable requirements. If numeric values are not defined, mark them unresolved rather than make up values.
- Alt + assigned slot key cycles available modes without casting or spending mana; evolved/fused skills retain prior forms.
- Mana is spent on skill usage. Essence concerns blessings and followers. EP represents permanent power.
- Toggleable intrinsic skills, patron grants, speed output percentage, flight variants, Jaycee-exclusive powers and restrictions must be reconciled with the full canon before implementation.
- Jaycee is spelled J-A-Y-C-E-E. Do not rename him JC in player-facing text.
- Avoid placeholder effects; implement and test real client/server behavior, including multiplayer permissions.
- Do not overwrite working source or approved UI while loading this documentation.

## Source limitations and conflicts
This package faithfully extracts the available **92-page master PDF**, including its original **292-entry concept encyclopedia** and 292 icon briefs. Some earlier agent-ready design material was not incorporated into that source. The encyclopedia may NOT match all earlier 220-ability patron and fusion decisions. Treat discrepancies as unresolved and seek reconciliation; do not silently replace earlier approved concepts. `data/ability_modes.json` is deliberately empty because an exact canonical list and cost table is not provided in the current master source. `null` means unspecified, not zero or free.

## Implementation order
Read and inventory existing code -> map canon and resolve contradictions -> implement data registry and network protocol -> connect GUI without redesigning Equip Page -> generate original icons from per-ability prompts -> implement individual server-authoritative skills and modes -> verify build and game tests -> document changes and remaining issues.
