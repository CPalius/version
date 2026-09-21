# CPalius CMF — Current Release

> **2.1.1** · 2026-09-21 · channel: `stable`

This file is **for humans**. Installations check for updates through
[`latest.json`](latest.json) — when you change the version, change **both**.

---

## What is in this release

Full notes: [releases/2.1.1.md](releases/2.1.1.md) · Turkish: [releases/2.1.1-tr.md](releases/2.1.1-tr.md)

**Highlights**

- Forum spoilers that drop their inner HTML when locked, so View Source and quotes cannot leak them
- Optional visitor-only slimmer postbit and hidden post bodies; search engines still see the full page
- A self-hosted font library under AACP → Appearance, with Roboto, Roboto Condensed and JetBrains Mono shipped
- The homepage picker moved to Appearance and names dormant modules instead of hiding them
- A cron lock so a scheduled job cannot overlap itself, including the Run Now button
- A Studio shell a module can claim, without being able to hide AACP
- Fixed: module scripts 404'd when the import map used a relative `./` path

Previously in 2.1.0:

- Two-step verification gains an e-mail method; each member picks app or e-mailed code
- AACP sits behind a gate question, asked once per session
- Idle sessions are revoked on a schedule, with a shorter limit for panel accounts
- Forum: per-member word filter, self-service signatures, anti-bump, longer opening-post edit window

---

## Release history

| Version | Date | Channel | Notes |
|---|---|---|---|
| 2.1.1 | 2026-09-21 | stable | [releases/2.1.1.md](releases/2.1.1.md) |
| 2.1.0 | 2026-09-18 | stable | [releases/2.1.0.md](releases/2.1.0.md) |
| 2.0.5 | 2026-09-18 | stable | [releases/2.0.5.md](releases/2.0.5.md) |
| 2.0.4 | 2026-09-18 | stable | [releases/2.0.4.md](releases/2.0.4.md) |
| 2.0.1 | 2026-09-16 | stable | [releases/2.0.1.md](releases/2.0.1.md) |
| 2.0.0 | 2026-09-16 | stable | [releases/2.0.0.md](releases/2.0.0.md) |
| 1.1.3 | 2026-09-16 | stable | [releases/1.1.3.md](releases/1.1.3.md) |
| 1.1.2 | 2026-09-16 | stable | [releases/1.1.2.md](releases/1.1.2.md) |
| 1.1.1 | 2026-09-16 | stable | [releases/1.1.1.md](releases/1.1.1.md) |
| 1.1.0 | 2026-09-15 | stable | [releases/1.1.0.md](releases/1.1.0.md) |
| 1.0.0 | 2026-09-14 | stable | [releases/1.0.0.md](releases/1.0.0.md) |

---

## Version numbering

```
MAJOR . MINOR . PATCH [ . HOTFIX ]
  1   .   2   .   3   .    1
```

| Segment | Increments when |
|---|---|
| **MAJOR** | A backward-incompatible change — the module API breaks, or a schema change needs manual intervention |
| **MINOR** | A new feature, backward compatible |
| **PATCH** | Bug fixes only |
| **HOTFIX** | An emergency security patch only. Omitted from normal releases (`1.2.3`, never `1.2.3.0`) |

Every number must be comparable with PHP `version_compare()` — update hooks are
ordered with that function, so a value it cannot parse sorts wrong and runs data
migrations out of sequence.
