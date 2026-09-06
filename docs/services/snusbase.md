# Snusbase (`snusbase`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `snusbase` |
| **Provider** | Snusbase |
| **Category** | breaches |
| **Query types** | email, username |
| **API key env** | `SNUSBASE_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **POST** `/data/search` — Search breach index by email or username
  - uses: `results (hits count)`
  - uses: `database names`

### UI entity-card fields

- hits
- databases

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Snusbase search response JSON on --json.

### Not used by CreepyEYE

- Hash lookup endpoints
- WHOIS / IP tools on Snusbase
- Full row fields (password hash, salt, name, ip) in card summary

## Upstream API — maximum available data

### POST `/data/search`
Search leaked records

**Response fields:**
- `took`: integer
- `size`: integer
- `results`: object keyed by database name → array of records
- `record`: {email, username, password, hash, salt, name, ip, lastip, _domain, created, birthdate, ...}

## Example response

```json
{
  "size": 1,
  "results": {
    "combo_2023": [
      {
        "email": "user@example.com",
        "username": "user123"
      }
    ]
  }
}
```

## References

- [https://docs.snusbase.com/](https://docs.snusbase.com/)
