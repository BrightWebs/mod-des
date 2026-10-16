# Primary implementation brief: Abilities interface

## Source page 1

JAYCEE: DI IMMORTALES

MASTER ABILITY IMPLEMENTATION BIBLE
 First-read instructions • exact Abilities-tab reconstruction brief • generative artwork briefs • complete 292-entry illustrated ability
 encyclopedia

 PRIORITY: The following Abilities-tab specification appears first by design. The complete ability encyclopedia follows without
 editing its existing pages. The screenshot is the visual reference, and this document is the written contract for recreating the
 approved look and interactions.

 SOURCE AND DELIVERY NOTE
 The previous 32-page Agent-Ready Ability Bible was listed in the project but its original PDF could not be retrieved for direct
 merging. This master instead preserves the available 51-page Complete Ability Encyclopedia and the full 3-page UI Revision
 addendum. Do not confuse their ability rosters or assume that either document proves code is implemented. If an older bible
 supplies additional canon mechanics, reconcile them rather than discarding them.

AGENT EXECUTION ORDER
 1. Read this front section, then the existing UI addendum and the complete catalog before changing code.

 2. Keep the already-approved menu navigation, tabs, colors, Equip Page, page count and behavior. Change only the Abilities tab
 components explicitly described here.

 3. Build canonical data records for names, ability IDs, patron/evolution/fusion grouping, description, available modes, level, mana
 cost, cooldown, range, area, cast time, and icon ID. Do not invent numeric values where the source has none; mark them for
 balancing or derive them from implemented mechanics.

 4. Generate ORIGINAL image assets from per-ability briefs, validate legibility at slot size, register files and make every GUI and
 hotbar view use the same asset ID. The existing catalog illustrations are concept references, not evidence of finished individual
 runtime textures.

 5. Implement interactions and test search, categories, accurate counts, selection, display, equipment persistence, Alt+slot mode
 cycling, and UI scales. Deliver sources and built artifact only after a working test pass.

SCREENSHOT RECONSTRUCTION — MEASURABLE LAYOUT
 Reference canvas is 1536 × 1024 pixels. Coordinates below are approximate reference anchors, NOT mandatory absolute pixels
 for all screen sizes; scale the design uniformly within the Minecraft GUI and use anchors and proportional constraints to avoid
 clipping. Match the screenshot when displayed at this aspect ratio.

  Area                  Approx. x range        Approx. y range       Behavior

  Top tabs             182–1344            94–198               Status / Abilities / Skills / Magic / Species / Quests; highlight Abilities in
                                                                                       violet

   Categories           32–337              213–923             Dark framed scrolling column; All Abilities first; replace other labels with
                                                                 approved canon groups

   Ability list            341–740             213–923             Search near y=280, row height ~54; icon/name/rank/level; purple
                                                                         selected highlight

   Details              744–1245            213–923            Header with small icon at upper left, name + level + tags; large art and
                                                                                    stat block

  Equip Page          1247–1505           213–923           UNMODIFIED; page selector, grid and hint remain operational

 VISUAL DESIGN, DOWN TO COMPONENT LEVEL


JAYCEE: DI IMMORTALES | FRONT-OF-BOOK IMPLEMENTATION CONTRACT                                                    1

## Source page 2

