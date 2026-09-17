# CPalius CMF — Current Release

> **2.0.5** · 2026-09-18 · channel: `stable`

This file is **for humans**. Installations check for updates through
[`latest.json`](latest.json) — when you change the version, change **both**.

---

## What is in this release

Full notes: [releases/2.0.5.md](releases/2.0.5.md) · Turkish: [releases/2.0.5-tr.md](releases/2.0.5-tr.md)

**Highlights**

- Patch on top of 2.0.4: mention suggestion avatars no longer open full size
- Private messages gain "mark all as read"; both inbox flyouts clear without a page reload
- "My topics" is paginated and follows the Studio per-page setting
- Who-is-online splits into members, guests, search engines and bots, each with an icon

Previously in 2.0.4:

- Maintenance mode is enforced for the first time, with a multilingual heading and message
- Operator-created mail templates, sent by hand to one member, a role, or every active member
- The cron URL is shown in the panel, and scheduled task times are editable
- Forum: mention autocomplete, profile links, `#N` post references, hover cards, selection quoting
- Forum editor: headings, text sizes, text and highlight colours
- Studio postbit designer: block visibility, order, and a custom CSS box
- Blog related posts moved below the comments and became configurable
- Fixed: telemetry and log rows were dropped whenever a request carried malformed UTF-8
- Carries the 2.0.2 and 2.0.3 changes, which were tagged but never published here

---

## Release history

| Version | Date | Channel | Notes |
|---|---|---|---|
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
