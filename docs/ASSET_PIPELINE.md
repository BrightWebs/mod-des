# Asset output requirements

Generate one original transparent 1024x1024 PNG image per ability, matching the full individual brief from `data/icon_descriptions.json`; export 256px (details/menu), 64px (HUD), and inspect at 32px. Keep coherent subject/action, palette, composition, border, transparency and filename. Do not place text in icons. These are prompts; final PNG icons are **not included** in this pack.

Map `ability_id -> icon_filename` in the code-backed ability registry. Keep texture in sync among ability list, detail panel and equip slot. In Minecraft Java, convert to the appropriate resources assets namespace/path for the actual mod loader/version before integrating.
