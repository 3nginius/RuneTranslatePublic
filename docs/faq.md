# Frequently asked questions

**[← Back to the README](../README.md)** · **[All 69 answers at runetranslate.com/faq](https://runetranslate.com/faq)** · **[Download](https://runetranslate.com/download)**

---

## Getting started

### What is RuneTranslate?

A Windows desktop app that translates a game by reading its own data files. It detects the engine, extracts every line of dialogue, menu text, item name and choice into an editable project, translates them through the provider you choose, and exports a **playable build** in your language. It is not an overlay and not a hook — nothing runs alongside the game afterwards.

Seventeen engines and formats are supported — sixteen game engines plus the gettext `.po` / `.mo` catalog format — and 35 languages.

### What do I need before I start?

Windows 10 or 11 (x64), the game folder, and a free Patreon sign-in. That is all. You do not need an API key, a compiler, Python, or any runtime installed first — and you do not need to know anything about the engine your game uses.

### How do I translate a game?

Four steps. Point *New project* at the game folder and let it detect the engine and count the text. Pick a target language and a provider, then press Translate and watch the progress bar. Read through the result in the editor and fix anything that reads badly. Press Export, choose an output folder, and play what lands there.

The [beginner's walkthrough](https://runetranslate.com/blog/how-to-translate-a-japanese-game-to-english) does it with screenshots.

### Do I need an account?

Yes. The app signs in with Patreon on first launch and there is no signed-out mode. Signing in is free and takes one click — no pledge required — and "free tier" means exactly that: signed in, not pledging. After the first sign-in your sign-in is verified on your own machine, so the app keeps working with no connection; it re-checks about once a day, so you do need to be online occasionally.

### How long does a whole game take?

Usually one sitting. A short visual novel of a few thousand lines is minutes on the free routes. A dense RPG of 30,000 to 100,000 lines is anywhere from twenty minutes to a few hours, depending on the provider, how many requests it accepts in parallel, and whether you are on the free throttle. Runs resume where they stopped, translation memory skips anything you have translated before, and the overnight queue can chain several games while you sleep.

---

## Cost and plans

### Is it free?

Yes, once you sign in. Every engine, every provider, every language, the whole editor, the AI refiner, the save editor and Cheat Mode's core cheats are unlocked with no pledge. There is no paid-only engine and no paid-only language.

What free gives up is throughput and convenience: translation runs slower, you keep one project at a time, the Image Studio opens read-only, and patch sharing is limited to one export and one import every three days.

### How much slower is the free tier, really?

Roughly **twice the wall-clock time on the AI providers**, and less than that on the free Google and DeepL routes, whose speed is set by the endpoint rather than by us. Free sends fewer requests in parallel, halves the batch size and pauses briefly between batches.

**Quality is identical.** Same provider, same model, same prompt, same output — the throttle only touches how fast requests go out.

*(Older RuneTranslate copy claimed "3–4× slower". That figure was never measured, and it has been retracted.)*

### What do the paid plans add?

**Supporter ($3/month)** removes the throttle and adds cloud translation memory, the glossary, provider routing, the overnight batch queue, collaborative project hosting, the full Image Studio editor, the advanced Cheat Mode tools, beta builds and 10 concurrent projects.

**Pro ($5/month)** includes everything in Supporter, plus 30 projects, animated scene themes, a larger Image Studio quota, and the bring-your-own proxy pool.

**Developer** is a superset of Pro for studios and localization teams: bulk CSV / JSON / PO / XLIFF interchange and 100 projects. It is quoted rather than listed — [email us](mailto:runetranslate@gmail.com).

### Do I have to keep paying to keep a translation I made?

No. Project files live on your own disk, exported builds are standalone folders that run with the app closed, and nothing expires or phones home to keep a finished translation working. If a subscription lapses you drop to the free tier, which still has every engine, every provider and the full editor at throttled speed.

### How many projects can I have at once?

One on free, 10 on Supporter, 30 on Pro, 100 on Developer. It counts projects sitting in your library, not games you may ever translate — finish one, export it, delete the project, and the slot is free. Collaborative projects you host or join do not count.

---

## Providers, keys and privacy

### Do I need an API key?

No. Five providers need no key and no account at all — free Google Translate, two free DeepL routes, Gemini Nano running on your own PC through Chrome, and a local model via Ollama or LM Studio, which runs fully offline with no per-token cost.

Keys are only needed if you *want* DeepL's official API, OpenAI, Anthropic, DeepSeek, or an OpenAI-compatible endpoint like OpenRouter.

### Which provider is cheapest?

Free Google Translate costs nothing and handles whole games. If you want LLM quality on a budget, DeepSeek is usually cents for an entire game, and provider routing can cut that further by sending short menu strings to a free engine while dialogue goes to the paid one. A local model costs nothing but your own electricity.

### Which provider gives the best quality?

For long Japanese dialogue, DeepL and the larger LLMs are the strong options; Claude in particular tends to hold register and tone. There is no single right answer, which is why the app lets you mix them in one run and re-translate any line on a different provider without redoing the rest. The [provider comparison](https://runetranslate.com/blog/best-providers-for-translating-japanese-games) goes through it properly.

### Does my game's text go through your servers?

No. Translation requests go from your PC straight to the provider you selected. RuneTranslate's own servers handle sign-in, updates, and the cloud features you opt into: translation memory sync, collaborative projects, and the Image Studio, which sends the image crops you are working on to our own OCR service so it can read the text and repaint the artwork behind it. Nothing else leaves your PC.

### Where are my API keys stored?

Encrypted on your own machine with Windows DPAPI, and sent only to the provider they belong to.

### Can I run it completely offline?

Almost. The first sign-in needs a connection, and the app re-checks it roughly once a day — in between, everything is verified on your own machine. Translation itself can be fully offline if you use a local model through Ollama or LM Studio, or Gemini Nano on-device. Everything in the editor, the save editor, Cheat Mode and export works offline.

---

## Results and safety

### What do I get at the end — a patch, or a copy of the game?

Whichever the engine can actually load, written into an output folder you choose.

Almost every engine gets a **full translated copy** of the game folder that you run directly — with the engine's own override route used inside that copy where it has one, so Kirikiri gets loose files plus a `patch.xp3` and Ren'Py gets translation files written into the copied `game/` folder. **Unreal is the one exception**: it ships a small `_P.pak` you drop into `Content/Paks`, so a 60 GB game is not duplicated.

### Will it damage or overwrite my game?

Translating never writes to your game folder. Extraction opens the game read-only, any unpacking happens in a workspace inside the app's own data folder, and export writes a fresh copy or a small override into a folder you select — so undoing an export means deleting that folder. The app also warns you before exporting into the game's own folder or over existing save files.

The one feature that *does* modify a game in place is Cheat Mode, which you point at a folder deliberately and which has a one-click Remove. The export guard warns you before writing into a folder inside the game's own folder, or over save files it finds. Back up anything irreplaceable anyway, and note that most engines produce a full game copy, so give the output drive room.

### Can I go back to the original text?

Yes. Every line stores the source text it was extracted from at project creation, so *Reset* followed by *Export* gives you the original game back even if you have overwritten an output folder along the way.

### Can I share a finished translation?

Yes, as a `.rtpatch` — a compact file carrying **your text only, no game files** — which another user applies in one click. You can also export to `.xlsx` for Excel, Google Sheets or a human translator, and import it back. Free accounts get one export and one import every three days.

### Is it legal to use on a game I own?

Translating a game you legally own for your own use is generally fine, and fan translation has a long history. Distributing game files is not — which is why patch export carries your text and nothing else. Respect each game's licence and the wishes of its developer, and do not redistribute anything you did not create.

---

## Languages

### Which languages can it translate into?

35, including English, Spanish, French, German, Russian, Chinese (Simplified and Traditional), Portuguese (European and Brazilian), Italian, Korean, Dutch, Polish, Turkish, Vietnamese, Arabic, Thai, Ukrainian and Mongolian. The [full list is in the README](../README.md#languages-japanese-to-english-and-34-more).

### Can it translate *from* something other than Japanese?

Yes — any of the 35 languages can be the source. Japanese is only the default because it is what most users bring. An English, Chinese or Korean game translates the same way.

### The translated text shows as boxes or question marks. Why?

That is a font problem, not a translation problem: the game ships a font with no glyphs for your language, so the engine draws a placeholder box. RuneTranslate bundles fonts for the engines where that is possible — Ren'Py targets that need Latin-Extended or Cyrillic, for instance — and for a few Japanese-charset-only engines (NScripter, Artemis, Wolf RPG) it can ship a purpose-built font that renders **Thai**. There is a [full write-up](https://runetranslate.com/blog/unity-translated-text-shows-boxes).

### Is the app itself available in my language?

The interface is translated into 18 languages, Arabic included with a right-to-left layout.

---

## Engines

### Which engines are supported?

Sixteen game engines, plus the gettext catalog format — seventeen entries in total: RPG Maker MV/MZ and XP/VX/VX Ace, Ren'Py, Kirikiri/KAG, Wolf RPG, TyranoBuilder/TyranoScript, custom Electron visual novels, Unity, Unreal Engine 4/5, Godot, RPG Developer Bakin, SRPG Studio, NScripter/ONScripter, Artemis, YU-RIS, AliceSoft System and LiveMaker. → **[details per engine](engines.md)**

### My game's engine is not on the list. What now?

Open the folder in *New project* anyway — a great many games run on a supported engine without advertising it: a custom Electron shell, a Cocos Creator build, a Unity game with an unusual folder name. If the game ships `.po` / `.mo` catalogs, or you can get CSV / JSON / XLIFF out of it, those work regardless of engine. And if it really is something new, [say so on Discord](https://discord.gg/ZtsfZu7YsW) or email `runetranslate@gmail.com` with the game and a folder listing — most of the sixteen supported engines were added because somebody did exactly that.

### Does it work on doujin, eroge and adult games?

Yes. RuneTranslate is engine-aware, not content-aware. If the game runs on a supported engine, it works regardless of theme.

### Does it work on Steam games?

If the game uses a supported engine, yes — copy the game folder out of your Steam library first and translate the copy, so Steam's file verification does not fight you.

---

## Working on a translation

### Can I edit the machine translation by hand?

That is what the editor is for. Every line is editable, searchable and filterable; find and replace works across the whole project with regex; a glossary locks names; and the AI refiner can re-read anything you are unhappy with, in context. Your edits survive re-runs and re-scans.

### What is translation memory?

A cache of every source → target pair you have ever translated, shared across all your projects. A line you have translated once never costs a provider call again, and your hand-fixed wording carries into the next game that uses the same line. Supporter and above, synced to your account.

### What is a glossary for?

Consistency. A machine translator will happily render the same character name four different ways across a long game. A glossary forces your chosen rendering into every batch on every provider, so it reads the same on line 1 and line 12,000. → [glossary guide](https://runetranslate.com/blog/translation-glossary-101)

### What is the AI refiner?

An optional second pass. It re-reads each translated line together with its neighbours, so it can see context the first pass could not, and fixes tone, pronouns and consistency. You can run it on one line, a selection, or a whole project, and you can edit the instructions it follows. Free on every tier. → [refiner guide](https://runetranslate.com/blog/ai-translation-refiner)

### Can several people work on one translation at the same time?

Yes. Live collaborative projects work like a shared document: the host shares an invite code, everyone edits the same line list, changes appear within seconds, and every line records who translated it. Hosting needs Supporter; **joining and translating is free for everyone**.

### What happens when the game gets an update?

Re-scan the source folder. New lines are merged in, your existing translations are kept, and your regex exclusion filters are re-applied to the newly found lines automatically.

### Can I use it from Claude Desktop?

Yes, over the open MCP standard. Connect Claude Desktop and talk to it about your project — it can search your lines, look things up on the web, and write translations back. Browsing is free; the write and run tools are a Supporter feature. It is off until you turn it on, and the connection is local and token-guarded. → [AI Connections](https://runetranslate.com/blog/ai-connections-claude-desktop)

---

## Platform and support

### Does it run on Linux, macOS or the Steam Deck?

There is no native Linux or macOS build, and none is planned — the games it translates are overwhelmingly Windows games. But RuneTranslate runs well on **Linux and the Steam Deck through Wine or Proton**: install the ordinary Windows version into a prefix and you get the same engines, providers, editor and export. That is a natural fit, since you are already running those games through the same compatibility layer. Most engines need nothing extra; RPG Developer Bakin additionally wants the .NET Framework in the prefix, which winetricks installs.

### Windows says the installer is unrecognised. Is it safe?

The build is not code-signed, so SmartScreen shows its "unrecognised app" warning on first run — that is a statement about a certificate, not about the file's contents. A checksum is published alongside each release so you can verify the installer you downloaded.

It is an ordinary Windows installer that puts an Electron app in your user profile: no admin rights required, no bundled toolbars, no ads, no background service left running after you close it, and anonymous usage statistics you can switch off in Settings. Always download from [runetranslate.com/download](https://runetranslate.com/download) and nowhere else.

### How do I report a bug?

From inside the app: *Support* files a real threaded ticket that the developer replies to in the same place, with screenshots or a `.rtpatch` attached. Free on every tier. Or [ask on Discord](https://discord.gg/ZtsfZu7YsW), which is faster for "has anyone translated this game before?"

### Where is the changelog?

[runetranslate.com/changelog](https://runetranslate.com/changelog) — every release, newest first, with a per-engine view of what changed.

---

**[← Back to the README](../README.md)** · **[Engines](engines.md)** · **[Features](features.md)** · **[Comparison](comparison.md)** · **[Troubleshooting](troubleshooting.md)**
