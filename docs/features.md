# Every feature, and the tier it needs

**[← Back to the README](../README.md)** · **[Download](https://runetranslate.com/download)** · **[Pricing on Patreon](https://www.patreon.com/cw/runetranslate/membership)**

The short version of RuneTranslate's pricing: **free is a speed lane, not a feature paywall.** Every game engine, every translation provider, every target language, the whole editor, the AI refiner, the save editor and the core of Cheat Mode are unlocked without paying anything. Paid plans buy throughput and convenience.

This page lists everything, with the minimum tier next to it.

- **Free** — signed in with Patreon, no pledge
- **Supporter** — $3 / month
- **Pro** — $5 / month, everything in Supporter plus the Pro rows
- **Developer** — [email us](mailto:runetranslate@gmail.com), everything in Pro plus the Developer rows

---

## Contents

- [Translating](#translating)
- [The editor](#the-editor)
- [Quality tools](#quality-tools)
- [Image text](#image-text)
- [Beyond translation](#beyond-translation)
- [Teams and automation](#teams-and-automation)
- [The app itself](#the-app-itself)
- [Limits at a glance](#limits-at-a-glance)

---

## Translating

| Feature | Tier | What it is |
|---|---|---|
| **All 17 engines and formats** | Free | No engine is paid-only. [Full list](engines.md) |
| **All 10 translation providers** | Free | No provider is paid-only either. Five need no API key at all — four free cloud routes plus a local model on your own PC |
| **35 source and target languages** | Free | Any of the 35 can be the source; Japanese is only the default |
| **Select files to translate** | Free | Tick exactly which of the game's files to include, with a per-file string count, so a test run costs a few hundred lines instead of the whole game |
| **Cost estimate before a run** | Free | On OpenAI, Anthropic or DeepSeek runs over 100 lines, expected tokens and USD are shown before anything is sent |
| **Live progress and ETA** | Free | A real progress bar with a cumulative-average ETA, plus a finish notification and chime |
| **Resume and retry** | Free | Runs pick up where they stopped; failed lines can be retried on a different provider without redoing the rest |
| **Full-speed translation** | Supporter | Free runs with fewer parallel requests, half the batch size and a short pause between batches — measured at roughly **2× the wall-clock time on AI providers**, and less on the free scrapers. Quality is identical at every tier |
| **Provider routing** | Supporter | Split a run into two lanes automatically: short strings (item names, "Yes"/"No", labels) to a cheap or free engine, long dialogue to your premium one. Both lanes run in parallel, and on most games the cheap lane carries the larger share of the line count |
| **Translation memory** | Supporter | Every JP → target pair cached across all your projects, synced to your account, so a repeated line never costs a provider call twice — and your hand-fixed wording carries forward. CSV import/export, and a compaction tool |
| **Your own proxies** | Pro | Google and free DeepL limit by IP address, not by account. Route the free engines through your own HTTP/HTTPS or SOCKS proxies, test each one's latency and real exit IP, and let requests rotate automatically. RuneTranslate never supplies proxies. [Guide](https://runetranslate.com/blog/translate-with-your-own-proxies) |

---

## The editor

| Feature | Tier | What it is |
|---|---|---|
| **The line table** | Free | Every extracted line, grouped by source file, filtered by status (pending / translated / edited / failed / excluded), edited inline with autosave. Stays responsive at tens of thousands of lines |
| **Find and replace** | Free | Ctrl+F / Ctrl+H across the source column, the translation column or a single file, with case-sensitive and full-regex modes, reporting exactly how many lines changed |
| **Bulk actions** | Free | Right-click a row, a whole file or a drag-selected block |
| **Regex exclusion filters** | Free | Keep asset paths, variable keys and engine plumbing out of a run. Excluded lines become red opt-in rows — nothing is deleted, and you can force-translate one when the filter was wrong. [Guide](https://runetranslate.com/blog/exclude-lines-with-regex-filters) |
| **Regex rule library** | Free | Star a pattern to keep it. Saved rules live in an account-level library you can search and tag by engine, so you never retype one. Unlimited and local on every tier |
| **Rule library cloud sync** | Supporter | The same library on every PC you sign in on, plus a web panel |
| **Re-scan source** | Free | When a game updates, re-scan: new lines merge in, your translations stay, and your exclusion filters are re-applied to the new lines automatically |
| **Extraction report** | Free | After a scan, exactly which files were found but not used, and why — so missing dialogue is a question with an answer |
| **Reset to source** | Free | Any line reverts to the text it was extracted from, which is stored in the project at creation time. Reset then export gives you the original game text back |
| **Export progress and summary** | Free | A live overlay while the build is written, then a panel with the count and a button to the folder — plus guard rails that warn before exporting into the game's own folder or over your saves |

---

## Quality tools

| Feature | Tier | What it is |
|---|---|---|
| **AI refiner** | Free | An optional second AI pass that re-reads each line with its neighbours for context and improves tone, pronouns and consistency. Choose "polish what is there" or "re-check against the original and keep whichever is more faithful" — per line, per selection, or for a whole run. You can edit its instructions. [Guide](https://runetranslate.com/blog/ai-translation-refiner) |
| **Custom LLM prompt** | Free | Rewrite the system prompt the AI providers receive, with a token for the target language, so register, honorific policy or house style is set once and every batch follows it |
| **Scan for suspicious translations** | Free | One click flags known failure patterns — duplicated words, smushed compounds, JSON metadata leaking into a line, output still in Japanese, a one-word answer to a long sentence — and flips them to *Failed* so you can retry only those. Fully reversible |
| **Run summary** | Free | The receipt: how many lines came from memory versus the provider, what that saved, glossary substitutions applied, how many the refiner improved, what failed |
| **Glossary** | Supporter | Force `勇者 → Hero` into every batch on every provider, so a character or place name reads the same on line 1 and line 12,000. CSV import/export. [Guide](https://runetranslate.com/blog/translation-glossary-101) |
| **Auto-glossary** | Supporter | Scans a project for recurring names and terms — katakana names, speaker labels, repeated compounds — and proposes a glossary you tick, edit and merge in one pass |

---

## Image text

The **Image Studio** is for the Japanese painted into a game's artwork — title screens, *New Game* buttons, HUD labels, a CG stamp. No text extractor can reach those, because they are pixels rather than strings. → **[How it works](https://runetranslate.com/image-translation)**

| Feature | Tier | What it is |
|---|---|---|
| **Open and read** | Free | Browse the game's artwork, pan and zoom, read existing work. This is the one place free is *read-only* rather than throttled — every edit is refused |
| **Detect and recognize** | Supporter | One click finds every text area on a page and reads it, grouping the lines of a balloon into one block. Anything it misses you can box by hand, and any single box can be re-read on its own |
| **Translate the boxes** | Supporter | Recognized text goes through the same provider as your dialogue and lands in the editor, where you can rewrite it to fit the space it has |
| **Clean** | Supporter | Paint over the original lettering and the art underneath is rebuilt — a real background, not a coloured patch |
| **Typeset** | Supporter | Font, size with auto-fit, weight, alignment, outline, shadow, colour, per box, vertical Japanese included |
| **Bake** | Supporter | Writes the translated image under its original filename, in the game's own format, so the game just loads it. On folder-based engines the untouched original is kept beside it as `bk_<name>`; in an archive there is no loose original to keep, and your source game is untouched either way |
| **Round-trip to Photoshop** | Supporter | Export a page (or every page in the current view) as PNG — plain artwork or the finished look — redraw it anywhere, and import it back as that page's base. A Kirikiri `.tlg` goes back as a `.tlg` |
| **Higher daily quota** | Pro | Detection and background rebuilding run on RuneTranslate's own OCR service and are metered per day. Pro raises the allowance well above Supporter's; Developer raises it again |

**Engines with image support:** RPG Maker MV/MZ (encrypted `.rpgmvp` and `.png_` included — the cipher is detected, not assumed), Kirikiri XP3 with TLG, NScripter `.nsa` / `.sar`, Ren'Py loose art and `.rpa`, Electron `app.asar`, and any engine that keeps its images in ordinary folders.

---

## Beyond translation

| Feature | Tier | What it is |
|---|---|---|
| **Save editor** | Free | Drag in a save and fix it instead of replaying. Gold, party levels, HP/MP/EXP, variables, switches and inventory for RPG Maker MV `.rpgsave` and MZ `.rmmzsave`, plus `.rxdata` / `.rvdata` / `.rvdata2` (XP, VX, VX Ace), `.lsd` (RPG Maker 2000 / 2003), Ren'Py `.save` and TyranoBuilder `.sav`. Variable names are read from the game and can be translated. Autosaves, and backs up the original on the first change. [More](https://runetranslate.com/save-editor) |
| **Cheat Mode** | Free | Injects a hotkey-toggled in-game cheat menu into an RPG Maker MV/MZ or Ren'Py game folder — 1000 gold, godmode, full heal, one-hit kill, no random encounters, walk through walls; the Ren'Py developer console. Offline single-player only, removable in one click. [More](https://runetranslate.com/cheat-mode) |
| **Advanced cheats** | Supporter | The Variables and Switches tabs (list, search and set every game variable or switch live), give-all-items, max stats and level, instant battle win, and Ren'Py's live store-variable editor |
| **Game diagnosis** | Free | When a translated build will not start, this checks the game folder, what the export delivered, fonts and encoding, coverage, the game's own crash log, and the individual lines whose shape has broken builds before — then offers a **safe-mode build** that reverts only the risky ones |
| **Guided hunt** | Supporter | When safe mode works but you do not know which line broke the game, the hunt narrows it down: it builds a trial version, you say whether it ran, and the next trial follows from your answer — usually ten to fourteen rounds to name the culprit |
| **Patch export / import** | Free | Share your work as a compact `.rtpatch` another user applies in one click, or as an `.xlsx` for Excel, Google Sheets or a human translator. **No game files are ever included.** Free accounts get one export and one import every three days; paid is unlimited. [Guide](https://runetranslate.com/blog/how-to-make-a-translation-patch) |
| **AI Connections (MCP)** | Free / Supporter | Connect Claude Desktop to RuneTranslate and talk to it about your project — it can research a game with its own web search and write results back. Browsing and searching are free; the write and run tools are Supporter. Off until you turn it on, and the link is local and token-guarded. [Guide](https://runetranslate.com/blog/ai-connections-claude-desktop) |
| **Developer interchange** | Developer | Import CSV, JSON, PO (gettext) or XLIFF, pick a source language and as many targets as you like, and get one auto-translated project per language — exported back in the same format with your ids and keys intact. Works for any engine, including unsupported ones. [Guide](https://runetranslate.com/blog/translate-your-own-game-strings) |

---

## Teams and automation

| Feature | Tier | What it is |
|---|---|---|
| **Join a collaborative project** | Free | Anyone can join someone else's shared project and translate in it |
| **Host a collaborative project** | Supporter | Share an invite code and translate a game together like a shared document — everyone on the same line list, edits visible within seconds, live presence showing who is editing which line, and a *translated by* credit on every line. Any member with their own copy of the game can export the build. [Guide](https://runetranslate.com/blog/collaborative-translation) |
| **Overnight queue** | Supporter | Line up several games, press start, walk away — optionally refining each one as it finishes. A failure is noted and the queue moves on; your PC is kept awake and you get a notification at the end. Supporter queues 10 games, Pro 30, Developer 50 |

---

## The app itself

| Feature | Tier | What it is |
|---|---|---|
| **18-language interface** | Free | The whole app, including the in-app help for every settings tab, in 18 languages — with right-to-left layout for Arabic |
| **Auto-update** | Free | New versions download in the background and prompt you to restart, with a What's New panel |
| **Early access to new builds** | Supporter | When early access is on, paid supporters get each release first and everyone else after a set delay, with a countdown shown in the app |
| **Support tickets** | Free | Report a bug or ask for a feature from inside the app and get a threaded reply in the same place. Attach screenshots, spreadsheets or a `.rtpatch` — paste a screenshot straight in with Ctrl+V |
| **Moved-folder recovery** | Free | Rename or move a game folder and the project follows it, instead of failing an export with a cryptic message |
| **Discord Rich Presence** | Free | Show RuneTranslate in your Discord status. Only the engine family is ever shown — never the game or project name. Off unless you turn it on |
| **Themes** | Free / Supporter / Pro | 18 colour themes, four of them animated procedural backdrops. Light is free, most come with Supporter, three animated scene themes are Pro, and three more are bought with RT Coins |
| **RT Coins** | Supporter | Every month subscribed earns coins, and an unbroken streak earns more. Spend them on a gift month of Supporter or Pro for someone else, or on cosmetics |
| **Website account panel** | Free | Manage your tier and renewal, RT Coins and gift codes in a browser. The translation-memory and regex-rule-library panels come with Supporter, like the cloud sync they belong to |

---

## Limits at a glance

| | Free | Supporter | Pro | Developer |
|---|---|---|---|---|
| Projects at once | 1 | 10 | 30 | 100 |
| Games in the overnight queue | — | 10 | 30 | 50 |
| Translation speed | throttled (~2× slower on AI providers) | full | full | full |
| Image Studio | read-only | editor | editor, larger quota | editor, largest quota |
| Patch export / import | 1 + 1 per 3 days | unlimited | unlimited | unlimited |

Collaborative projects you host or join do not count against the project limit. Finishing a game, exporting it and deleting the project frees the slot again — and the exported build and the translations inside it are yours permanently, whatever happens to your subscription.

---

**[← Back to the README](../README.md)** · **[Engines](engines.md)** · **[Comparison](comparison.md)** · **[FAQ](faq.md)** · **[Troubleshooting](troubleshooting.md)**
