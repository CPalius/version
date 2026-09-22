# CPalius CMF — Current Release

> **2.1.4** · 2026-09-22 · channel: `stable`

This file is **for humans**. Installations check for updates through
[`latest.json`](latest.json) — when you change the version, change **both**.

---

## What is in this release

Full notes: [releases/2.1.4.md](releases/2.1.4.md) · Turkish: [releases/2.1.4-tr.md](releases/2.1.4-tr.md)

**Highlights**

- `cp:update` now adds the forum `translation_group_id` column that 2.1.3 mapped but did not apply
- Pending module `.sql` files run even when `module.json` did not move
- BanGuard still boots against a stale 2.1.2 compiled container

Previously in 2.1.3:

- Independent Ai module translates Forum, Blog and Pages on create and edit
- Studio post list searches live across locales without a page reload
- Website header search shows grouped hits as you type
- Profile inbox keeps only unread notifications and messages

Previously in 2.1.2:

- Forum counters increment in O(1) along the ancestor path; `COUNT(*)` is legal only on recount
- Deny-Wins ACL: Inherit / Allow / Deny, four layers, sparse persist
- Local moderators, ban filters, passworded sections, a banned page
- Studio desk grouped as Structure / Permissions / Moderation / People / Settings
- Settings hub with cards; cockpit is attention, health and five shortcuts

---

## Release history

| Version | Date | Channel | Notes |
|---|---|---|---|
| 2.1.4 | 2026-09-22 | stable | [releases/2.1.4.md](releases/2.1.4.md) |
| 2.1.3 | 2026-09-22 | stable | [releases/2.1.3.md](releases/2.1.3.md) |
| 2.1.2 | 2026-09-22 | stable | [releases/2.1.2.md](releases/2.1.2.md) |
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
