# CPalius Version

The **single source of truth** for CPalius CMF release information. Installations
check this repository once a day and offer a one-click update when a newer
release appears.

No code lives here — only release metadata and release notes.

---

## Files

| File | Read by | Purpose |
|---|---|---|
| [`latest.json`](latest.json) | **Code** | Current release pointer. This is the only file CPalius reads to decide whether an update exists. |
| [`versions.json`](versions.json) | **Code** | Index of every release, for upgrade paths and history. |
| [`version.md`](version.md) | Humans | Summary of the current release and the numbering rules. |
| [`releases/<version>.md`](releases/) | Humans | Full notes per release: features, fixes, breaking changes. |

### Why both `.json` and `.md`?

Extracting a version number from a Markdown heading is fragile — rewriting one
heading would silently break the update check on every installation in the
field. `latest.json` is eight lines and never ambiguous. `version.md` is the
document people read.

---

## Publishing a release

Three files change, and the order matters:

**1. Write the release notes**

Create `releases/<new-version>.md`. Template: [releases/1.0.0.md](releases/1.0.0.md)

It should carry these headings: *Features* · *Fixes* · *Breaking changes (if any)* ·
*Upgrade notes (if any)* · *Known limitations*

**2. Add it to the `versions.json` index**

The new entry goes at the **top** of the list.

**3. Update `latest.json` last**

The moment this file changes, every installation starts seeing the new release —
which is why it goes **last**. Moving the pointer ahead of the published notes
sends users to a release note that does not exist yet.

```jsonc
{
  "schema": 1,
  "channel": "stable",
  "version": "1.1.0",           // must be version_compare()-able
  "released_at": "2026-10-01",
  "critical": false,            // true renders the panel notice as non-dismissible
  "requires": {
    "php": ">=8.4",
    "upgrade_from": ">=1.0.0"   // older installs must step through an interim release first
  },
  "notes": {
    "url": "https://github.com/CPalius/version/blob/main/releases/1.1.0.md",
    "raw": "https://raw.githubusercontent.com/CPalius/version/main/releases/1.1.0.md"
  },
  "download": {
    "zip": "https://.../cpalius-1.1.0.zip",
    "sha256": "<sha256 of that archive>"
  }
}
```

> `download.sha256` is not optional once `download.zip` is set. The updater
> refuses an archive whose digest does not match, which is the only thing
> standing between a compromised mirror and every installation that trusts this
> file.

---

## Version numbering

```
MAJOR . MINOR . PATCH [ . HOTFIX ]
```

- **MAJOR** — backward-incompatible change
- **MINOR** — new feature, compatible
- **PATCH** — bug fixes only
- **HOTFIX** — emergency security patch only; omitted from normal releases

Every number must sort correctly under PHP `version_compare()`.

---

## How installations consume this

```
CPalius (cron, once a day)
  → GET https://raw.githubusercontent.com/CPalius/version/main/latest.json
  → version_compare(latest, installed)
  → result stored in cp_settings
  → AACP panel and site footer read that record
```

The network call happens **only during cron**. A page request never contacts
GitHub, so an outage cannot slow the site down or take it offline.

---

## License

[LICENSE](LICENSE)
