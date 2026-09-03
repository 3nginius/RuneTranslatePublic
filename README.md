<div align="center">

<a href="https://runetranslate.com"><img src="https://runetranslate.com/icon-512.png" width="112" alt="RuneTranslate" /></a>

# RuneTranslate

### Translate Japanese games into English — and 34 other languages

**A Windows desktop app that reads a game's own files, translates every line, and exports a playable build in your language.**
RPG Maker, Ren'Py, Kirikiri, Wolf RPG, Unity, Unreal, Godot, NScripter and eight more engines, plus gettext catalogs. No overlay. No hook. No server left running.

[![Download for Windows](https://img.shields.io/badge/Download-Windows%2010%20%2F%2011-EC4899?style=for-the-badge&logo=windows&logoColor=white)](https://runetranslate.com/download)
[![RuneTranslate website](https://img.shields.io/badge/Website-runetranslate.com-7C9EFF?style=for-the-badge&logo=firefoxbrowser&logoColor=white)](https://runetranslate.com)
[![Discord community](https://img.shields.io/badge/Discord-Join-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/ZtsfZu7YsW)
[![Support on Patreon](https://img.shields.io/badge/Patreon-Support-FF424D?style=for-the-badge&logo=patreon&logoColor=white)](https://www.patreon.com/cw/runetranslate/membership)

**[Download](https://runetranslate.com/download)** · **[Engines](https://runetranslate.com/engines)** · **[Guides](https://runetranslate.com/blog)** · **[FAQ](https://runetranslate.com/faq)** · **[Compare](https://runetranslate.com/compare)** · **[Changelog](https://runetranslate.com/changelog)**

**In this repo:** [Engines](docs/engines.md) · [File formats](docs/file-formats.md) · [Features & pricing](docs/features.md) · [Comparison](docs/comparison.md) · [FAQ](docs/faq.md) · [Troubleshooting](docs/troubleshooting.md)

</div>

---

## Contents

- [What RuneTranslate does](#what-runetranslate-does)
- [Download and install](#download-and-install)
- [How to translate a Japanese game to English in four steps](#how-to-translate-a-japanese-game-to-english-in-four-steps)
- [Supported game engines and file formats](#supported-game-engines-and-file-formats)
- [Translation providers](#translation-providers)
- [Languages: Japanese to English, and 34 more](#languages-japanese-to-english-and-34-more)
- [The translation editor](#the-translation-editor)
- [Image translation, save editing and cheat menus](#image-translation-save-editing-and-cheat-menus)
- [Collaborative and overnight translation](#collaborative-and-overnight-translation)
- [Pricing](#pricing)
- [RuneTranslate vs Translator++, MTool, Sugoi Toolkit and XUnity.AutoTranslator](#runetranslate-vs-translator-mtool-sugoi-toolkit-and-xunityautotranslator)
- [Frequently asked questions](#frequently-asked-questions)
- [Troubleshooting: when a translated game misbehaves](#troubleshooting-when-a-translated-game-misbehaves)
- [Links and community](#links-and-community)

---

## What RuneTranslate does

There are only three ways to get Japanese out of a game: **patch its files**, **hook it while it runs**, or **read the pixels off your screen**. Only the first one leaves you holding a translated game instead of a translated session.

RuneTranslate is a file patcher — an MTL tool of the kind fan-translation projects use — and a thorough one. Point it at a game folder and it identifies the engine, opens the archives, pulls every translatable string (dialogue, choices, item names, skill descriptions, menus, system terms, plugin text) into an editable project, translates them through the provider you pick, and writes a **playable build** into an output folder of your choosing. Your original game is never modified.

- **17 engines and formats**, one workflow — see the [full table](#supported-game-engines-and-file-formats)
- **10 translation providers** — DeepL, OpenAI, Claude, DeepSeek, Google, a local model, and more. **Five need no API key at all**
- **35 languages**, source and target — Japanese is the default source, not a hard-coded one
- **Runs on your PC.** Translation requests go straight from your machine to the provider you picked, and API keys are encrypted locally and never leave. The only things that reach RuneTranslate's servers are the ones that have to — sign-in, updates, and the cloud features you opt into (translation memory, collaborative projects, and the Image Studio's text detection)
- **Every engine, every provider and the whole editor are free.** Paid plans buy speed and convenience, not access

> **Windows 10 / 11 (x64)** — and it runs well on Linux and the Steam Deck through Wine or Proton. Not affiliated with any engine vendor. Intended for personal and fan-translation use — respect the licence of every game you touch.

<div align="center">

[![Watch: how to translate a Japanese game to English with RuneTranslate](https://runetranslate.com/videos/how-to-use-poster.png)](https://www.youtube.com/watch?v=1xsez7SFdlk)

**▶ [Watch the two-minute walkthrough](https://www.youtube.com/watch?v=1xsez7SFdlk)**

</div>

---

## Download and install

**[⬇ Download the Windows installer at runetranslate.com/download](https://runetranslate.com/download)**

Run it, sign in once with Patreon, and you are ready. New versions download in the background and prompt you to restart. There is nothing to compile and no runtime to install first.

Signing in is free and takes one click — a pledge is not required, and "free tier" simply means signed in without one. After that first sign-in your sign-in is verified on your own machine, so the app keeps working with no connection; it re-checks about once a day, so you do need to be online occasionally.

The build is not code-signed, so Windows SmartScreen shows an "unrecognised app" warning the first time. A checksum is published with each release. **Only download from [runetranslate.com/download](https://runetranslate.com/download)** — no installer is distributed from this repository.

---

## How to translate a Japanese game to English in four steps

**1. Open the game folder.** *New project* → point it at the game directory. The engine is detected automatically and every translatable string is pulled into a project. A report tells you which files were read and which were skipped, so missing dialogue is never a mystery.

**2. Pick a language and a provider.** Choose your target language and a translation engine — free Google, free DeepL, DeepL with your key, OpenAI, Claude, DeepSeek, an OpenAI-compatible endpoint, on-device Gemini Nano, or your own local model. You can also tick exactly which of the game's files to include, so a test run costs a few hundred lines instead of the whole game.

**3. Translate, then read it back.** Watch the progress bar and live ETA. Afterwards, work through the editor: find and replace, regex filters, a glossary to lock character names, and an optional AI refiner that re-reads each line in context and fixes stiff first-draft phrasing. On big OpenAI, Claude or DeepSeek runs you get a token and USD estimate *before* anything is sent.

**4. Export.** Pick an output folder. RuneTranslate writes a translated, playable copy there — or, where the engine prefers it, a small override the game loads on top of itself. Launch it and play. Re-run any time; your manual edits are kept.

📖 Full beginner walkthrough: **[How to translate a Japanese game to English](https://runetranslate.com/blog/how-to-translate-a-japanese-game-to-english)**

---

## Supported game engines and file formats

**17 engines and formats** — sixteen game engines plus the gettext catalog format, all unlocked on the free tier. RPG Maker takes two rows below because the Ruby generation (XP / VX / Ace) is a different reader, but it is one engine.

| Engine | Status | What it reads, and what you get |
|---|---|---|
| **[RPG Maker MV / MZ](https://runetranslate.com/engines/rpg-maker)** | Full | Event dialogue, choices, the whole database and plugin strings out of `data/*.json`, with in-game word-wrap applied on export. Handles games packed into a single `.exe` and natively protected builds. ✅ *Confirmed playable in-game.* |
| **[RPG Maker XP / VX / VX Ace](https://runetranslate.com/engines/rpg-maker-xp-vx-ace)** | Full | The Ruby (RGSS) generation — events, database and system terms, read from a loose `Data` folder or straight out of an encrypted `.rgssad` / `.rgss2a` / `.rgss3a` archive. Exports a full runnable copy. |
| **[Ren'Py](https://runetranslate.com/engines/renpy)** | Full | Source `.rpy`, compiled-only `.rpyc` and archived `.rpa` games alike. Delivers translation files into the game's own `game/` folder, bundling a font for your target's script when the Japanese game shipped none. Can also fill in the game's own `tl/<language>/` files — the folder you hand back to a developer. |
| **[Kirikiri / KAG](https://runetranslate.com/engines/kirikiri)** | Full | KAG scripts and compiled PSB scenarios inside XP3 archives, with around 25 encryption schemes ported and a generic solver for simple ones. Ships loose files *plus* a patch archive, so it overrides whichever way the game loads. ✅ *Confirmed playable in-game.* |
| **[Wolf RPG](https://runetranslate.com/engines/wolf-rpg)** | Full | Maps, common events and the database from encrypted `.wolf` archives on both 2.x and 3.x, then **rebuilds the archive** — because Wolf reads the archive in preference to loose files, so a loose-only patch would silently do nothing. ✅ *Confirmed playable in-game.* |
| **[TyranoBuilder / TyranoScript](https://runetranslate.com/engines/tyranobuilder)** | Full | Scenario scripts, config and UI strings from both Electron-wrapped and HTML5 builds, including character display names. |
| **[Electron visual novels](https://runetranslate.com/engines/electron-vn)** | Full | The catch-all for custom Electron shells, including Cocos Creator games: reads the text out of `app.asar` and rewrites the archive itself, because Electron always prefers `app.asar` to a loose folder — there is no override route. You get a full translated copy of the game. ✅ *Confirmed playable in-game.* |
| **[Unity](https://runetranslate.com/engines/unity)** | Best-effort | Externalized text on both Mono and IL2CPP builds — `TextAsset`, `MonoBehaviour` fields, localization tables, `StreamingAssets` scripts, encrypted Addressable bundles, and — on Mono builds — the string literals compiled into `Assembly-CSharp.dll`. Exports a full translated copy. ✅ *Confirmed playable in-game.* |
| **[Unreal Engine 4 / 5](https://runetranslate.com/engines/unreal)** | Best-effort | `.locres` UI, menu, system and subtitle text from `.pak` archives and UE5 IoStore containers, recovering the AES key by itself where a game uses one. Output is a small override `_P.pak` you drop into `Content/Paks` — no multi-gigabyte repack. ✅ *Confirmed playable in-game.* |
| **[Godot 3.x / 4.x](https://runetranslate.com/engines/godot)** | Best-effort | Unpacks the `.pck` — including one embedded inside the `.exe` — recovers dialogue and UI from GDScript, scenes and Godot's own `.translation` resources, and repacks a runnable build. ✅ *Confirmed playable in-game.* |
| **[RPG Developer Bakin](https://runetranslate.com/engines/bakin)** | Best-effort | Database text (items, skills, characters) and event/scenario text through Bakin's own localization data. The exported build opens already in your language. ✅ *Confirmed playable in-game.* |
| **[SRPG Studio](https://runetranslate.com/engines/srpg-studio)** | Best-effort | Unpacks the encrypted `data.dts`, translates story, database, item and event text, and repacks a full runnable copy. |
| **[NScripter / ONScripter](https://runetranslate.com/engines/nscripter)** | Best-effort | The classic single-script engines, scrambled script forms included, rewritten in exactly the form the engine expects. It can even render **Thai** on these Japanese-charset-only engines by shipping a matching font. ✅ *Confirmed playable in-game.* |
| **[Artemis (Mikage)](https://runetranslate.com/engines/artemis)** | Full | Lua-based Artemis visual novels: reads `.pfs` archives (PF8 / PF6 / PF2) and exports both loose files and an override archive. ✅ *Confirmed playable in-game.* |
| **[YU-RIS](https://runetranslate.com/engines/yu-ris)** | Best-effort | raiL-soft's engine: reads `.ypf` packages and the compiled YSTB scripts inside them, working out the script key on its own, and exports translated scripts as a loose-file override. |
| **[AliceSoft System 3.x / 4](https://runetranslate.com/engines/alicesoft)** | Full | The Rance and Evenicle era — `.ald` / `.afa` archives and the message text inside `System39.ain` or a per-game `.ain`, exported by loose-file override. |
| **[LiveMaker / LiveNovel](https://runetranslate.com/engines/livemaker)** | Best-effort | Dialogue and menu choices out of the compiled `.lsb` scenarios inside the VFF archive embedded in the `.exe`, repacked into a runnable translated copy. |
| **[Gettext `.po` / `.mo`](https://runetranslate.com/engines/gettext)** | Format | Not an engine but a catalog format — what Python, pygame, SDL and anything localized with Poedit or Weblate ships. Writes both a fresh locale and the catalog the game is already loading, so the text actually appears. |

**Status** is the app's own support level, shown to you again when you open a game: *Full* means the engine is handled end to end; *Best-effort* means games in that family vary enough that some need a hand — and the app tells you when it hits something it cannot read, rather than failing quietly. A ✅ marks an engine where a **real game was translated, exported, launched and played with translated text on screen**, on a recorded app version.

**Engine not listed?** Many games are built on a supported engine without saying so — open the folder in *New project* and let detection answer. If it really is something new, [say so on Discord](https://discord.gg/ZtsfZu7YsW) or email [runetranslate@gmail.com](mailto:runetranslate@gmail.com) with the game and a folder listing: most of the engines above were added because somebody sent in a game that would not open.

📖 Per-engine walkthroughs: **[RPG Maker](https://runetranslate.com/blog/how-to-translate-rpg-maker-games)** · **[Ren'Py](https://runetranslate.com/blog/how-to-translate-renpy-games)** · **[Kirikiri](https://runetranslate.com/blog/how-to-translate-kirikiri-visual-novels)** · **[Wolf RPG](https://runetranslate.com/blog/how-to-translate-wolf-rpg-to-english)** · **[Unity](https://runetranslate.com/blog/how-to-translate-unity-games)** · **[Unreal](https://runetranslate.com/blog/how-to-translate-unreal-engine-games)** · **[Godot](https://runetranslate.com/blog/how-to-translate-godot-games)** · **[TyranoBuilder](https://runetranslate.com/blog/how-to-translate-tyranobuilder-games)** · **[NScripter](https://runetranslate.com/blog/how-to-translate-nscripter-onscripter-games)** · **[SRPG Studio](https://runetranslate.com/blog/how-to-translate-srpg-studio-games)** · **[Artemis](https://runetranslate.com/blog/how-to-translate-artemis-games)** · **[YU-RIS](https://runetranslate.com/blog/how-to-translate-yu-ris-games)** · **[AliceSoft](https://runetranslate.com/blog/how-to-translate-alicesoft-games)** · **[.po / .mo](https://runetranslate.com/blog/how-to-translate-po-and-mo-files)**

➡️ **Every engine in detail: [docs/engines.md](docs/engines.md)** — and if you are staring at an extension you do not recognise (`.xp3`, `.wolf`, `.rpa`, `.locres`, `.ypf`, `.pfs`…), **[docs/file-formats.md](docs/file-formats.md)** says what it is.

---

## Translation providers

Ten engines, mixed freely. **Five need no API key and no account** — four free cloud routes, plus a local model running entirely on your own hardware.

| Provider | Key needed | Cost | Good for |
|---|---|---|---|
| **Google Translate** (unofficial) | No | Free | Whole games on a budget. The fastest free route — batched, with automatic rotation when an endpoint pushes back |
| **DeepL** (unofficial, free) | No | Free | DeepL quality with no account. Deliberately paced, so it suits smaller jobs rather than a 60,000-line RPG |
| **DeepL Classic / Next-gen** (unofficial, free) | No | Free | The same DeepL quality with no account, over a stateful session — and a choice between DeepL's Classic and Next-gen models |
| **Gemini Nano** (on-device) | No | Free | Runs inside your own Chrome install — nothing leaves the machine. A small model: slower and rougher than the cloud engines |
| **Local model** (Ollama / LM Studio) | No | Free, self-hosted | Fully offline LLM translation on your own GPU. No per-token cost, nothing sent anywhere |
| **DeepL** (official API) | Yes | DeepL's own free tier is 500k chars/month | The best non-LLM quality for long Japanese dialogue |
| **OpenAI** | Yes | Pay per token | `gpt-4o-mini` for cheap context-aware translation, `gpt-4o` for quality |
| **Anthropic Claude** | Yes | Pay per token | Strong on register, tone and onomatopoeia — the pick for dialogue-heavy visual novels |
| **DeepSeek** | Yes | Pay per token | LLM quality at a fraction of the price — often cents for a whole game |
| **OpenAI-compatible** | Yes | Whatever that service charges | OpenRouter, NanoGPT or any endpoint speaking the OpenAI API, with the model list pulled live |

**No provider is locked behind a plan.** Every tier, including free, can use all ten.

API keys are stored encrypted with Windows DPAPI on your own machine and are sent **directly** to the provider — never through RuneTranslate's servers.

The unofficial free endpoints are exactly that: unofficial, rate-limited, and able to change without notice. The app is built around that — it batches, paces itself, rotates, retries and tells you plainly when a limit is real instead of grinding silently.

📖 **[Which provider should you use?](https://runetranslate.com/blog/best-providers-for-translating-japanese-games)** · **[Translating with DeepSeek](https://runetranslate.com/blog/translate-japanese-games-with-deepseek)**

---

## Languages: Japanese to English, and 34 more

**35 languages, and any of them can be the source.** RuneTranslate is built for Japanese and defaults to it, but nothing in the app is hard-coded to it — an English or Chinese game translates just as well.

| | |
|---|---|
| **Most used** | Japanese · **English** · Spanish · French · German · Russian · Chinese (Simplified) · Chinese (Traditional) · Portuguese (Portugal) · Portuguese (Brazil) · Italian · Korean |
| **Also supported** | Dutch · Polish · Turkish · Vietnamese · Arabic · Bulgarian · Czech · Danish · Greek · Estonian · Finnish · Hungarian · Indonesian · Lithuanian · Latvian · Norwegian · Romanian · Slovak · Slovenian · Swedish · Thai · Ukrainian · Mongolian |

Regional variants are first-class: Chinese Simplified and Traditional, and European and Brazilian Portuguese, are four separate choices pinned to the right code on every provider — so "Portuguese" never quietly means one thing on DeepL and another on Google.

The **app's own interface** is translated into 18 languages, Arabic included with a full right-to-left layout.

Two engine-level extras worth knowing about: RuneTranslate bundles fonts for Ren'Py targets whose glyphs a Japanese game never had, and it can render **Thai** inside NScripter, Artemis and Wolf RPG games whose engines only ever understood the Japanese character set.

---

## The translation editor

The translation is the easy half. The editor is where a machine draft becomes something worth playing.

- **One fast table** for every extracted line, grouped by the file it came from, filtered by status, edited inline with autosave. Tens of thousands of lines stay responsive.
- **Find & replace** across source, translation or a single file, with case-sensitive and full-regex modes.
- **Regex exclusion filters** keep asset paths, variable keys and engine plumbing out of your run. Excluded lines become red opt-in rows — nothing is silently deleted, and you can force-translate one whenever the filter was wrong.
- **A regex rule library** at account level. Star a pattern once, reuse it in the next project instead of retyping it. Free and unlimited locally on every tier.
- **Glossary** — force `勇者 → Hero` into every batch on every provider, so a name reads the same on line 1 and line 12,000. **Auto-glossary** proposes entries by scanning the project for recurring names and terms. *Supporter+.*
- **AI refiner** — an optional second pass that re-reads each line with its neighbours for context and fixes tone, pronouns and consistency. Run it on a line, a selection or a whole project, and edit its instructions yourself.
- **Custom LLM prompt** — set register, honorific policy or house style once and every batch follows it.
- **Cost estimate** before an OpenAI, Claude or DeepSeek run over 100 lines: expected tokens and USD, before a single request is sent.
- **Scan for suspicious translations** flags known failure patterns — duplicated words, smushed compounds, JSON leaking into a line, output still in Japanese — and flips them to *Failed* so you can retry just those on another provider.
- **Run summary** afterwards: how many lines came from memory versus the provider, what that saved, glossary substitutions applied, and what failed.
- **Re-scan source** when a game updates: new lines merge in, your existing translations stay, and your exclusion filters are re-applied to whatever is new.
- **Translation memory** caches every JP → target pair across all your projects, so a line you have already translated once never costs a provider call again — and your hand-fixed wording carries forward. *Supporter+.*

➡️ **Every feature and the tier it needs: [docs/features.md](docs/features.md)**

---

## Image translation, save editing and cheat menus

### 🖼️ Image Studio — the text painted into the artwork

Title screens, *New Game* buttons, HUD labels, a CG stamp: words that are pixels rather than strings, which no text extractor can reach.

Detect every text area on an image and read it in one click. Paint over the original lettering and the art underneath is **rebuilt**, not covered with a coloured patch. Typeset your translation with real fonts — size and auto-fit, weight, alignment, outline, shadow, colour, vertical Japanese — then bake it back under the original filename so the game simply loads it — and on folder-based engines the untouched original is kept beside it. You can also export a page to Photoshop, redraw it there and import it straight back; it returns in the game's own format, so a Kirikiri `.tlg` goes back as a `.tlg`.

Works on RPG Maker MV/MZ (encrypted `.rpgmvp` included), Kirikiri XP3/TLG, NScripter archives, Ren'Py loose art and `.rpa`, Electron `app.asar`, and any engine that keeps its images in ordinary folders.

*Free opens the Studio read-only — browse, zoom and read. Editing and baking come with Supporter.* → **[How image translation works](https://runetranslate.com/image-translation)**

### 💾 Save editor — free

Drag a save file in and fix it instead of replaying. Gold, party levels, HP/MP/EXP, variables, switches and inventory for RPG Maker MV (`.rpgsave`) and MZ (`.rmmzsave`), plus the Ruby generation (`.rxdata`, `.rvdata`, `.rvdata2`), RPG Maker 2000/2003 (`.lsd`), Ren'Py (`.save`) and TyranoBuilder (`.sav`). Variable and switch names are read from the game itself — and can be translated, so you know what you are editing. Every change autosaves and the original is backed up on the first edit. → **[Save editor](https://runetranslate.com/save-editor)**

### 🎲 Cheat Mode — free

Point it at an RPG Maker MV/MZ or Ren'Py game folder and it injects a hotkey-toggled in-game cheat menu, in place, with no external trainer and no memory editor: 1000 gold, godmode, full heal, one-hit kill, no random encounters, walk through walls. For Ren'Py it enables the built-in developer console. Offline single-player only, and one click removes it cleanly. *(The Variables and Switches tabs, give-all-items, max stats and instant win come with a paid plan.)* → **[Cheat Mode](https://runetranslate.com/cheat-mode)**

### 🩺 Game diagnosis — free

When a translated build will not start, the diagnosis page tells you why in plain words instead of leaving you to guess: it checks the game folder, what the export actually delivered, fonts and encoding, translation coverage, the game's own crash log, and the individual lines whose shape has broken builds before. It can then export a **safe-mode build** that reverts only the risky lines. If that works but you still do not know which line was at fault, a guided hunt narrows it down — it builds a trial version, you say whether it ran, and the next trial follows from your answer, usually in ten to fourteen rounds. *(Diagnosis and the safe-mode build are free; the guided hunt is a Supporter feature.)*

### 📦 Share your work — free

Export your translations as a compact `.rtpatch` another user applies in one click, or as an `.xlsx` you can edit in Excel or Google Sheets and hand to a translator. **No game files are ever included** — only your text. *(Free accounts get one export and one import every three days; paid plans are unlimited.)* → **[How to make a translation patch](https://runetranslate.com/blog/how-to-make-a-translation-patch)**

### 🧑‍💻 Developer interchange — bring your own strings

Making your own game? Import CSV, JSON, PO (gettext) or XLIFF, choose a source language and as many targets as you like, and get one auto-translated project per language — then export each back in the same format with your ids and keys intact, ready to drop into the build. Works for any engine, including ones RuneTranslate has never heard of. *Developer plan.* → **[Translate your own game strings](https://runetranslate.com/blog/translate-your-own-game-strings)**

### 🤖 AI Connections — Claude Desktop, inside your project

Connect Claude Desktop to RuneTranslate over the open MCP standard and just talk to it: *"find the untranslated lines"*, *"look up this character's official name"*, *"translate the rest and keep the honorifics."* Claude researches the game with its own web search and writes results straight back into your project. One click installs the extension; the link is local, token-guarded, and off until you turn it on. Browsing is free; the write and run tools come with Supporter. → **[AI Connections](https://runetranslate.com/blog/ai-connections-claude-desktop)**

---

## Collaborative and overnight translation

**🤝 Live collaborative projects.** Translate a game with your team like a shared document. The host shares an invite code, everyone works the same line list, and edits appear for the others within seconds. Live presence shows who is online, the line each person is editing and the rows they have selected; every line carries a *translated by* credit. Any member with their own copy of the game can export the finished build. *Hosting needs Supporter — **joining and translating is free for everyone**.* → **[Collaborative translation](https://runetranslate.com/blog/collaborative-translation)**

**🌙 Overnight queue.** Line up several games, press start, walk away. RuneTranslate works through them back to back, optionally running the AI refiner on each as it finishes. A failure is noted and the queue moves on, your PC is kept awake for the batch, and a notification tells you when it is done. *Supporter.*

**🔀 Bring your own proxies.** Google and free DeepL limit by IP address, not by account, so one address caps a whole-game run. Paste your own HTTP/HTTPS or SOCKS proxies, test them for latency and real exit IP, and requests rotate automatically — a proxy that gets limited cools down and steps aside. RuneTranslate never supplies proxies; yours stay encrypted on your PC, and only translation traffic is routed through them. *Pro.* → **[Translate with your own proxies](https://runetranslate.com/blog/translate-with-your-own-proxies)**

---

## Pricing

**Free is a speed lane, not a feature paywall.** Every engine, every provider, every language and the whole editor are unlocked without paying — plus the save editor, Cheat Mode's core cheats and the AI refiner.

| | **Free** | **Supporter** | **Pro** | **Developer** |
|---|---|---|---|---|
| | $0 | $3 / month | $5 / month | [contact us](mailto:runetranslate@gmail.com) |
| All 17 engines & 35 languages | ✅ | ✅ | ✅ | ✅ |
| All 10 providers | ✅ | ✅ | ✅ | ✅ |
| Full editor, AI refiner, save editor, Cheat Mode core | ✅ | ✅ | ✅ | ✅ |
| Join a collaborative project | ✅ | ✅ | ✅ | ✅ |
| Translation speed | throttled | full | full | full |
| Projects at once | 1 | 10 | 30 | 100 |
| Translation memory, glossary, provider routing | — | ✅ | ✅ | ✅ |
| Overnight queue | — | 10 games | 30 games | 50 games |
| Host collaborative projects | — | ✅ | ✅ | ✅ |
| Image Studio | read-only | editor | editor, larger quota | editor, largest quota |
| Animated scene themes | — | — | ✅ | ✅ |
| Your own translation proxies | — | — | ✅ | ✅ |
| Bulk CSV / JSON / PO / XLIFF | — | — | — | ✅ |

**What "throttled" actually means:** on the free tier RuneTranslate sends fewer requests in parallel, halves the batch size, and pauses briefly between batches; on an exceptionally heavy day a free account can also be capped on how many runs it starts. Measured, the speed difference works out at **roughly twice the wall-clock time on the AI providers, and less than that on the free scrapers**, whose speed is set by the endpoint rather than by us. The **quality is identical** — same provider, same model, same prompt, same result. A banner above the progress bar explains it while a run is going.

Translations you have already made stay yours. Project files live on your disk, exported builds are standalone folders that run with the app closed, and nothing expires or phones home to keep a finished translation working.

➡️ **Every feature, and the tier it needs: [docs/features.md](docs/features.md)** · **[Support the project on Patreon](https://www.patreon.com/cw/runetranslate/membership)**

---

## RuneTranslate vs Translator++, MTool, Sugoi Toolkit and XUnity.AutoTranslator

|  | Approach | What you are left with |
|---|---|---|
| **RuneTranslate** | Patches the game's files | A translated build you keep, play offline and can share as a patch |
| **Translator++** | Patches the game's files | A translated build. Open source (GPL-3.0), with its own editor |
| **MTool** | Hooks the running game | A live session. Nothing is written to the game |
| **Sugoi Toolkit** | Bundled offline MT engine + hook | Mostly a live session; the value is the offline model |
| **XUnity.AutoTranslator** | Hooks Unity at runtime | A live session, Unity only |
| **Textractor** | Hooks the text as the engine draws it | Extracted text for another tool to translate |
| **Translumo** | Screen OCR overlay | An overlay, on any game — and a fresh chance to misread every line |

Hooks and OCR earn their place: they are the only options for a game nothing can unpack, and they get you reading within minutes. But a hook stops matching when the engine updates, OCR turns a misread character into a confidently wrong sentence, and neither one leaves you with a game. RuneTranslate reads the files, so the result is a build — no companion process, no pause before every line, and something you can hand to a friend.

➡️ **The full comparison, tool by tool: [docs/comparison.md](docs/comparison.md)**

Head to head, in detail: **[vs Translator++](https://runetranslate.com/compare/translator-plus-plus)** · **[vs MTool](https://runetranslate.com/compare/mtool)** · **[vs Sugoi Toolkit](https://runetranslate.com/compare/sugoi-toolkit)** · **[vs XUnity.AutoTranslator](https://runetranslate.com/compare/xunity-autotranslator)** · **[vs Textractor](https://runetranslate.com/compare/textractor)** · **[vs Translumo](https://runetranslate.com/compare/translumo)**

---

## Frequently asked questions

### Is RuneTranslate a rune translator?

No. Despite the name, RuneTranslate has nothing to do with Norse runes, the Elder Futhark alphabet or Viking inscriptions. It is a Windows desktop app that translates **video games** — it reads a game's own data files, translates the text inside them, and writes back a playable build in your language.

### Is RuneTranslate safe?

The installer is not code-signed, so Windows SmartScreen shows an "unrecognised app" warning the first time you run it, and some antivirus engines flag unsigned installers on reputation alone. That warning is about the missing signature, not about anything found in the file. A SHA-256 checksum is published with every release so you can verify what you downloaded, and **the only place to get it is [runetranslate.com/download](https://runetranslate.com/download)** — no installer is distributed from this repository, and anything calling itself RuneTranslate anywhere else is not ours.

What it does on your disk: it reads your game's files and writes the translated build to a separate output folder you choose, so the original game folder is left alone. The one exception is Cheat Mode, which modifies a game in place after you point it at that folder deliberately, and which has a one-click Remove.

What it does on the network: signs you in with Patreon, sends the lines you are translating to the provider *you* pick (or to nothing at all, if you use a local model through Ollama or LM Studio), and checks for updates. Your games are never uploaded — only the text lines being translated, and only to the provider you chose.

The app itself is closed-source; this repository is documentation, not the build. If that is a dealbreaker for you, that is a fair call to make.

### Is RuneTranslate free?

Yes. Every engine, every provider, every language, the full editor, the AI refiner, the save editor and Cheat Mode's core cheats are unlocked with no pledge. There is no paid-only engine and no paid-only language. What paid buys is throughput and convenience: full-speed translation, more projects at once, translation memory, a glossary, provider routing, the overnight queue and collaborative hosting.

### Do I need an account?

Yes — the app signs in with Patreon on first launch and there is no anonymous mode. Signing in is free and takes one click; you do not need to pledge anything. After that first sign-in your sign-in is verified on your own machine, so you can keep working with no connection — it re-checks about once a day.

### Do I need an API key to translate a game?

No. Five providers need no key and no account — free Google Translate, two free DeepL routes, on-device Gemini Nano, and a local model through Ollama or LM Studio, which runs fully offline with no per-token cost. Keys are only for DeepL's official API, OpenAI, Anthropic, DeepSeek or an OpenAI-compatible endpoint, if you want those.

### What do I get at the end — a patch, or a copy of the game?

Whichever the engine can load, written into an output folder you choose. Almost every engine gets a full translated copy of the game folder that you run directly — with the engine's own override route used inside that copy where it has one, so Kirikiri gets loose files plus a `patch.xp3` and Ren'Py gets translation files written into the copied `game/` folder. Unreal is the one exception: it ships a small `_P.pak` you drop into `Content/Paks`, so a 60 GB game is not duplicated. Either way it is a standalone build you keep and play offline.

### Will it damage my game?

No. Translating never writes to your game folder — export goes to a separate folder you pick, so undoing it means deleting that folder, and the app warns you before exporting into a folder inside the game's own folder, or over your saves. The one feature that modifies a game in place is Cheat Mode, which you point at a folder deliberately and which has a one-click Remove.

### How long does a whole game take?

Usually one sitting. A short visual novel of a few thousand lines takes minutes on the free routes. A dense RPG of 30,000–100,000 lines runs anywhere from twenty minutes to a few hours, depending on the provider, how much it will accept in parallel, and your tier. Runs resume where they stopped, translation memory skips anything you have translated before, and the overnight queue can chain several games while you sleep.

### Does it work on games from Steam, DLsite, Fanza or itch.io?

Yes — the storefront is irrelevant, only the engine matters. If you bought it on Steam, copy the game folder out of your library first and translate the copy, so Steam's file verification does not fight you.

➡️ **The long-form FAQ: [docs/faq.md](docs/faq.md)** · **[All 69 answers at runetranslate.com/faq](https://runetranslate.com/faq)**

---

## Troubleshooting: when a translated game misbehaves

1. **Ask the app first.** The in-app diagnosis page checks the game folder, the export, fonts and encoding, coverage and the game's own crash log, then offers a safe-mode build.
2. **Search the guides** — [runetranslate.com/blog](https://runetranslate.com/blog) has an end-to-end walkthrough for most engines plus troubleshooting write-ups.
3. **Report it from inside the app.** *Support* files a real threaded ticket you get a reply in, with screenshots or a `.rtpatch` attached (paste a screenshot straight in with Ctrl+V). Free on every tier.
4. **[Ask on Discord](https://discord.gg/ZtsfZu7YsW)** — the fastest route for "has anyone translated this game before?"

The usual suspects, each with a fix: [the translated game will not start](docs/troubleshooting.md#the-translated-game-will-not-start-crash-or-black-screen-on-launch) · [text shows as boxes or question marks](docs/troubleshooting.md#text-shows-as-boxes-question-marks-or-garbage-tofu-mojibake) · [the game is still in Japanese after export](docs/troubleshooting.md#the-game-is-still-in-japanese-after-export) · [the engine was not detected](docs/troubleshooting.md#the-engine-was-not-detected) · [a rate limit stopped the run](docs/troubleshooting.md#translation-is-slow-or-stops-with-a-rate-limit)

➡️ **All of them: [docs/troubleshooting.md](docs/troubleshooting.md)**

---

## Links and community

| | |
|---|---|
| 🌐 **Website** | [runetranslate.com](https://runetranslate.com) |
| ⬇️ **Download** | [runetranslate.com/download](https://runetranslate.com/download) |
| 🎮 **Engines** | [runetranslate.com/engines](https://runetranslate.com/engines) |
| 📖 **Guides** | [runetranslate.com/blog](https://runetranslate.com/blog) |
| ❓ **FAQ** | [runetranslate.com/faq](https://runetranslate.com/faq) |
| ⚖️ **Compare** | [runetranslate.com/compare](https://runetranslate.com/compare) |
| 📝 **Changelog** | [runetranslate.com/changelog](https://runetranslate.com/changelog) |
| 💬 **Discord** | [discord.gg/ZtsfZu7YsW](https://discord.gg/ZtsfZu7YsW) |
| ❤️ **Patreon** | [patreon.com/cw/runetranslate](https://www.patreon.com/cw/runetranslate) |
| ▶️ **YouTube** | [@RuneTranslate](https://www.youtube.com/@RuneTranslate) |
| ✉️ **Email** | [runetranslate@gmail.com](mailto:runetranslate@gmail.com) |

### In this repository

This repository is RuneTranslate's public information hub — the app itself is closed-source and distributed from [runetranslate.com/download](https://runetranslate.com/download).

- **[docs/engines.md](docs/engines.md)** — every supported engine and format, in detail
- **[docs/file-formats.md](docs/file-formats.md)** — what `.xp3`, `.wolf`, `.rpa`, `.locres`, `.ypf` and twenty other extensions are
- **[docs/features.md](docs/features.md)** — the complete feature list, and which tier each one needs
- **[docs/comparison.md](docs/comparison.md)** — RuneTranslate against the other Japanese-game translation tools
- **[docs/faq.md](docs/faq.md)** — the long-form FAQ
- **[docs/troubleshooting.md](docs/troubleshooting.md)** — when a translated game misbehaves
- **[SUPPORT.md](SUPPORT.md)** — how to get help · **[SECURITY.md](SECURITY.md)** — reporting a vulnerability

---

<div align="center">

### [⬇️ Download RuneTranslate for Windows](https://runetranslate.com/download)

<sub>
<b>Engines:</b>
<a href="docs/engines.md#rpg-maker-mv--mz">RPG Maker MV / MZ</a> ·
<a href="docs/engines.md#rpg-maker-xp--vx--vx-ace">RPG Maker XP / VX / VX Ace</a> ·
<a href="docs/engines.md#renpy">Ren'Py</a> ·
<a href="docs/engines.md#kirikiri--kag">Kirikiri / KAG</a> ·
<a href="docs/engines.md#wolf-rpg-editor">Wolf RPG</a> ·
<a href="docs/engines.md#tyranobuilder--tyranoscript">TyranoBuilder</a> ·
<a href="docs/engines.md#electron-visual-novels">Electron VN</a> ·
<a href="docs/engines.md#unity">Unity</a> ·
<a href="docs/engines.md#unreal-engine-4--5">Unreal Engine</a> ·
<a href="docs/engines.md#godot-3x--4x">Godot</a> ·
<a href="docs/engines.md#rpg-developer-bakin">RPG Developer Bakin</a> ·
<a href="docs/engines.md#srpg-studio">SRPG Studio</a> ·
<a href="docs/engines.md#nscripter--onscripter">NScripter / ONScripter</a> ·
<a href="docs/engines.md#artemis-mikage">Artemis</a> ·
<a href="docs/engines.md#yu-ris">YU-RIS</a> ·
<a href="docs/engines.md#alicesoft-system-3x--4">AliceSoft System</a> ·
<a href="docs/engines.md#livemaker--livenovel">LiveMaker</a> ·
<a href="docs/engines.md#gettext-po--mo">gettext</a>
</sub>

<sub>RuneTranslate is an independent tool and is not affiliated with, endorsed by, or connected to any game engine vendor or translation provider. Engine and product names are the trademarks of their respective owners.</sub>

</div>
