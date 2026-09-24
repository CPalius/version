# CPalius CMF - Current Release

> **2.2.6** · 2026-09-24 · channel: `stable`

This file is **for humans**. Installations check for updates through
[`latest.json`](latest.json) - when you change the version, change **both**.

---

## What is in this release

Full notes: [releases/2.2.6.md](releases/2.2.6.md) · Turkish: [releases/2.2.6-tr.md](releases/2.2.6-tr.md)

**Highlights**

- Updates no longer turn switched-off modules back on

Previously in 2.2.5:

- Critical: an update no longer deletes the stylesheet manifest when Tailwind cannot run on the server
- The built CSS ships in the package and is copied into place before assets compile
- Login telemetry no longer stores passwords

Previously in 2.2.4:

- Updates screen checks the release feed on demand
- Appearance: logo, favicon, share image, colours, logo size, site width, navbar height
- Designed mail and DNS homepage, SMTP login test, WHOIS over RDAP
- Visual spam score with advice, IP quota, and forum share into the message body
- Zip installer with a verified first admin and a lean sample

Previously in 2.2.3:

- Importer source kinds: WXR, SQL dump, or remote MySQL; pick which steps run
- Board files: WordPress uploads, XenForo `data/`, MyBB `uploads/` (avatars and attachments)
- Forum leftover BBCode rewrites on view; XenForo smilies import
- AACP user edit holds the full profile; overlay capabilities use language labels
- After password login, an e-mail code is asked when SMTP works

Previously in 2.2.2:

- Per-user capability overlay on AACP user edit (inherit / grant / deny; deny wins)
- `system.*` cannot be granted through the overlay; last-admin and self-lock are refused
- Themed 404 / 403 pages replace Symfony's default error screen
- Studio SEO redirects send dead public URLs to a chosen destination

Previously in 2.2.1:

- Zip / patch / `cp:update` compile the importmap after files land
- Rebuild runner ships as `/js/studio-rebuild.js` (no hashed AssetMapper file)
- Twig `asset()` is an alias of `cp_asset()` so a missing Symfony Asset component does not 500
- AACP asset rebuild dumps the importmap, not only Tailwind

Previously in 2.2.0:

- DnsTools: 50+ public DNS, mail and network tools with per-page SEO
- Header global search includes enabled tools
- One-shot catch-all inbox for spam scoring (webhook / drop / IMAP)
- Studio rebuild desk for cache, blog categories and forum counters
- Sitemap sources are tagged so modules can contribute URLs

Previously in 2.1.4:

- `cp:update` adds the forum `translation_group_id` column that 2.1.3 mapped but did not apply
- Pending module `.sql` files run even when `module.json` did not move
- BanGuard still boots against a stale 2.1.2 compiled container

Previously in 2.1.3:

- Independent Ai module translates Forum, Blog and Pages on create and edit
- Studio post list searches live across locales without a page reload
- Website header search shows grouped hits as you type
- Profile inbox keeps only unread notifications and messages

---

## Release history

| Version | Date | Channel | Notes |
|---|---|---|---|
| 2.2.6 | 2026-09-24 | stable | [releases/2.2.6.md](releases/2.2.6.md) |
| 2.2.5 | 2026-09-24 | stable | [releases/2.2.5.md](releases/2.2.5.md) |
| 2.2.4 | 2026-09-24 | stable | [releases/2.2.4.md](releases/2.2.4.md) |
| 2.2.3 | 2026-09-23 | stable | [releases/2.2.3.md](releases/2.2.3.md) |
| 2.2.2 | 2026-09-23 | stable | [releases/2.2.2.md](releases/2.2.2.md) |
| 2.2.1 | 2026-09-23 | stable | [releases/2.2.1.md](releases/2.2.1.md) |
| 2.2.0 | 2026-09-22 | stable | [releases/2.2.0.md](releases/2.2.0.md) |
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
| **MAJOR** | A backward-incompatible change - the module API breaks, or a schema change needs manual intervention |
| **MINOR** | A new feature, backward compatible |
| **PATCH** | Bug fixes only |
| **HOTFIX** | An emergency security patch only. Omitted from normal releases (`1.2.3`, never `1.2.3.0`) |

Every number must be comparable with PHP `version_compare()` - update hooks are
ordered with that function, so a value it cannot parse sorts wrong and runs data
migrations out of sequence.
