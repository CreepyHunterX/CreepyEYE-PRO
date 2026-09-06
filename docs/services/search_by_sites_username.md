# Search by sites (`search_by_sites_username`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `search_by_sites_username` |
| **Provider** | CreepyEYE (multi-site HTTP probes) |
| **Category** | username |
| **Query types** | username |
| **API key env** | `_(none)_` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `` — Per-site profile URL and optional API URL (GitHub, GitLab, Reddit, X, Instagram, TikTok, etc.)
  - uses: `site name`
  - uses: `found / not found status`
  - uses: `aggregate counts (sites checked, found, top sites)`

### UI entity-card fields

- sites
- found
- top
- note

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Scan summary with per-site probe results.

### Not used by CreepyEYE

- Deep profile scraping beyond existence check
- Authenticated API pagination for full profile data

## Upstream API — maximum available data

**Type:** Built-in site probe list (HTTP HEAD/GET)

### Capabilities

- Probe 14+ social/code platforms for username existence
- GitHub/GitLab API user endpoints where configured
- HEAD/GET status and redirect heuristics

### Output fields


**summary**
- sites
- found
- top

**probe_result**
- site
- url
- status
- found
- http_status

Not a single third-party API; capabilities bounded by each site's public HTTP behavior.

## Example response

```json
{
  "sites": 14,
  "found": 6,
  "top": "GitHub, Reddit"
}
```

## References

- [https://docs.github.com/en/rest/users](https://docs.github.com/en/rest/users)
