# Prompt Safety Checker

> Scan your prompt **before** it reaches any AI — catches secrets, credentials, PII and sensitive patterns locally in your browser. Zero data sent anywhere.

![License](https://img.shields.io/badge/license-MIT-green)
![Zero dependencies](https://img.shields.io/badge/dependencies-zero-blue)
![Offline](https://img.shields.io/badge/works-offline-brightgreen)

---

## Why this exists

In March 2026, Anthropic had **3 security incidents in 5 days** — a CMS config leak exposing an unreleased model, a source map leak exposing Claude Code's entire 512K-line codebase, and an npm packaging mistake. This raised a real question: *how much should you trust AI tools with sensitive data?*

The answer is: **don't share sensitive data with any AI tool in the first place.**

This tool helps you enforce that habit by scanning your prompt locally before you send it — to Claude, ChatGPT, Gemini, Copilot, or any other AI.

---

## Features

- Detects **12 categories** of sensitive data
- Works **100% offline** — pure HTML + JS, no backend, no API calls
- **Zero dependencies** — single file, open in any browser
- **Redacted preview** — shows a safe version you can copy and send
- **Safety score** — quick visual pass/fail per category
- Works before sending to **any AI tool**, not just Claude

---

## What it detects

| Category | Severity | Examples |
|---|---|---|
| API keys & tokens | 🔴 Critical | OpenAI, Anthropic, GitHub, AWS, Slack, SendGrid keys |
| Passwords | 🔴 Critical | "my password is ...", `password=...` |
| Credit / debit cards | 🔴 Critical | Visa, Mastercard, Amex numbers + CVV |
| National IDs | 🔴 Critical | Aadhaar, SSN (US), Passport numbers, PAN (India), SIN (Canada) |
| Private keys / certs | 🔴 Critical | RSA, EC, PGP private key blocks |
| Database connections | 🔴 Critical | MongoDB, PostgreSQL, MySQL, Redis URIs |
| Cloud config secrets | 🔴 Critical | AWS access keys, Azure tenant/client IDs, GCP project IDs |
| Usernames / login IDs | 🟡 Caution | `username=...`, "my username is ..." |
| Email addresses | 🟡 Caution | Full and partial email references |
| Phone numbers | 🟡 Caution | India, US, UK, international formats |
| Internal IPs / hosts | 🟡 Caution | 192.168.x.x, 10.x.x.x, localhost |
| Confidential markers | 🟡 Caution | "confidential", "under NDA", "internal only" |

---

## Usage

### Option A — Use directly (no install)
1. Download [`index.html`](./index.html)
2. Open it in any browser
3. Paste your prompt → click **Scan Prompt**
4. Review results, copy the redacted version if needed

### Option B — GitHub Pages (hosted)
Fork this repo and enable GitHub Pages (`Settings → Pages → Deploy from main`). Your own hosted instance at `https://yourusername.github.io/prompt-safety-checker`

### Option C — Keyboard shortcut
`Ctrl + Enter` inside the text box triggers a scan instantly.

---

## Privacy guarantee

Open the browser devtools (`F12 → Network`) while scanning — you will see **zero outgoing network requests**. Everything runs as local JavaScript regex pattern matching. Nothing leaves your machine.

---

## Contributing

Patterns can always be improved. PRs welcome for:
- New credential formats (new AI services, regional ID numbers, etc.)
- False positive fixes
- UI improvements
- Translations / i18n

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## Motivation & context

- [Claude Code source leak via npm (March 31, 2026)](https://dev.to/gabrielanhaia/claude-codes-entire-source-code-was-just-leaked-via-npm-source-maps-heres-whats-inside-cjo)
- [Anthropic CMS leak of unreleased model (March 26, 2026)](https://fortune.com/2026/03/26/anthropic-leaked-unreleased-model-exclusive-event-security-issues-cybersecurity-unsecured-data-store/)
- [GitGuardian 2026 report: AI-assisted commits leak secrets at 2x baseline rate](https://thehackernews.com/expert-insights/2026/03/the-real-problem-isnt-that-ai-cant.html)

---

## License

MIT — free to use, modify, and distribute. See [LICENSE](./LICENSE).
