# Troubleshooting

**[← Back to the README](../README.md)** · **[Guides](https://runetranslate.com/blog)** · **[Ask on Discord](https://discord.gg/ZtsfZu7YsW)**

Common problems when translating a Japanese game, and what actually fixes them.

**Before anything else: open the diagnosis page in the app.** It checks the game folder, what the export delivered, fonts and encoding, translation coverage, the game's own crash log, and the individual lines whose shape has broken builds before — then offers a *safe-mode build* that reverts only the risky ones. It is free on every tier, and it answers most of what is on this page without you having to guess which section applies.

---

## Contents

- [The translated game will not start](#the-translated-game-will-not-start-crash-or-black-screen-on-launch)
- [Text shows as boxes, question marks or garbage](#text-shows-as-boxes-question-marks-or-garbage-tofu-mojibake)
- [The game is still in Japanese after export](#the-game-is-still-in-japanese-after-export)
- [Some lines are still Japanese, but most are fine](#some-lines-are-still-japanese-but-most-are-fine)
- [The engine was not detected](#the-engine-was-not-detected)
- [The export failed](#the-export-failed)
- [Translation is slow, or stops with a rate limit](#translation-is-slow-or-stops-with-a-rate-limit)
- [A line came back unchanged, or obviously wrong](#a-line-came-back-unchanged-or-obviously-wrong)
- [A Unity game hangs on a loading screen](#a-unity-game-hangs-on-a-loading-screen)
- [Windows SmartScreen warns about the installer](#windows-smartscreen-warns-about-the-installer)
- [I lost my save files](#i-lost-my-save-files)
- [Still stuck](#still-stuck)

---

## The translated game will not start (crash or black screen on launch)

Almost always one bad line rather than a broken export. Some engines store dialogue in a structure where the *shape* of the text matters — a control code, a line count, a length prefix — and a translation that changes that shape crashes the game before it draws anything.

**Do this:**

1. Open the **diagnosis page** in the app and run it on the project. It reads the game's own crash log where there is one and flags the lines whose shape looks risky.
2. Export a **safe-mode build**, which reverts only those lines and keeps everything else translated. If that starts, you have confirmed the cause.
3. If safe mode works but you want the full translation back, run the **guided hunt** (Supporter): it builds a trial version, you say whether it ran, and the next trial narrows the range — usually ten to fourteen rounds to name the exact line.
4. Fix or exclude the culprit and re-export.

**Check first, because they are quick:** did you export into the game's own folder (export somewhere fresh instead), and is the output path very long or does it contain non-Latin-1 characters? A Ren'Py game can fail to start from a folder with such characters in its path, and a natively-protected RPG Maker MZ export needs a game-root path of about 65 characters or fewer.

---

## Text shows as boxes, question marks or garbage (tofu, mojibake)

This is a **font** problem, not a translation problem. The engine is drawing text correctly — the font it was given simply has no glyph for your characters, so you get boxes (□□□), question marks, or mojibake.

- **Boxes / tofu** → the font lacks the glyph. RuneTranslate bundles fonts where it can: Ren'Py exports include a CJK-capable or Latin-Extended font when the target needs one, and for NScripter, Artemis and Wolf RPG it can ship a purpose-built font to render **Thai** on engines that only ever understood the Japanese character set.
- **Question marks everywhere** → the target language cannot be encoded in the character set the engine uses at all. Older Shift-JIS engines are limited that way: RPG Maker XP/VX and YU-RIS ship the unmappable characters as `?`, and LiveMaker substitutes look-alikes and then strips what is left, flagging every line it had to change. A Latin-script target is the reliable choice on all three.
- **Mojibake (きちんと → ‚«‚¿‚ñ‚Æ)** → an encoding mismatch. Re-export; if it persists, report it with the engine name, because it means the file's encoding was misread.

Full write-up: **[why translated text shows as boxes](https://runetranslate.com/blog/unity-translated-text-shows-boxes)**

---

## The game is still in Japanese after export

You ran the export, it said success, and the game is unchanged. Two likely causes:

**1. You are running the wrong copy.** Export writes to the output folder you chose, not over your installed game. Launch the executable inside the *output* folder.

**2. The engine prefers its archive to your loose files.** Several engines read a packed archive in preference to anything on disk. Wolf RPG is the classic case — its runtime reads the `.wolf` archive first, so a loose-file patch does nothing at all. RuneTranslate rebuilds the archive for exactly this reason; if a rebuild could not be produced, the export tells you and explains the fallback, so read the export notes rather than assuming it worked.

For **Kirikiri**, both delivery routes are shipped (loose files *and* a `patch.xp3`) because some games comment out the hook the loose files rely on. If neither takes effect, say which game on Discord — that is a real finding, not user error.

---

## Some lines are still Japanese, but most are fine

Four causes, in rough order of likelihood:

1. **The text is in the artwork.** Title screens, menu buttons, HUD labels and CG stamps are pixels, not strings, so no extractor can reach them. That is what the [Image Studio](https://runetranslate.com/image-translation) is for.
2. **The file was not included in the run.** Check the file selection you made before translating, and check whether a regex exclusion filter caught those lines — excluded rows are shown in red and can be force-translated individually.
3. **The line came back untranslated.** Run *Scan for suspicious translations*: output that is still Japanese is one of the patterns it flags, and it flips those rows to *Failed* so you can retry them on a different provider.
4. **The extractor could not reach it.** Open the extraction report — it lists which files were found but not used, and why. If a whole file is listed and it clearly holds dialogue, report it.

---

## The engine was not detected

- **Open the folder one level up or down.** Detection looks for specific markers; pointing at `www/` instead of the game root, or at a launcher folder above it, will miss them.
- **Copy the game out of Steam / a network drive** and open the copy.
- **Check the game is not a wrapper.** Many games ship as an Electron or a browser shell around a supported engine; detection handles that, but a copy-protection wrapper can hide it.
- **Look for catalogs.** If the game has `.po` / `.mo` files, those work regardless of engine.
- **[Ask on Discord](https://discord.gg/ZtsfZu7YsW)** with the game name and a screenshot of the folder. Most supported engines started as somebody's request.

---

## The export failed

- **"Locked file" or a permission error** — the game (or an antivirus scan) is holding the output folder open. Close the game and retry.
- **A cryptic "no data found to export to"** — this used to mean the game folder had been renamed or moved. Current versions follow a moved folder automatically and, when they genuinely cannot find it, say so in plain words and offer to locate it. If you see the old message, you are on an old build: update.
- **Not enough disk space** — most engines export a full copy of the game, so a 40 GB game needs 40 GB free. Unreal is the exception; it emits a small override pak instead.
- **Antivirus quarantined the output** — some heuristics dislike freshly written game executables. Add an exclusion for your output folder.

---

## Translation is slow, or stops with a rate limit

**The free provider routes are unofficial endpoints.** They are rate-limited by the service, not by RuneTranslate, and the limits are per **IP address**, not per account.

- **Wait it out.** The app tells you when a limit is real rather than grinding through silent retries. Free Google limits usually clear in tens of minutes.
- **Switch provider.** Free DeepL and free Google have separate limits; the keyed providers have none worth worrying about.
- **Use a local model.** Ollama or LM Studio has no limit and no cost beyond your own hardware.
- **Route your run** (Supporter). Provider routing sends short strings to a free engine and dialogue to a paid one, which spreads the load and usually finishes faster than either alone.
- **Use your own proxies** (Pro). Because the limit is per IP, rotating across your own proxies turns one capped address into many. [Guide](https://runetranslate.com/blog/translate-with-your-own-proxies)

**If it is slow but nothing is failing**, and you are on the free tier, that is the throttle: roughly 2× the wall-clock time on AI providers. The banner above the progress bar says so while a run is going.

---

## A line came back unchanged, or obviously wrong

- **Unchanged output** is flagged automatically — the app marks a line failed when a provider returns the source verbatim, which is common with Google on onomatopoeia (`ドキドキ`, `ガタッ`). Retry those on DeepL or an LLM provider.
- **Duplicated words, smushed compounds, JSON fragments, one-word answers to long sentences** — run *Scan for suspicious translations*, which flags all of these and flips them to *Failed* for a targeted retry. It is fully reversible.
- **Inconsistent character names** — that is what the glossary is for. Add the name once and re-run; every batch on every provider will use your rendering.
- **Stiff, literal phrasing throughout** — run the AI refiner. It re-reads each line with its neighbours for context, which is exactly the information the first pass did not have.

---

## A Unity game hangs on a loading screen

A Unity game that loads forever with no error message is the classic symptom of a **translated identifier**: a `MonoBehaviour` field that looked like text but was actually a control id, a localization key or an engine operand, so the game is now looking up a name that no longer exists.

Current versions recognise and exclude those shapes automatically, at extraction *and* again at write-back. If you hit it anyway:

1. Update, then **create a fresh project** from the game folder. A re-scan only appends newly found lines, so it will not re-classify rows an older project already holds — though export is protected either way, because the same rules run again at write-back, refuse the row and tell you they did.
2. Look for rows that are short, ASCII, and look like identifiers rather than sentences, and exclude them.
3. Report it with the game name; the exclusion rules are structural, so a real example makes them better for everyone.

---

## Windows SmartScreen warns about the installer

The build is not code-signed, so SmartScreen shows its "Windows protected your PC" / "unrecognised app" notice. That is a statement about a code-signing certificate, not about the file's contents — and a **checksum is published alongside each release** so you can verify what you downloaded.

**Only ever download from [runetranslate.com/download](https://runetranslate.com/download).** If you got the installer anywhere else, delete it.

---

## I lost my save files

Export copies the game folder into your output folder, and a file the source folder also has will replace the one in the destination. If you exported over a build you had already played, and the original game folder happened to contain saves of its own, those can be overwritten.

**The app warns you before this happens** — it scans the destination for save data and tells you how many files are at risk. To avoid it entirely, **export into a fresh, empty folder each time**, and keep your saves somewhere else.

---

## Still stuck

1. **Run the in-app diagnosis** if you have not — it answers most of this page without guessing.
2. **Search the guides**: [runetranslate.com/blog](https://runetranslate.com/blog) has an end-to-end walkthrough for most engines.
3. **File a support ticket from inside the app.** It is a real threaded conversation with a reply, free on every tier, and you can attach a screenshot (Ctrl+V pastes one straight in), a spreadsheet or a `.rtpatch`. The About page has a one-click diagnostics block to paste in.
4. **[Ask on Discord](https://discord.gg/ZtsfZu7YsW)** — best for "has anyone translated this game before?"

When you report something, the useful details are: the game's engine, the app version, what you expected, what happened, and whether the *original* game runs on your machine.

---

**[← Back to the README](../README.md)** · **[Engines](engines.md)** · **[Features](features.md)** · **[Comparison](comparison.md)** · **[FAQ](faq.md)**
