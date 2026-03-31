# Contributing to Prompt Safety Checker

Thanks for helping make this tool better for everyone. Contributions are welcome and encouraged.

## What's most needed

### New detection patterns
The most valuable contribution is adding patterns for credentials or PII that aren't yet covered. Good candidates:
- New AI service API key formats (new providers, updated key formats)
- Regional national ID numbers not yet covered
- OAuth / JWT patterns
- `.env` file content patterns
- Cloud provider secrets (GCP service account JSON, Azure SAS tokens, etc.)

### False positive fixes
If a pattern is triggering on benign content, please open an issue with the example text (redacted if needed) so we can tighten the regex.

### UI / UX improvements
The tool is a single HTML file. CSS and JS improvements that keep it dependency-free are welcome.

### Translations
The UI is currently English-only. If you want to add language support, open an issue first to discuss approach.

---

## How to contribute

1. Fork the repo
2. Make your changes in `index.html`
3. Test with real examples covering the pattern you added
4. Open a PR with a clear description of what you added and why

## Pattern format

Each check in `CHECKS` array follows this structure:

```js
{
  id: 'unique_id',
  label: 'Human readable label',
  severity: 'fail',        // 'fail' = red/block, 'caution' = yellow/warn
  patterns: [
    /your-regex-here/gi,   // always use 'g' flag for global matching
  ],
  describe: (matches) => `Message shown when triggered: ${matches[0]}`,
  ok: 'Message shown when check passes'
}
```

## Ground rules

- Keep it a **single file** — no build steps, no npm, no bundler
- **No external requests** — the tool must work fully offline
- Test patterns for both false positives and false negatives
- Keep severity honest — `fail` is for things that should never be shared; `caution` is for things worth reviewing

## Reporting issues

Open a GitHub issue with:
- The pattern that triggered (or didn't trigger) unexpectedly
- The input text that caused it (redact any real secrets)
- What you expected vs what happened
