# Supported engines and formats

**[← Back to the README](../README.md)** · **[Engine hub on runetranslate.com](https://runetranslate.com/engines)** · **[Download](https://runetranslate.com/download)**

RuneTranslate supports **17 engines and formats**, every one of them unlocked on the free tier. The two RPG Maker generations count as one entry there but get a section each below, so there are eighteen sections on this page. It is the long version of the table in the README: what each adapter detects, what it pulls out, what the export actually looks like, and where the edges are.

Three things are true of every engine below:

- **Your original game is never modified.** Export writes to an output folder you choose.
- **Every line is editable** before and after translation, and every line can be reset to the source text it was extracted from.
- **What you get is a build, not a session.** No overlay, no injected process, nothing running alongside the game.

**Legend** — *Full*: handled end to end. *Best-effort*: games in that family vary enough that some need a hand, and the app says so instead of failing quietly. ✅ *Played*: a real game was translated, exported, launched and played with translated text on screen, on a recorded app version.

---

## Contents

- [RPG Maker MV / MZ](#rpg-maker-mv--mz)
- [RPG Maker XP / VX / VX Ace](#rpg-maker-xp--vx--vx-ace)
- [Ren'Py](#renpy)
- [Kirikiri / KAG](#kirikiri--kag)
- [Wolf RPG Editor](#wolf-rpg-editor)
- [TyranoBuilder / TyranoScript](#tyranobuilder--tyranoscript)
- [Electron visual novels](#electron-visual-novels)
- [Unity](#unity)
- [Unreal Engine 4 / 5](#unreal-engine-4--5)
- [Godot 3.x / 4.x](#godot-3x--4x)
- [RPG Developer Bakin](#rpg-developer-bakin)
- [SRPG Studio](#srpg-studio)
- [NScripter / ONScripter](#nscripter--onscripter)
- [Artemis (Mikage)](#artemis-mikage)
- [YU-RIS](#yu-ris)
- [AliceSoft System 3.x / 4](#alicesoft-system-3x--4)
- [LiveMaker / LiveNovel](#livemaker--livenovel)
- [Gettext `.po` / `.mo`](#gettext-po--mo)
- [My engine is not here](#my-engine-is-not-here)

---

## RPG Maker MV / MZ

**Status: Full · ✅ Played** — [engine page](https://runetranslate.com/engines/rpg-maker) · [walkthrough](https://runetranslate.com/blog/how-to-translate-rpg-maker-games) · [MV vs MZ](https://runetranslate.com/blog/rpg-maker-mv-vs-mz-translation)

The most common engine in Japanese indie games, and the one RuneTranslate knows best.

**Detected by** `www/data/` (MV) or `data/` (MZ), plus the packed and protected variants below.

**What comes out:** event dialogue and choices, the database (items, weapons, armour, skills, states, enemies, classes, actors), `System.json` terms and messages, map names, and translatable strings inside plugin parameters. Dialogue is re-wrapped to the message window's width on export, so a longer English line does not run off the box.

**Awkward packaging, handled:**

- **Enigma Virtual Box** builds, where `data/` lives inside the `.exe` and there is no folder to open. RuneTranslate unpacks the whole virtual filesystem and exports a complete, runnable, *unpacked* copy of the game with the translated data in it.
- **Natively protected MZ**, where the data JSON is encrypted by a wrapper.
- **Plugin-held scripts** — some games keep their entire character dialogue in a plugin's own scenario format outside `data/*.json`. Those are read too.

**Export:** a full translated copy of the game folder. Double-click and play.

**Also for RPG Maker:** the [save editor](https://runetranslate.com/save-editor) opens `.rpgsave` and `.rmmzsave`, and [Cheat Mode](https://runetranslate.com/cheat-mode) injects an in-game cheat menu.

---

## RPG Maker XP / VX / VX Ace

**Status: Full** — [engine page](https://runetranslate.com/engines/rpg-maker-xp-vx-ace)

The Ruby generation — a genuinely different runtime from MV/MZ (RGSS and Ruby Marshal data instead of JavaScript and JSON), so it gets its own adapter.

**Detected by** a `Data/` folder of `.rxdata` / `.rvdata` / `.rvdata2`, or an encrypted `Game.rgssad` / `.rgss2a` / `.rgss3a` archive, which is decrypted automatically.

**What comes out:** event dialogue and choices, the database, and `System` terms.

**Export:** a full runnable copy of the game.

**Worth knowing:** XP and VX render text as Shift-JIS, so they suit English and other Latin-script targets best; VX Ace is UTF-8 and has no such limit. Strings written directly into the Ruby `Scripts` section are out of scope.

---

## Ren'Py

**Status: Full** — [engine page](https://runetranslate.com/engines/renpy) · [walkthrough](https://runetranslate.com/blog/how-to-translate-renpy-games)

**Detected by** a `game/` folder, whatever form the scripts are in.

**What comes out:** `say` dialogue, menu choices (including conditional ones), screen and UI text, `_()` / `__()` / `_p()` translatable strings, and text held in Python data structures.

**All three packaging forms work:**

- **Source** `.rpy` — read directly.
- **Compiled-only** `.rpyc` — decompiled first, so a game that shipped without sources still opens.
- **Archived** `.rpa` — unpacked, including RPA-2 / 3 / 3.2 / 4.0 and the common vendor obfuscations, with the key detected automatically.

**Export:** translation files written into the copied `game/` folder — a translations bundle, a small language hook, and a `translate <lang> strings:` block — plus a font covering your target's script when the Japanese game shipped none — Korean, Chinese, Thai, Arabic, Greek, Cyrillic and Latin-Extended are all covered. Dialogue is matched by source **text**, not by Ren'Py's generated identifiers, so it survives a game update that renumbers them.

There is also a second export mode that fills in the game's own `game/tl/<language>/` files, keeping every translation identifier the Ren'Py launcher wrote. That is the folder you hand back to a game's developer.

**Also for Ren'Py:** the save editor reads `.save` variables, Cheat Mode enables the developer console and a live variable editor, and the [Image Studio](https://runetranslate.com/image-translation) reads loose `game/` art and `.rpa` archives.

---

## Kirikiri / KAG

**Status: Full · ✅ Played** — [engine page](https://runetranslate.com/engines/kirikiri) · [walkthrough](https://runetranslate.com/blog/how-to-translate-kirikiri-visual-novels)

The workhorse of Japanese commercial visual novels, and the most encryption-heavy engine on this list.

**Detected by** `.xp3` archives, KrkrZ markers, signed `.exe.emb` / `.xp3.sig` builds, and archives appended inside the `.exe` itself.

**What comes out:** KAG `.ks` scenario text, inline `[ruby]` / `[name]` / `[title]` / `[button]` / `[edit]` tag text, and compiled PSB `.scn` scenarios.

**Encryption:** around 25 XP3 schemes ported from the format-research community, plus a generic solver for simple single-byte obfuscations. An archive appended to the end of the executable is located the same way the engine itself does it.

**Export:** loose files under the game's script folders **and** a `patch.xp3`. Two delivery routes on purpose, because no single one is universal — the loose files rely on the game running its own initialization hook, while `patch.xp3` is auto-mounted at higher priority and overrides even when that hook is commented out.

**Out of scope:** encrypted or MDF-compressed PSB scenarios, compiled KAG bytecode, and schemes that need per-archive runtime state.

---

## Wolf RPG Editor

**Status: Full · ✅ Played** — [engine page](https://runetranslate.com/engines/wolf-rpg) · [walkthrough](https://runetranslate.com/blog/how-to-translate-wolf-rpg-to-english)

**Detected by** a `.wolf` archive or a `BasicData` folder, at the game root or under `Data/`. Both the 2.x and the newer 3.x engine generations are supported, including encrypted archives.

**What comes out:** map events, common events, database entries and loose script files — messages, choices and database values, while comments and internal reference operands are deliberately left alone.

**Export rebuilds the archive.** This matters more here than anywhere else: Wolf's runtime reads the `.wolf` archive *in preference to* loose files on disk, so a loose-only patch produces a green progress bar and a game still entirely in Japanese. RuneTranslate repacks with the same scheme the game's own archives declare, verifies the rebuilt archive holds at least what it was built from, and falls back to a documented loose-file delivery only when a rebuild genuinely cannot be produced.

**Worth knowing:** Wolf games are usually Shift-JIS, and RuneTranslate can render **Thai** in them by shipping a matching font and repointing the game's font table.

---

## TyranoBuilder / TyranoScript

**Status: Full** — [engine page](https://runetranslate.com/engines/tyranobuilder) · [walkthrough](https://runetranslate.com/blog/how-to-translate-tyranobuilder-games)

**Detected by** `tyrano/tyrano.js` plus `data/scenario/*.ks`, in both packaging shapes: Electron-wrapped (inside `resources/app.asar`) and HTML5 standalone (loose files at the root).

**What comes out:** every `.ks` scenario, the UI strings in `tyrano/lang.js`, `data/system/Config.tjs`, and character display names — which are injected as proper `chara_new` entries so the engine's own character lookup keeps working. Inline KAG tags are masked before translation so a provider cannot mangle them.

**Export:** a runnable translated build in the game's own shape.

---

## Electron visual novels

**Status: Full · ✅ Played** — [engine page](https://runetranslate.com/engines/electron-vn)

The catch-all for custom Electron shells — including Cocos Creator games — that are not TyranoBuilder.

**Detected by** `resources/app.asar` without Tyrano's markers.

**What comes out:** the game's dialogue files plus a general scan of the bundled `.js`, `.html`, `.json` and `.ks` assets. Template expressions are masked so a translated line stays valid JavaScript. In Cocos builds, asset UUIDs that sit next to dialogue in the same JSON are recognised from the game's own resource manifest and excluded, so you are not shown 3,000 rows of asset ids.

**Export:** a rewritten `app.asar` inside a full copy of the game. Electron resolves the archive in preference to a loose folder, so the archive is what has to change — there is no override route. (The Image Studio has a separate streaming path of its own, which swaps a single image inside a multi-gigabyte archive in seconds without unpacking it.)

---

## Unity

**Status: Best-effort · ✅ Played** — [engine page](https://runetranslate.com/engines/unity) · [walkthrough](https://runetranslate.com/blog/how-to-translate-unity-games)

**Detected by** a `<Name>_Data/` folder.

**What comes out — externalized text, on both Mono and IL2CPP builds:**

- `TextAsset` and `MonoBehaviour` strings from `.assets`, `level*` and asset bundles
- Localization tables (`m_Array` JSON tables, XUnity.AutoTranslator dictionaries)
- `StreamingAssets` scripts and, for some in-house VN engines, their custom `StreamingAssets` archives — where the entire script sometimes turns out to live
- String literals in a Mono `Assembly-CSharp.dll`, gated on how each one is actually used
- Encrypted Addressable bundles, decrypted where the key can be recovered

**Export:** a full translated copy of the game, with assets patched in place.

**Out of scope:** strings compiled into an IL2CPP binary. Control identifiers, localization keys, locale codes and engine wiring are recognised and excluded rather than translated — translating those is the classic cause of a Unity game that hangs on a loading screen with no error at all.

**If your Unity game shows boxes instead of text:** that is a font issue, and there is a [write-up for it](https://runetranslate.com/blog/unity-translated-text-shows-boxes).

---

## Unreal Engine 4 / 5

**Status: Best-effort · ✅ Played** — [engine page](https://runetranslate.com/engines/unreal) · [walkthrough](https://runetranslate.com/blog/how-to-translate-unreal-engine-games)

**Detected by** `<Game>/Content/Paks/*.pak`, or UE5 IoStore `.utoc` / `.ucas` containers.

**What comes out:** the `.locres` UI, menu, system and subtitle text. Every namespace, key and source-string hash is preserved exactly; only the value changes. For games that ship no `.locres` at all, text baked into cooked Blueprint assets can be lifted into a runtime `.locres` override instead.

**Encryption:** AES-encrypted paks are supported, and the key is recovered from the game itself where possible rather than asked for.

**Export:** a small, unencrypted override `_P.pak` that you drop into `Content/Paks`. Unreal mounts `_P` last, so it shadows the base archives — no re-signing, and a 60 GB game is not duplicated to change its menus.

**Out of scope, and reported rather than silently skipped:** DataTables and general cooked `.uasset` text. Oodle-compressed loose paks need the bundled retoc sidecar or the game's own `oo2core` library.

---

## Godot 3.x / 4.x

**Status: Best-effort · ✅ Played** — [engine page](https://runetranslate.com/engines/godot) · [walkthrough](https://runetranslate.com/blog/how-to-translate-godot-games)

**Detected by** a `.pck` beside the executable, or a `.pck` embedded inside the `.exe`.

**What comes out:** dialogue and UI text from GDScript, scene files, Godot's own compiled `.translation` resources (patched by value, so the game's keys keep resolving), and Dialogic timelines.

**Export:** a repacked, runnable build.

**Worth knowing:** Godot projects are frequently written in English, so RuneTranslate's exclusion rules for this engine work by *position* — is this string a signal name, a constructor argument, a dictionary key? — rather than by guessing from the words. On a real Latin-source game that took 2,839 apparent lines down to the 13 that were actually shown to a player.

---

## RPG Developer Bakin

**Status: Best-effort · ✅ Played** — [engine page](https://runetranslate.com/engines/bakin)

**Detected by** Bakin's own data layout.

**What comes out:** database text — items, skills, characters — and event/scenario text, routed through Bakin's own localization data, so the exported build simply opens in your language.

**Two build shapes** exist depending on whether the game ships localization data at all, and RuneTranslate picks the right one automatically.

---

## SRPG Studio

**Status: Best-effort** — [engine page](https://runetranslate.com/engines/srpg-studio) · [walkthrough](https://runetranslate.com/blog/how-to-translate-srpg-studio-games)

**Detected by** an SRPG Studio `data.dts`.

**What comes out:** story text, the database, item and unit text, and event text — unpacked from the encrypted data file, translated, and repacked.

**Export:** a full runnable copy of the game.

---

## NScripter / ONScripter

**Status: Best-effort · ✅ Played** — [engine page](https://runetranslate.com/engines/nscripter) · [walkthrough](https://runetranslate.com/blog/how-to-translate-nscripter-onscripter-games)

The classic doujin visual-novel engine and its open-source descendant, both of which keep the entire game in one script file at the game root.

**Detected by** `nscript.dat`, `nscript.zat` or a loose `0.txt`, in whichever obfuscated form the game shipped — the form is detected and the export is written back in the *same* form, because these engines will not read any other.

**What comes out:** dialogue and choices. Commands that share a line with dialogue are recognised as commands and left untouched.

**Thai works here**, which is unusual: NScripter only ever understood the Japanese character set, so RuneTranslate ships a purpose-built font and maps Thai text through it cluster by cluster. Verified in-game on a real 313,000-line title.

---

## Artemis (Mikage)

**Status: Full · ✅ Played** — [engine page](https://runetranslate.com/engines/artemis) · [walkthrough](https://runetranslate.com/blog/how-to-translate-artemis-games)

**Detected by** `.pfs` archives (PF8, PF6 and PF2, including PF8's hash-based encryption).

**What comes out:** dialogue, speaker names and choices from the Lua-based `.ast` and `.txt` scripts.

**Export:** loose files plus an override archive, so the game picks the translation up whichever way it loads its scripts.

**Thai also works here**, via the same character-set tunnelling approach used for NScripter, and it has been confirmed in-game.

---

## YU-RIS

**Status: Best-effort** — [engine page](https://runetranslate.com/engines/yu-ris) · [walkthrough](https://runetranslate.com/blog/how-to-translate-yu-ris-games)

raiL-soft's engine, handled in pure TypeScript with no external tool.

**Detected by** a `.ypf` package in the root or `pac/`, or a loose `ysbin/` folder of YSTB `.ybn` scripts.

**What comes out:** dialogue from the compiled YSTB scripts, with the per-script XOR key worked out automatically. Raw YU-RIS dialogue carries nothing that marks it as text, so the adapter identifies script *values* by their declared type and by the engine's own command grammar rather than by looking at the words — which is what keeps bytecode out of your line list.

**Export:** a loose-file override on a copy of the game.

**Worth knowing:** the engine writes text as CP932, so non-Japanese-charset targets are limited today.

---

## AliceSoft System 3.x / 4

**Status: Full** — [engine page](https://runetranslate.com/engines/alicesoft) · [walkthrough](https://runetranslate.com/blog/how-to-translate-alicesoft-games)

The Rance and Evenicle era of AliceSoft's in-house engine, handled in pure TypeScript.

**Detected by** `.ald` / `.afa` archives and a `System39.ain` (System 3.x) or per-game `.ain` (System 4), including the compressed and encrypted container variants.

**What comes out:** the message text.

**Export:** a copy of the game with the translated data dropped in.

---

## LiveMaker / LiveNovel

**Status: Best-effort** — [engine page](https://runetranslate.com/engines/livemaker)

**Detected by** a VFF archive at the end of the `.exe`, or a loose `.dat` / `.ext` archive pair.

**What comes out:** dialogue, text-menu choices and caption text from the compiled `.lsb` scenarios. Object names, flow operands, fonts and positions are deliberately left alone.

**Export:** a full runnable copy of the game with the archive repacked into the executable. The rebuilt archive is re-opened and re-parsed before anything is overwritten, so a half-written repack never reaches your output folder.

**Worth knowing:** LiveMaker text is CP932, so targets outside that character set are out of scope; anything unencodable is flagged rather than silently mangled.

---

## Gettext `.po` / `.mo`

**Status: Format** — [engine page](https://runetranslate.com/engines/gettext) · [walkthrough](https://runetranslate.com/blog/how-to-translate-po-and-mo-files)

Not an engine but a catalog format — what Python, pygame, SDL, Solarus and anything localized with Poedit or Weblate ships, and something a Godot or Unity game may also carry alongside its own data.

**What comes out:** every translatable message in the catalog, plurals and contexts included.

**Export:** both a fresh locale directory *and* the catalog the game is currently loading, because writing only the former is the usual reason a correctly translated `.po` never shows up in the game.

---

## My engine is not here

Three things to try, in order:

1. **Open the folder anyway.** A great many games are built on an engine on this list without advertising it — Electron shells, Unity games with an unusual folder name, Kirikiri games with a renamed archive. Detection is cheap, so let it answer.
2. **Look for a catalog.** If the game ships `.po` / `.mo` files, or you can get CSV / JSON / XLIFF out of it, the [gettext support](#gettext-po--mo) and the Developer interchange tab can translate it whatever the engine is.
3. **[Ask on Discord](https://discord.gg/ZtsfZu7YsW)**, or email `runetranslate@gmail.com` with the game and a listing of its folder. Most of the engines on this page were added because somebody sent in a game that would not open.

---

**[← Back to the README](../README.md)** · **[Features](features.md)** · **[Comparison](comparison.md)** · **[FAQ](faq.md)** · **[Troubleshooting](troubleshooting.md)**
