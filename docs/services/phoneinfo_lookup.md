# PhoneInfo (`phoneinfo_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `phoneinfo_lookup` |
| **Provider** | PhoneInfoAPI |
| **Category** | network |
| **Query types** | phone |
| **API key env** | `PHONEINFO_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://phoneinfoapi.com/{phone}` — Phone metadata lookup
  - uses: `valid`
  - uses: `region`
  - uses: `timezone`

### UI entity-card fields

- valid
- region
- timezone

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

PhoneInfo API JSON on --json.

### Not used by CreepyEYE

- Carrier MCC/MNC detail
- Number type confidence scores

## Upstream API — maximum available data

### GET `/{phone_number}`
Phone enrichment

**Response fields:**
- `valid`: boolean
- `number`: string
- `country`: string
- `region`: string
- `timezone`: string
- `carrier`: string
- `line_type`: string

## Example response

```json
{
  "valid": true,
  "region": "California",
  "timezone": "America/Los_Angeles"
}
```

## References

- [https://phoneinfoapi.com/docs](https://phoneinfoapi.com/docs)
