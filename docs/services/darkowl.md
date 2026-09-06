# DarkOwl (`darkowl`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `darkowl` |
| **Provider** | DarkOwl Vision |
| **Category** | breaches |
| **Query types** | email, username |
| **API key env** | `DARKOWL_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/v1/entity/email/{email}` — Dark web entity lookup by email
  - uses: `mentions, sources, risk (scalar branches)`
  - uses: `full record dump branches when present`

### UI entity-card fields

- mentions
- sources
- risk
- None
- tags

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type, result}` envelope with DarkOwl entity payload.

### Not used by CreepyEYE

- Entity endpoints for domain, ip, crypto, phone
- Search / query language API
- Document download endpoints

## Upstream API — maximum available data

### GET `/api/v1/entity/{type}/{value}`
Entity profile (email, domain, ip, etc.)

**Response fields:**
- `entity`: string
- `entityType`: string
- `risk`: object
- `mentions`: integer
- `sources`: array
- `records`: array of dark web documents
- `firstSeen`: datetime
- `lastSeen`: datetime
- `tags`: array

### POST `/api/v1/search`
Query dark web corpus

**Response fields:**
- `results`: array
- `total`: integer
- `facets`: object

## Example response

```json
{
  "records": [
    {
      "context": "mock ctx",
      "url": "https://example.com"
    }
  ],
  "risk_score": 0,
  "classification": "low",
  "mentions": 1
}
```

## References

- [https://docs.darkowl.com/](https://docs.darkowl.com/)
