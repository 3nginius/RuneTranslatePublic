# Japanese game file formats: what each extension is

**[← Back to the README](../README.md)** · **[Engines](engines.md)** · **[Troubleshooting](troubleshooting.md)** · **[Download](https://runetranslate.com/download)**

You opened a Japanese game folder and found a file you have never seen before. This page says what it is, which engine wrote it, whether the text inside is plain or compiled, and whether **[RuneTranslate](https://runetranslate.com)** can read it.

Everything here is a *container or data* format. If your file is not listed, check [the engine list](engines.md) — the engine is usually easier to identify than the extension.

---

## Contents

- [RPG Maker](#rpg-maker)
- [Ren'Py](#renpy)
- [Kirikiri / KAG](#kirikiri--kag)
- [Wolf RPG](#wolf-rpg)
- [Unity](#unity)
- [Unreal Engine](#unreal-engine)
- [Godot](#godot)
- [Visual novel engines](#visual-novel-engines)
- [Other engines](#other-engines)
- [Portable text formats](#portable-text-formats)
- [Save files](#save-files)
- [RuneTranslate's own files](#runetranslates-own-files)

---

## RPG Maker

### `data/*.json` — RPG Maker MV / MZ game data

Plain JSON. `Map001.json` and friends hold events and dialogue; `Items.json`, `Actors.json`, `Skills.json` and the rest are the database; `System.json` holds terms and the title. MV keeps them under `www/data/`, MZ under `data/`.
**Readable?** Yes, in a text editor — but editing by hand is how people break games, because dialogue is stored as command codes inside nested arrays. → [RPG Maker MV / MZ](engines.md#rpg-maker-mv--mz)

### `.rgssad` · `.rgss2a` · `.rgss3a` — RPG Maker XP / VX / VX Ace archive

The encrypted archive holding everything the Ruby generation of RPG Maker ships: `Data/`, `Graphics/`, `Audio/`. `.rgssad` is XP, `.rgss2a` is VX, `.rgss3a` is VX Ace.
**Readable?** Not directly. RuneTranslate decrypts it automatically. → [RPG Maker XP / VX / VX Ace](engines.md#rpg-maker-xp--vx--vx-ace)

### `.rxdata` · `.rvdata` · `.rvdata2` — RPG Maker XP / VX / VX Ace data

Ruby Marshal serialization — the Ruby equivalent of MV/MZ's JSON, holding maps, events and the database. XP and VX store text as Shift-JIS; VX Ace uses UTF-8.
**Readable?** Binary. RuneTranslate parses them directly.

### `.rpgmvp` · `.rpgmvo` · `.rpgmvm` · `.png_` · `.ogg_` · `.m4a_` — encrypted RPG Maker assets

Ordinary PNG, OGG and M4A files with an encrypted header. The `.rpgmv*` set is MV; the trailing-underscore set is MZ. Some games use an encryption *plugin* with a scheme of its own instead of RPG Maker's.
**Readable?** Rename to `.png` and it will not open — the header is scrambled. The [Image Studio](https://runetranslate.com/image-translation) reads and re-encrypts these, working the scheme out from the file itself rather than assuming RPG Maker's, so plugin-encrypted games work too.

### `.lsd` — RPG Maker 2000 / 2003 save

`LcfSaveData`, the save format of the two oldest RPG Makers.
**Readable?** Binary. RuneTranslate's [save editor](https://runetranslate.com/save-editor) opens it. Note that translating RM2K/2K3 *game text* is not supported — only the saves.

---

## Ren'Py

### `.rpy` — Ren'Py script

Plain-text Python-flavoured source: dialogue, menus, screens, everything. The friendliest format on this page.
**Readable?** Yes, in any text editor. → [Ren'Py](engines.md#renpy)

### `.rpyc` — compiled Ren'Py script

The bytecode Ren'Py generates from a `.rpy`. Many commercial games ship *only* these.
**Readable?** No. RuneTranslate decompiles them so a source-free game still opens.

### `.rpa` — Ren'Py archive

The container holding a Ren'Py game's scripts and assets. Versions RPA-2, RPA-3, RPA-3.2 and RPA-4.0 exist, and some vendors obfuscate the index.
**Readable?** Not directly. RuneTranslate unpacks all of the above, detecting the key automatically.

---

## Kirikiri / KAG

### `.xp3` — Kirikiri archive

The container almost every Kirikiri visual novel ships. Frequently encrypted, and the encryption is usually per-publisher rather than standard. An `.xp3` can also be appended to the end of the game's `.exe` with no separate file on disk at all.
**Readable?** Not directly. RuneTranslate ports around 25 known schemes plus a solver for simple ones. → [Kirikiri / KAG](engines.md#kirikiri--kag)

### `.ks` — KAG scenario script

Kirikiri's scenario format: dialogue interleaved with `[tags]`. Also the extension TyranoScript uses, since Tyrano is a KAG descendant.
**Readable?** Usually yes once extracted, unless the game compiled it to bytecode.

### `.scn` — compiled PSB scenario

A Kirikiri scenario compiled into PSB, a binary structure format. Some are additionally encrypted or MDF-compressed.
**Readable?** No. RuneTranslate reads the unencrypted, non-compressed form; the encrypted variants are out of scope and are reported rather than silently skipped.

### `.tjs` — Kirikiri script

The engine's own scripting language, used for the UI and game logic rather than dialogue.

### `.tlg` — Kirikiri image

Kirikiri's own lossless image format. The Image Studio reads and writes it, so a translated title screen goes back in as a `.tlg`.

---

## Wolf RPG

### `.wolf` — Wolf RPG archive

A DXArchive container, usually encrypted, holding `Data/`. **The engine reads this archive in preference to loose files on disk** — which is why a translation delivered as loose files alone appears to do nothing at all. RuneTranslate rebuilds the archive. → [Wolf RPG](engines.md#wolf-rpg-editor)

### `.dat` (Wolf) — common events and database

`CommonEvent.dat`, `DataBase.dat`, `CDataBase.dat`, `SysDatabase.dat` and `Game.dat` under `Data/BasicData/`. Command streams and database tables, not plain text.

### `.mps` — Wolf map

One file per map, holding its events and their dialogue.

---

## Unity

### `resources.assets` · `sharedassets*.assets` · `level*` · `globalgamemanagers`

Unity's serialized asset files, under `<GameName>_Data/`. Text lives in them as `TextAsset` contents and `MonoBehaviour` fields.
**Readable?** Binary, and the layout depends on the Unity version the game was built with. → [Unity](engines.md#unity)

### `data.unity3d` · `.bundle` · `.unity3d` — Unity asset bundles

Bundled assets, sometimes compressed and sometimes encrypted (Addressables can be shipped with AES encryption). A rewritten bundle also has to have its catalog entry updated or the game will refuse to load it.

### `StreamingAssets/` — anything at all

Unity copies this folder verbatim into the build, so studios put whatever they like in it — JSON scripts, CSV tables, or a custom archive of their own. On some in-house visual-novel engines the *entire* script lives here rather than in the Unity assets.

### `Assembly-CSharp.dll` — the game's own code

A .NET assembly on Mono builds. Strings compiled into it can be read and rewritten where they are genuinely display text. On IL2CPP builds the code is compiled to native binaries instead, and those strings are out of scope.

---

## Unreal Engine

### `.pak` — Unreal package archive

The main container, under `<Game>/Content/Paks/`. Often AES-encrypted, and often Oodle-compressed. Note that **`_P.pak` files mount last**, which is why an override pak is the polite way to patch an Unreal game — no repack, no re-sign, no duplicated 60 GB. → [Unreal Engine](engines.md#unreal-engine-4--5)

### `.utoc` · `.ucas` — UE5 IoStore containers

UE5's newer packaging. `.utoc` is the table of contents, `.ucas` the data.

### `.locres` — Unreal localization resource

The compiled string table Unreal loads at runtime: namespaces, keys, and the text. This is the file a translated Unreal game actually reads.
**Readable?** Binary, but structurally simple — RuneTranslate rewrites only the values and preserves every hash, which is what keeps the game's lookups working.

### `.uasset` — cooked Unreal asset

Everything else Unreal cooks. Text baked into Blueprints lives here; general `.uasset` text is out of scope, but a game that ships no `.locres` at all can have that text lifted into a runtime `.locres` override instead.

---

## Godot

### `.pck` — Godot package

Everything a Godot game ships. It may sit beside the executable, or be **embedded inside the `.exe`** with no `.pck` on disk. Godot 3 and Godot 4 use different layouts, and the pack can be encrypted.
**Readable?** Not directly. RuneTranslate unpacks both, embedded included. → [Godot](engines.md#godot-3x--4x)

### `.translation` — Godot compiled translation

Godot's own compiled message catalog, generated from a CSV or PO at export. RuneTranslate patches it by value, so the game's keys keep resolving.

### `.gd` · `.tscn` · `.scn` — GDScript and scenes

Script and scene files. In a `.pck` they are usually stored compiled, which is why simply unzipping a pack rarely gives you readable dialogue.

---

## Visual novel engines

### `nscript.dat` · `nscript.zat` · `0.txt` — NScripter / ONScripter script

The whole game in one file: dialogue, choices and commands. `0.txt` is the plain form; `nscript.dat` and `nscript.zat` are obfuscated in two different ways, and the engine will only load the form it expects — so a translation has to be written back in the *same* form it was read in. → [NScripter / ONScripter](engines.md#nscripter--onscripter)

### `.nsa` · `.sar` — NScripter archive

The asset containers beside the script. The Image Studio reads images out of them.

### `.pfs` — Artemis archive

The container for Artemis (Mikage) visual novels, in PF8, PF6 and PF2 variants; PF8 adds a hash-based scrambling of the data. Dialogue inside lives in `.ast` and `.txt` scripts. → [Artemis](engines.md#artemis-mikage)

### `.ypf` — YU-RIS package

raiL-soft's archive format. The scripts inside are `.ybn` files in the YSTB format, obfuscated with a per-script key.
**Readable?** No. RuneTranslate recovers the key by itself. → [YU-RIS](engines.md#yu-ris)

### `.ald` · `.afa` · `.ain` — AliceSoft System

`.ald` and `.afa` are archives; `.ain` is the compiled program — `System39.ain` on System 3.x, or a per-game `.ain` on System 4 — and the message text lives inside it. → [AliceSoft System](engines.md#alicesoft-system-3x--4)

### `.lsb` — LiveMaker scenario

LiveMaker's compiled scenario: dialogue, menu choices and flow logic in one binary. The archive holding them is a **VFF** container, which is usually appended to the end of the game's `.exe` rather than shipped as a separate file — though a loose `.dat` / `.ext` pair also exists. → [LiveMaker](engines.md#livemaker--livenovel)

### `data.dts` — SRPG Studio data

The single encrypted file holding an SRPG Studio game's story, database, units and events. → [SRPG Studio](engines.md#srpg-studio)

---

## Other engines

### `app.asar` — Electron archive

Under `resources/`. Electron mounts this archive **in preference to** a loose `resources/app/` folder, which is why patching an Electron game means rewriting the archive rather than dropping files beside it. Custom visual-novel shells, Cocos Creator games and TyranoBuilder's Electron builds all ship one. → [Electron visual novels](engines.md#electron-visual-novels)

### `data/scenario/*.ks` — TyranoBuilder scenario

Tyrano inherits KAG's `.ks` scenario format. A Tyrano game may be an Electron build (inside `app.asar`) or loose HTML5 files at the root. → [TyranoBuilder](engines.md#tyranobuilder--tyranoscript)

---

## Portable text formats

### `.po` · `.mo` — gettext catalogs

The oldest and most portable localization format going: `.po` is the editable text catalog, `.mo` its compiled form. Shipped by Python and pygame games, SDL games, Solarus, and anything localized with Poedit or Weblate — and sometimes carried *alongside* an engine's own data.
**Readable?** `.po` yes, in any text editor or Poedit. RuneTranslate reads both, and writes both a fresh locale and the catalog the game is already loading — writing only the former is the usual reason a correct `.po` never appears in the game. → [Gettext](engines.md#gettext-po--mo)

### `.csv` · `.json` · `.xliff` — interchange formats

Not game formats, but the formats a localization pipeline speaks. RuneTranslate's Developer tab imports and exports all of them plus `.po`, with ids and keys preserved, which is the route for an engine nothing on this page covers.

---

## Save files

RuneTranslate's [save editor](https://runetranslate.com/save-editor) opens all of these — free, on every tier:

| Extension | Engine |
|---|---|
| `.rpgsave` | RPG Maker MV |
| `.rmmzsave` | RPG Maker MZ |
| `.rxdata` | RPG Maker XP |
| `.rvdata` | RPG Maker VX |
| `.rvdata2` | RPG Maker VX Ace |
| `.lsd` | RPG Maker 2000 / 2003 |
| `.save` | Ren'Py |
| `.sav` | TyranoBuilder / TyranoScript |

Variable and switch names are read from the game itself, so you edit *Gold* rather than *variable 42* — and those Japanese labels can be translated too. Every change autosaves, and the original is backed up on the first edit.

---

## RuneTranslate's own files

### `.rtproj` — a RuneTranslate project

Your extracted lines, translations, edits, filters and settings for one game. It lives on your own disk and contains no game assets. Earlier versions used `.gtproj`, which still opens.

### `.rtpatch` — a shared translation patch

Your translations plus the source lines they attach to, and **no game files, art or audio at all**. Hand one to somebody who owns the same game and they apply it in one click and export their own build. It is also how you move your own work between PCs or send a project to a proofreader. → [How to make a translation patch](https://runetranslate.com/blog/how-to-make-a-translation-patch)

---

**[← Back to the README](../README.md)** · **[Engines](engines.md)** · **[Features](features.md)** · **[Comparison](comparison.md)** · **[FAQ](faq.md)** · **[Troubleshooting](troubleshooting.md)**