Canvas and framing
 Keep Minecraft world faintly visible behind the GUI. Use deep near-black midnight-blue translucent panels (#071427 to #111c32),
 fine blue-white strokes, faint inner glows, slim corner filigree and silver-violet diamond details. Separate columns by narrow
 luminous vertical dividers. Keep all text on dark surfaces bright enough to read.

 Top navigation
 Keep centered horizontal navigation tiles. The selected Abilities tab glows saturated violet with a bright thin outline and flame-like
  ability symbol; inactive tabs use icy-blue monochrome symbols. Preserve M and E side hints if already built. Do not rebuild tabs.

 Left filter column
 Header Ability Categories. First row All Abilities with 2x2 grid pictogram and violet selection. Use the actual canonical category
 labels supplied in the bible—not the screenshot generic examples. Each row includes a category-matched pictogram at left and
 live count aligned at far right. Row separators are subtle blue lines; selected row gets violet fill and a glowing rectangle. If a skill
 belongs to multiple filters, All Abilities still counts unique skills.

 Middle browse panel
 Header Abilities (Selected Filter), small search bar with magnifier and placeholder, live matching-results fraction at right. Vertical
  list is scrollable; each ability row shows 48-ish-square decorated original icon on left, name, tier capsule if relevant, and level at
 right. Selected row is outlined in purple and filled with soft gradient; switching selection updates details only—no accidental
 cast/equip.

 Details header
 At top of main details column put a distinct 70-ish-square icon and large white ability title. At the right place level text in warm gold
 and a thin golden underline. Beneath the title, rank/type badges in golden, red, violet or another ability-appropriate accent. All
 ranks must come from data.

 Preview and numerical stats
 Below the header, place a roughly 270x240 cinematic ability illustration at left. At right, use a framed narrow panel with five
 stacked rows: blue droplet Mana Cost, hourglass Cooldown, reticle Range, dashed-circle Area, purple spiral Cast Time. Align
 labels left and numeric values right. Update dynamically on selected mode. For passives show drain per second and N/A for
 genuinely inapplicable rows.

 Description and effects
 Under artwork, use a small violet ornamental icon followed by Description label in bright white. Display two-to-four clear text lines
 of what the selected skill really does, wrapping without overlap. Below that, a tiny starburst icon and Effects heading, then a
 compact bullet list describing concrete mechanics. Add mode, evolution, mastery and grant restrictions in an expandable
 subsection if content does not fit.

 Action zone
 Near bottom of details panel, use a gold-outlined button using the existing equip action semantics (in reference it reads Remove
 from Page because the sample ability is already equipped). The action state must reflect the real slot state. Do not add an
 independent alternative equip panel.

 Equip and persistence
 Do not change right panel design, four visible icon slots, page arrows, page indicator, diamond page progress controls, or
 Alt+wheel page switching. Equipping must immediately show the same icon as in the list and details header. Restore slots after
 relog, server sync and reopening UI.

 Accessibility and scaling
 At smaller GUI scales use scissoring/scroll views for middle/left columns, clipped long names with full hover tooltips, and flexible
 preview/stat sizing; avoid stretching artwork. Keep hover, focus, keyboard support and clear selected states.

REFERENCE SCREENSHOT


JAYCEE: DI IMMORTALES | FRONT-OF-BOOK IMPLEMENTATION CONTRACT                                                    2

## Source page 3

Use the reference image for proportions, ornaments and placement; authoritative text in this section determines which portions change.





JAYCEE: DI IMMORTALES | FRONT-OF-BOOK IMPLEMENTATION CONTRACT                                                    3
# Additional UI revision and reference

## Source page 39

JAYCEE: DI IMMORTALES

  Abilities Tab — Targeted UI Revision for Coding Agent
 Status: design/implementation instruction; this addendum does not claim that the mod UI is already changed. Apply alongside
 the existing Divine Ability Bible. The supplied Reality Severance interface image is a layout reference, not an exhaustive list of
  abilities.

 1 | Scope: keep the rest of the GUI unchanged
 Modify only the Abilities tab, specifically its left category/filter column, middle ability list, and selected-ability details panel.
 Preserve the existing overall visual theme and the existing right-hand Equip Page including its page navigation, slots, and
  existing interaction model. Do not recreate or redesign that page.

 2 | Left column: replace generic groupings
 Remove the provisional filters Offensive, Defensive, Support, Mobility, Control, Transformation, Reality Manipulation,
 Creation, Destruction, Passive as the primary category scheme. Retain All Abilities as the first category. Populate the
 remaining category names from the actual approved ability taxonomy and patron/evolution/fusion groupings defined in
 the ability bible; use the canon labels, not guessed or generic substitutes. Where the source design is ambiguous, mark the
 mapping for approval rather than silently inventing categories.

 Each category shows a live count of abilities belonging to it, respecting unlock visibility rules. The All Abilities count is the
 unique total, not a sum that double-counts an ability assigned to multiple groupings. Clicking a category filters the middle list;
  its header and result count update to match. Search works within the active filter, and counts refresh when abilities are
 unlocked, blessed, or removed.

 3 | Middle column: ability selection
 Show each ability with its original distinct icon, canonical name, tier/rank, and mastery level where applicable. Clicking the
 entry highlights it and populates the adjacent selected-ability panel without equipping or casting it. Preserve
 scrolling/searching and support locked abilities according to existing progression rules. No placeholder icons in the shipped
 mod.

 4 | Selected ability details panel
 Follow the reference layout: large ability name with large original icon, relevant tier/element badges and level; a visual
 preview/artwork area; a compact, clearly aligned stat block containing Mana Cost, Cooldown, Range, Area, Cast Time; then
 a Description explaining behavior and an Effects section showing concrete mechanics. Include unlocked modes,
 mastery/evolution/fusion conditions, and requirements without obscuring the core five stats. Display contextual values per
 selected mode and level rather than invented constants. For passive/toggle abilities label sustained mana drain, activation
 costs, and cooldowns appropriately; show N/A only where mechanics truly do not apply.

 5 | Equipping and icons
 Use the existing Equip Page. Assigning a selected unlocked ability to a slot immediately displays the exact same icon in that
  slot and on the in-game equipped-ability HUD. Persist the slot assignment and icon through saves, reloads, GUI reopenings,
 and mode changes. If a selected slot is occupied, obey the existing replacement/confirmation behavior rather than adding a
 new panel. Icon assets must be visibly distinct and legible at HUD scale, with consistent rendering and transparent
 backgrounds.

 6 | Interaction contract
  Click ability entry = select and inspect, not activate. Equip action = assign to chosen existing slot. Normal equipped hotkey =
  activate current mode. Hold Alt + press the corresponding ability hotkey = cycle through unlocked modes without
 activation or mana use; update mode indicator, ability stats/description where applicable, and slot visual state. Evolved and
 fused abilities retain access to their earlier forms and modes as specified in the design bible.


Jaycee: Di Immortales | Abilities UI Revision                                                                                  1

## Source page 40

7 | Acceptance checks
 Confirm the right Equip Page remains functionally unchanged; each list entry has a unique relevant icon; selection opens
 accurate descriptions and all five combat stat fields; counts and search are correct; equipping mirrors icon onto the chosen
  slot; Alt+slot cycles modes without casting; no abilities or levels are lost; GUI does not clip at supported UI scales. Use the
 complete approved ability data, not just the ten example entries visible in the reference.





Jaycee: Di Immortales | Abilities UI Revision                                                                                  2

## Source page 41

Visual layout reference

 Use this screenshot to guide proportions, icon placement, stat display, descriptive text, and the existing equip-slot
 arrangement. Only the categories and the defined portions of the Abilities tab are to be altered.





 Art direction: The previous supplied icon examples are stylistic references, not mandatory assets. Each named ability
 requires an original image whose subject communicates its effect (for example, speed: a sprinting figure with trailing motion
  streaks). Store per-ability icon descriptions, final asset IDs, and fallback handling in the ability registry so list, details panel,
 and equip slots all resolve to one canonical icon.





Jaycee: Di Immortales | Abilities UI Revision                                                                                  3
