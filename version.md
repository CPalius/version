# CPalius CMF — Current Release

> **1.0.0** · 2026-09-14 · channel: `stable`

This file is **for humans**. Installations check for updates through
[`latest.json`](latest.json) — when you change the version, change **both**.

---

## What is in this release

First stable release. Full notes: [releases/1.0.0.md](releases/1.0.0.md)

**Highlights**

- Module system, role/capability authorisation, notification and global search infrastructure
- Ten modules: Forum, Blog, Pages, Media, Menu, Seo, Roadmap, Whitepaper, Widget, Importer
- Forum: section hierarchy, polls, attachments, drafts, topic split/merge, ban/mute, permission matrix
- Importer: WordPress, Joomla, MyBB, XenForo and CSV
- Seo: JSON-LD schema graph, per-source sitemaps
- Multilingual content and interface
- AACP administration panel, `cp:doctor` diagnostics
- Version-tagged update hooks

---

## Release history

| Version | Date | Channel | Notes |
|---|---|---|---|
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
