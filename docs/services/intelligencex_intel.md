# IntelligenceX (`intelligencex_intel`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `intelligencex_intel` |
| **Provider** | Intelligence X |
| **Category** | breaches |
| **Query types** | email, username |
| **API key env** | `INTELLIGENCEX_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **POST** `/intelligent/search` — Start selector search (email, domain, etc.)
  - uses: `records count`
  - uses: `media types`
  - uses: `selector`
- **GET** `/intelligent/search/result` — Poll search results

### UI entity-card fields

- records
- media
- selector

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Intelligence X search/result JSON on --json.

### Not used by CreepyEYE

- /file/view, /file/read full document retrieval in summary card
- Phonebook API
- Export / bulk download

## Upstream API — maximum available data

### POST `/intelligent/search`
Create search job

**Response fields:**
- `id`: uuid
- `status`: integer
- `softselector`: boolean

### GET `/intelligent/search/result`
Fetch result records

**Response fields:**
- `records`: array of {systemid, storageid, bucket, name, date, media, type, size, keyvalues, accesslevel}
- `status`: integer
- `maxresults`: integer

### GET `/file/view`
View document metadata/content

**Response fields:**
- `content`: string
- `contenttype`: string
- `filename`: string
- `keyvalues`: object

## Example response

```json
{
  "records": 3,
  "media": "pastes, leaks",
  "selector": "user@example.com"
}
```

## References

- [https://help.intelx.io/docs/api/](https://help.intelx.io/docs/api/)
