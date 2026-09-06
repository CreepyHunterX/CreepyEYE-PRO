# Pastebin (`pastebin_scraper`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `pastebin_scraper` |
| **Provider** | Pastebin (scrape) |
| **Category** | breaches |
| **Query types** | email, username |
| **API key env** | `PASTEBIN_SCRAPER_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `scrape.pastebin.com/api_scrape_item.php` — Fetch individual paste by ID when discovered
- **GET** `pastebin.com/raw/{id}` — Fallback raw paste URLs

### UI entity-card fields

- pastes
- latest
- tags
- api_key_types
- findings

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Scan result object with paste list, counts, and optional paste bodies.

### Not used by CreepyEYE

- POST /api/api_post.php (paste creation; referenced in module)
- Pro scraping tier archive listing (requires scraping API key)
- Paste metadata API beyond discovered IDs

## Upstream API — maximum available data

**Type:** HTTP scrape (no official search API for free tier)

### Capabilities

- Search public paste sources / discovery heuristics for email or username
- Fetch paste content by ID from multiple mirror URLs
- Report paste count and latest paste timestamp

### Output fields


**scan**
- pastes
- latest
- matches
- paste_ids

**paste_item**
- paste_id
- title
- date
- content_preview
- source

Pastebin does not offer a full public search API; CreepyEYE uses discovery + scrape endpoints.

## Example response

```json
{
  "pastes": 2,
  "latest": "2024-06-01",
  "matches": [
    {
      "paste_id": "abcdef12",
      "title": "leak combo",
      "source": "pastebin.com"
    }
  ]
}
```

## References

- [https://pastebin.com/doc_scraping_api](https://pastebin.com/doc_scraping_api)
- [https://pastebin.com/doc_api](https://pastebin.com/doc_api)
