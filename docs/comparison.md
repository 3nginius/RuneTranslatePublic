# RuneTranslate vs the other Japanese game translation tools

**[← Back to the README](../README.md)** · **[Full comparison on runetranslate.com](https://runetranslate.com/compare)** · **[Download](https://runetranslate.com/download)**

If you are choosing a tool to translate a Japanese game or visual novel, the first decision is not *which app* — it is **which of the three approaches** you want. Everything else follows from that, and half the tools people argue about are not solving the same problem.

---

## Contents

- [The three approaches](#the-three-approaches)
- [Comparison table](#comparison-table-runetranslate-vs-translator-mtool-sugoi-toolkit-xunityautotranslator-textractor-and-translumo)
- [Translator++ alternative](#translator-alternative--runetranslate-vs-translator)
- [MTool alternative](#mtool-alternative--runetranslate-vs-mtool)
- [Sugoi Toolkit alternative](#sugoi-toolkit-alternative--runetranslate-vs-sugoi-toolkit)
- [XUnity.AutoTranslator alternative](#xunityautotranslator-alternative--runetranslate-vs-xunityautotranslator)
- [Textractor alternative](#textractor-alternative--runetranslate-vs-textractor)
- [Translumo alternative](#translumo-alternative--runetranslate-vs-translumo)
- [What RuneTranslate does that the others do not](#what-runetranslate-does-that-the-others-do-not)
- [Which tool should I use? Straight answers](#which-tool-should-i-use-straight-answers)
- [Fairness note](#fairness-note)

---

## The three approaches

### File patchers — you end up with a translated game

A patcher opens the game's own data: RPG Maker's JSON, a Ren'Py script, a Kirikiri XP3, a Unity bundle. It pulls every translatable string into a project, you translate and edit them, and it writes the finished text back. What comes out is a **build**: you launch the exported copy and it is in your language, menus and all, with nothing running beside it and nothing to set up again tomorrow.

- **Best at:** a game you intend to actually play through, a translation you want to keep, and anything you want to share.
- **Worst at:** a game whose format nothing can open yet. If the files cannot be read, there is nothing to patch.
- **Tools:** **RuneTranslate**, Translator++.

### Runtime hooks — you end up with a translated session

A hook attaches to the running game and intercepts text as the engine draws it, translating on the fly. Nothing is written to the game.

- **Best at:** being up and reading within minutes, on a title no extraction tool has ever opened.
- **Worst at:** permanence. Nothing is saved back, and a hook built against one version of an engine quietly stops matching a newer one.
- **Tools:** MTool, XUnity.AutoTranslator, Textractor, Sugoi Hook.

### Screen OCR overlays — you end up with a live overlay

An overlay ignores the game entirely: it captures part of your display, runs optical character recognition on the pixels, translates the result and paints it back over the window.

- **Best at:** reaching text no other approach can see — emulators, browser games, a build nothing can read.
- **Worst at:** accuracy and latency. Stylised fonts, vertical text, furigana and textured backgrounds all degrade recognition, and a misread character becomes a confidently wrong sentence with nothing in the chain to catch it.
- **Tools:** Translumo, and the OCR modes built into other suites.

**RuneTranslate is a file patcher**, and that is the whole design: it is for people who want the game, not the session.

---

## Comparison table: RuneTranslate vs Translator++, MTool, Sugoi Toolkit, XUnity.AutoTranslator, Textractor and Translumo

| | Approach | Engine coverage | Result | Platform | Licence |
|---|---|---|---|---|---|
| **RuneTranslate** | File patcher | 17 engines and formats | A playable translated build you keep | Windows 10 / 11 | Proprietary (free tier, paid plans) |
| **Translator++** | File patcher | Narrower built-in set, plus a custom-parser system and RPG Maker 2000/2003 | A playable translated build | Windows 7 SP1+ | GPL-3.0-or-later |
| **MTool** | Runtime hook | RPG Maker focus | A live session | Windows 7+, Android 11+ | Proprietary |
| **Sugoi Toolkit** | Offline MT engine + hook | Varies | Mostly a live session | Windows 10+ | Mixed (NTT model licence; Sugoi Hook GPL-3.0) |
| **XUnity.AutoTranslator** | Runtime hook | Unity only | A live session | Windows (Unity games) | MIT |
| **Textractor** | Runtime hook | Engine-specific hooks | Extracted text for another tool | Windows 7+ | GPL-3.0 |
| **Translumo** | Screen OCR overlay | Any game | A live overlay | Windows 10 2004+ | Apache-2.0 |

*Competitor details verified August 2026 against each project's own site or repository. Authors: Translator++ by Dreamsavior, MTool by AdventCirno, Sugoi Toolkit by MingShiba, XUnity.AutoTranslator by bbepis, Textractor by Artikash, Translumo by ramjke (created by Danily07).*

---

## Translator++ alternative — RuneTranslate vs Translator++

The closest comparison on this page, because both tools do the same *kind* of thing: open the game's own files, put the strings in an editor, and write back a playable build. Neither reads memory at runtime and neither draws an overlay.

The difference is how far the file-level coverage reaches and who decides what is safe to translate. RuneTranslate parses **17 engines and formats itself** — Unity on both Mono and IL2CPP, Unreal 4/5, Godot, Bakin, SRPG Studio, Artemis, YU-RIS, AliceSoft, LiveMaker and the rest — and builds the filters that keep scripts, tags, asset paths and lookup keys *out* of the translation into the extractor, then runs them again at export. It also brings ten translation providers, an [Image Studio](https://runetranslate.com/image-translation) for text painted into artwork, a save editor, Cheat Mode, translation memory and live collaboration in the same app.

Translator++ is free and open source (GPL-3.0-or-later), and it holds two places of its own: **RPG Maker 2000 and 2003**, which RuneTranslate has no adapter for, and formats nobody has written a parser for at all, because its Custom Parser lets you define one yourself. Plenty of people keep both.

→ [The detailed head-to-head](https://runetranslate.com/compare/translator-plus-plus)

## MTool alternative — RuneTranslate vs MTool

MTool hooks the running game, so it is quick to start and leaves nothing behind. RuneTranslate patches the files, so it takes a few minutes longer up front and hands you a build you can replay, back up and share as a patch — with an editor for fixing what the machine got wrong, a glossary that keeps character names consistent across a whole game, and 17 engines rather than an RPG Maker focus.

If you want to read one game tonight and never think about it again, a hook is a reasonable answer. If you want the translation to exist tomorrow, it has to be written to disk.

→ [The detailed head-to-head](https://runetranslate.com/compare/mtool)

## Sugoi Toolkit alternative — RuneTranslate vs Sugoi Toolkit

Sugoi Toolkit's real value is its bundled offline machine-translation model — you get translation with no API key, no account and no connection. RuneTranslate reaches the same place by a different road: **four providers need no key or account** (free Google, two free DeepL routes, and on-device Gemini Nano), and a local model through Ollama or LM Studio is fully offline with no per-token cost and a far larger choice of models.

Where they genuinely differ is the output. Sugoi is primarily a translation *engine* plus a hook; RuneTranslate is a patcher with an editor around it, so the result is a build with your corrections in it rather than a session.

→ [The detailed head-to-head](https://runetranslate.com/compare/sugoi-toolkit)

## XUnity.AutoTranslator alternative — RuneTranslate vs XUnity.AutoTranslator

XUnity.AutoTranslator is the standard answer for Unity games and it is genuinely good at what it does: MIT-licensed, widely used, and able to translate text that only exists at runtime — including strings compiled into an IL2CPP binary, which no file patcher can reach.

RuneTranslate takes Unity at the file level instead: `TextAsset` and `MonoBehaviour` strings, localization tables, `StreamingAssets` scripts, encrypted Addressable bundles and Mono `Assembly-CSharp.dll` literals, with identifier and lookup-key shapes excluded structurally so a translated control id cannot hang the game on a loading screen. What you get is a translated copy of the game rather than a plugin that has to keep running — and the same app handles the other sixteen engines and formats when your next game is not Unity.

→ [The detailed head-to-head](https://runetranslate.com/compare/xunity-autotranslator)

## Textractor alternative — RuneTranslate vs Textractor

Textractor is a text *hooker*: it captures the strings an engine is drawing and hands them to something else to translate. It is excellent at reaching a visual novel nothing can unpack, and it is GPL-3.0 open source.

RuneTranslate is the other end of the same problem. It opens Kirikiri, NScripter, Artemis, YU-RIS, AliceSoft, LiveMaker, TyranoBuilder and custom Electron shells directly, so the text comes out into an editor, gets a glossary and a second AI pass, and goes back in as a build. No companion window, no per-session setup, and something you can hand to a friend.

→ [The detailed head-to-head](https://runetranslate.com/compare/textractor)

## Translumo alternative — RuneTranslate vs Translumo

Translumo reads the screen, which makes it the one approach with no compatibility list at all — emulators, browser games, anything that puts pixels on a monitor. That is a real capability and nothing here replaces it.

The cost is that every line goes through recognition first, so stylised fonts, vertical Japanese, furigana and textured backgrounds all degrade the result, a misread character becomes a confidently wrong sentence, and there is a pause before each line. RuneTranslate reads the text as the game stores it, so there is nothing to misrecognise — and for artwork specifically, the Image Studio does the OCR *once*, lets you correct it, and bakes the result into the picture permanently rather than re-recognising it every time you play.

→ [The detailed head-to-head](https://runetranslate.com/compare/translumo)

---

## What RuneTranslate does that the others do not

**Seventeen engines and formats in one app.** RPG Maker MV/MZ *and* the Ruby XP/VX/Ace generation, Ren'Py, Kirikiri/KAG, Wolf RPG 2.x and 3.x, TyranoBuilder, Electron and Cocos Creator shells, Unity on both Mono and IL2CPP, Unreal 4/5, Godot, Bakin, SRPG Studio, NScripter/ONScripter, Artemis, YU-RIS, AliceSoft System, LiveMaker and gettext catalogs. Most tools cover one engine family well; this covers the shelf. → **[the full list](engines.md)**

**Ten translation providers, mixed in one run.** DeepL, OpenAI, Anthropic Claude, DeepSeek, an OpenAI-compatible endpoint, free Google, two free DeepL routes, on-device Gemini Nano, and your own local model. Provider routing can send menu strings to a free engine and dialogue to a premium one in the same run.

**An editor, not just a converter.** Regex filters, a saved rule library, a glossary that locks character names on every provider, an AI refiner that re-reads lines in context, a suspicious-translation scanner, and translation memory so you never pay to translate the same line twice.

**Text inside artwork.** The [Image Studio](https://runetranslate.com/image-translation) detects the Japanese painted into title screens and buttons, rebuilds the art underneath, typesets your translation with real fonts, and bakes it back in the game's own image format. Hooks and OCR overlays cannot touch this; most patchers do not try.

**A team can work on one game at once.** Live collaborative projects, with presence and per-line credit. Joining is free.

**35 languages, in both directions.** Not just Japanese to English — and regional variants are separate, correct choices rather than a coin flip between European and Brazilian Portuguese.

**And it is genuinely free to use.** Every engine, every provider, every language, the whole editor, the save editor, Cheat Mode and the AI refiner are unlocked without paying. Translation memory, the glossary and provider routing come with Supporter, and the paid plans buy speed and convenience.

---

## Which tool should I use? Straight answers

### I want to play a Japanese RPG Maker game in English tonight

Either approach works. RuneTranslate takes a few extra minutes up front and leaves you with a build you can replay, back up and hand to a friend. A hook has you reading sooner and leaves nothing behind.

### I want to publish a fan translation

A patcher, and only a patcher. You need an editable project, consistency tooling and a shareable output — RuneTranslate exports a `.rtpatch` that carries your text and no game files.

### My Unity game will not open in anything else

Try RuneTranslate first: it reads Unity's externalized text on both Mono and IL2CPP builds, including localization tables and encrypted Addressable bundles. On Mono builds it also reads the strings compiled into `Assembly-CSharp.dll`. Only IL2CPP-compiled managed strings are out of reach — that is the one case where a runtime hook is the right tool.

### It is a visual novel with a weird engine

Kirikiri, NScripter, Artemis, YU-RIS, AliceSoft, LiveMaker, TyranoBuilder and custom Electron shells are all covered. Open the folder and let detection answer before assuming it is unsupported.

### It is an emulator, a browser game, or something with no files I can reach

Screen OCR. Nothing that reads files can help you, and that is not a criticism of either approach.

### My backlog is a mix of engines

RuneTranslate — one app covers seventeen engines and formats and works out which one you handed it, including every RPG Maker from XP and VX Ace through MV and MZ. One gap, stated plainly: RPG Maker **2000 and 2003** game text, where Translator++ has a dedicated parser and RuneTranslate has only save-file editing.

### My text is in a format nobody has written a parser for

If you can get the strings out as CSV, JSON, PO or XLIFF, RuneTranslate's Developer interchange tab translates them and gives them back in the same format with ids intact — which covers most engines that expose their text at all. If you cannot get them out in the first place, Translator++'s Custom Parser lets you define a reader yourself.

### I want the translation to keep working after the game updates

Re-scan the source folder: new lines merge in, your existing translations stay, and your filters re-apply. A hook has to be re-matched against the new build by whoever maintains it.

---

## Fairness note

Every tool above is a real, useful project, and several are free and open source. Runtime hooks and OCR reach games nothing else can, and for a one-evening read-through they can be the faster answer. This page is written by the people who make RuneTranslate and argues for it — but the facts about the other tools are checked, and the situations where another approach is the better fit are named above rather than hidden.

**Head to head, in detail:** [vs Translator++](https://runetranslate.com/compare/translator-plus-plus) · [vs MTool](https://runetranslate.com/compare/mtool) · [vs Sugoi Toolkit](https://runetranslate.com/compare/sugoi-toolkit) · [vs XUnity.AutoTranslator](https://runetranslate.com/compare/xunity-autotranslator) · [vs Textractor](https://runetranslate.com/compare/textractor) · [vs Translumo](https://runetranslate.com/compare/translumo)

---

**[← Back to the README](../README.md)** · **[Engines](engines.md)** · **[Features](features.md)** · **[File formats](file-formats.md)** · **[FAQ](faq.md)** · **[Troubleshooting](troubleshooting.md)**
