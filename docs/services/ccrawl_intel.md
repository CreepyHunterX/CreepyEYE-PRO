# Common Crawl (`ccrawl_intel`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `ccrawl_intel` |
| **Provider** | Common Crawl |
| **Category** | intelligence |
| **Query types** | domain |
| **API key env** | `COMMONCRAWL_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `index.commoncrawl.org/collinfo.json` — List available index collections
- **GET** `index.commoncrawl.org/{index}-index` — CDX index queries for domain/URL
  - uses: `snapshot count`
  - uses: `URL count`
  - uses: `latest capture timestamp`

### UI entity-card fields

- snapshots
- urls
- latest

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Common Crawl summary object with snapshot/url stats.

### Not used by CreepyEYE

- WARC record download from data.commoncrawl.org
- Columnar index (cc-index-table) on S3
- Full CDX row payloads in UI

## Upstream API — maximum available data

### GET `/collinfo.json`
Available crawl indexes

**Response fields:**
- `id`: string
- `name`: string
- `timegate`: url
- `cdx-api`: url
- `from`: string
- `to`: string

### GET `/{index}-index`
CDX server API for captures

**Response fields:**
- `urlkey`: string
- `timestamp`: string
- `url`: string
- `mime`: string
- `status`: string
- `digest`: string
- `length`: string
- `offset`: string
- `filename`: string

## Example response

```json
{
  "snapshots": 4,
  "urls": 128,
  "latest": "2024-06-01"
}
```

## References

- [https://index.commoncrawl.org/](https://index.commoncrawl.org/)
- [https://commoncrawl.org/get-started](https://commoncrawl.org/get-started)
