<div align="center">

<img src="https://runetranslate.com/icon-512.png" width="120" alt="RuneTranslate logo" />

# RuneTranslate

**Translate Japanese games into your language — RPG Maker, Ren'Py, Kirikiri, Wolf RPG, and more.**

A Windows desktop app that translates Japanese games *end-to-end* — dialogue, menus, items, plugin strings, and character names — into a fully playable build in your language.

[![Download for Windows](https://img.shields.io/badge/Download-Windows%2010%2F11-EC4899?style=for-the-badge&logo=windows&logoColor=white)](https://runetranslate.com/download)
[![Website](https://img.shields.io/badge/Website-runetranslate.com-7C9EFF?style=for-the-badge)](https://runetranslate.com)
[![Discord](https://img.shields.io/badge/Discord-Join-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/ZtsfZu7YsW)
[![Patreon](https://img.shields.io/badge/Patreon-Support-FF424D?style=for-the-badge&logo=patreon&logoColor=white)](https://www.patreon.com/cw/runetranslate)

</div>

---

## ✨ What it is

RuneTranslate works at the **game-engine level**, not by overlaying text at runtime. You open a Japanese game folder, pick a language and a translation provider, hit run, and out comes a **redistributable, fully playable translated build** of the game. No local server to keep running, no per-frame overlay, no scripting per game.

- 🎮 **9 engines supported** — RPG Maker MV/MZ, Ren'Py, Kirikiri/KAG, Wolf RPG, TyranoBuilder, Unity, Bakin, SRPG Studio, and custom Electron VN shells
- 🌐 **6 translation providers** — DeepL, OpenAI (ChatGPT), Anthropic Claude, free Google Translate, a local model (Ollama / LM Studio), or any OpenAI-compatible API
- 🗣️ **9 target languages** — English, Spanish, French, German, Portuguese, Russian, Chinese, Italian, Turkish
- 🔒 **Offline-first** — your API keys and translations never touch our servers
- 💸 **Free** — every engine, every provider, and every feature is unlocked on the free tier

> ⚠️ **Windows 10 / 11 (x64) only.** Not affiliated with the engine vendors. For personal / fan-translation use — respect each game's license.

---

## ⬇️ Download

Grab the latest installer from **[runetranslate.com/download](https://runetranslate.com/download)**, run it, and you're ready. The app auto-updates itself.

---

## 🚀 How to translate a game (3 steps)

1. **Open the game folder.** Click *New project* and point RuneTranslate at the game directory. Engine detection runs automatically and pulls every translatable string into a project.
2. **Pick a language + provider.** Choose your target language and a provider (DeepL, ChatGPT, Claude, free Google Translate, or your own local model). Optionally route short strings like menus to a cheap provider and dialogue to a premium one.
3. **Translate & export.** Run the batch translator, review any hand-flagged lines in the editor, and export. You get a playable copy of the game in your language. Re-run anytime — your manual edits are preserved.

---

## 🎮 Supported engines

| Engine | Status | Notes |
|---|---|---|
| **RPG Maker MV / MZ** | ✅ Full | dialogue, choices, items, skills, terms, plugin strings; auto word-wrap on export |
| **Ren'Py** | ✅ Full | source `.rpy`, compiled `.rpyc`, and archived `.rpa` — all handled |
| **Kirikiri / KAG** | ✅ Full | 26+ XP3 encryption schemes + auto-solver |
| **Wolf RPG** | ✅ Full | `.wolf` archive decrypt + repack |
| **TyranoBuilder / TyranoScript** | ✅ Full | scenarios, UI, config, character names |
| **Electron VN shells** | ✅ Full | custom Electron-based visual novels |
| **Unity** | 🟡 Best-effort | externalized text (TextAsset / MonoBehaviour / StreamingAssets) |
| **RPG Developer Bakin** | 🟡 Best-effort | database + event text via Bakin's built-in localization |
| **SRPG Studio** | 🟡 Best-effort | unpack `data.dts`, translate, repack |

➡️ Full per-engine walkthroughs: **[runetranslate.com/engines](https://runetranslate.com/engines)**

---

## 🌐 Translation providers

| Provider | Cost |
|---|---|
| **Google Translate** | Free, no key needed |
| **DeepL** | Free tier or Pro key |
| **Local model** (Ollama / LM Studio) | Free, self-hosted, fully offline |
| **OpenAI (ChatGPT, gpt-4o)** | Bring your own key |
| **Anthropic Claude** | Bring your own key |
| **Any OpenAI-compatible API** (OpenRouter, NanoGPT, …) | Bring your own key |

API keys are stored DPAPI-encrypted on your machine and go **directly** to the provider — never through us.

---

## 🧰 Beyond translation

### 💾 Built-in Save Editor

Drag a save file in and edit it directly — no replaying to fix a missed flag or grind for gold.

- **RPG Maker MV / MZ** (`.rpgsave` / `.rmmzsave`) — gold, party HP/MP/level/exp, variables, switches, inventory
- **TyranoBuilder** (`.sav`) and **Ren'Py** (`.save`) — game variables
- Auto-detects variable names from the game and can translate the labels so you know what you're editing
- Every edit auto-saves, and the original is backed up — one click to revert

### 🎲 Cheat Mode

Point it at a game folder and it injects a live in-game cheat menu — no external trainers or memory editors.

- **RPG Maker MV / MZ** — a hotkey overlay (F10): add 1000 gold, godmode, full heal, one-hit kill, no random encounters, walk through walls
- **Variables & Switches tabs** — list every game variable and switch, search by name or id, and set or toggle any of them live
- **Ren'Py** — enables the built-in developer console (Shift+O) plus a hotkey panel that edits the game's variables live
- Offline single-player only — it injects in place, and one click removes it cleanly

> Core cheats are free; a few advanced ones (the Variables/Switches editor, give-all-items, max stats, instant-win) are part of a paid plan.

### 💎 Power features

- **Translation memory** — caches every JP → target line across all your projects, so the same line in a different game is reused instantly (and your hand-fixes carry over)
- **Provider routing** — split a run into two lanes: short strings to a cheap provider, dialogue to your premium one (often cuts LLM cost 2–3×)
- **Glossary** — force-substitute names and terms (`勇者 → Hero`) so they render consistently across the whole game, on any provider

---

## 💸 Pricing

Free vs paid is a **speed lane**, not a feature paywall.

| Tier | Price | What you get |
|---|---|---|
| **Free** | $0 | Every engine, every provider, every feature — translation runs ~3–4× slower |
| **Supporter** | $3/mo | Full-speed translation + translation memory + provider routing + glossary + beta channel |
| **Pro** | $5/mo | Same as Supporter — a bigger thank-you that keeps the project alive |

Support on **[Patreon](https://www.patreon.com/cw/runetranslate/membership)**.

---

## ❓ FAQ

<details>
<summary><b>Is it really free?</b></summary>

Yes. Every engine, every provider, and every editor feature is unlocked on the free tier — translation just runs slower than the paid speed lane. There is no paid-only engine and no paid-only language.
</details>

<details>
<summary><b>Do I need an API key?</b></summary>

No. Google Translate works with no key, DeepL has a free tier, and a local model (Ollama / LM Studio) runs fully offline with no key and no per-token cost. OpenAI and Anthropic are bring-your-own-key if you want LLM quality.
</details>

<details>
<summary><b>Does it work on eroge / doujin / adult games?</b></summary>

Yes. RuneTranslate is engine-aware, not content-aware — if it's built on a supported engine, it works regardless of theme.
</details>

<details>
<summary><b>How is this different from Sugoi Toolkit / Translator++ / mtool?</b></summary>

Those translate at runtime via overlays or a local server. RuneTranslate translates the project once and exports a redistributable, fully playable build — no overlay, no local server, and DeepL / OpenAI / Anthropic / Google / local models all in one editor.
</details>

<details>
<summary><b>What languages can it translate into?</b></summary>

English, Spanish, French, German, Portuguese, Russian, Chinese, Italian, and Turkish. Source language is Japanese.
</details>

More answers: **[runetranslate.com/faq](https://runetranslate.com/faq)**

---

## 🔗 Links & community

- 🌐 **Website** — [runetranslate.com](https://runetranslate.com)
- ⬇️ **Download** — [runetranslate.com/download](https://runetranslate.com/download)
- 📖 **FAQ** — [runetranslate.com/faq](https://runetranslate.com/faq)
- 🎮 **Engine guides** — [runetranslate.com/engines](https://runetranslate.com/engines)
- 💬 **Discord** — [discord.gg/ZtsfZu7YsW](https://discord.gg/ZtsfZu7YsW)
- ❤️ **Patreon** — [patreon.com/cw/runetranslate](https://www.patreon.com/cw/runetranslate)

<div align="center">

**[⬇️ Download RuneTranslate for Windows](https://runetranslate.com/download)**

<sub>Translate Japanese RPG Maker, Ren'Py, Kirikiri, Wolf RPG, TyranoBuilder, Unity, Bakin & SRPG Studio games into English and 8 other languages.</sub>

</div>
