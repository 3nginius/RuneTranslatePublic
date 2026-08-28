# Security policy

RuneTranslate is a closed-source Windows desktop application distributed from **[runetranslate.com/download](https://runetranslate.com/download)**. This repository holds its public documentation; it contains no application code.

## Reporting a vulnerability

**Please report privately, not as a public issue.** Use whichever is easiest:

- A **support ticket from inside the app** (*Support* → new ticket) — this is the most reliable route and it reaches the developer directly
- A direct message on **[Discord](https://discord.gg/ZtsfZu7YsW)**
- Email **[runetranslate@gmail.com](mailto:runetranslate@gmail.com)**

Please include what you found, how to reproduce it, the app version (the About page has a one-click diagnostics block), and what you think the impact is. Reports are usually acknowledged within a few days.

Please do not post a working exploit publicly before it has been fixed.

## Scope

**In scope:** the RuneTranslate desktop application, `runetranslate.com` and its APIs, and the account/authentication flow.

**Out of scope:** the third-party translation providers RuneTranslate can talk to (DeepL, OpenAI, Anthropic, DeepSeek, Google, OpenRouter and so on) — report those to the provider — and the games themselves.

## Downloading safely

The Windows build is not code-signed, so SmartScreen shows an "unrecognised app" warning on first run. A checksum is published with each release so you can verify what you downloaded.

**Only ever download RuneTranslate from [runetranslate.com/download](https://runetranslate.com/download).** No installer is distributed from this repository, and any RuneTranslate build offered anywhere else is not ours.
