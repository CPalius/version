# CPalius CMF — Current Release

> **2.1.0** · 2026-09-18 · channel: `stable`

This file is **for humans**. Installations check for updates through
[`latest.json`](latest.json) — when you change the version, change **both**.

---

## What is in this release

Full notes: [releases/2.1.0.md](releases/2.1.0.md) · Turkish: [releases/2.1.0-tr.md](releases/2.1.0-tr.md)

**Highlights**

- Two-step verification gains an e-mail method; each member picks app or e-mailed code
- AACP sits behind a gate question, asked once per session
- Idle sessions are revoked on a schedule, with a shorter limit for panel accounts
- A Security page under the account area: your own open sessions and your second factor
- Forum: a per-member word filter on topic titles
- Forum: signatures are editable by the member again
- Forum: anti-bump folds a consecutive self-reply into the post above it
- Forum: the opening post gets its own, longer edit window
- The type and spacing scale is fluid — unchanged at desktop width, scaling down on phones
- Fixed: My Topics, Unread and Drafts were crushed against the left edge

Previously in 2.0.5:

- Patch on top of 2.0.4: mention suggestion avatars no longer open full size
- Private messages gain "mark all as read"; both inbox flyouts clear without a page reload
- "My topics" is paginated and follows the Studio per-page setting
- Who-is-online split into members, guests, search engines and bots (collapsed back into a single total in 2.1.0)

---

## Release history

| Version | Date | Channel | Notes |
|---|---|---|---|
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
