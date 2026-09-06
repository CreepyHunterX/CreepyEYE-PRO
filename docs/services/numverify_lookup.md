# NumVerify (`numverify_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `numverify_lookup` |
| **Provider** | NumVerify (Apilayer) |
| **Category** | network |
| **Query types** | phone |
| **API key env** | `NUMVERIFY_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://apilayer.net/api/validate` — Phone number validation
  - uses: `valid`
  - uses: `carrier`
  - uses: `line_type`
  - uses: `country_name / country_code`

### UI entity-card fields

- valid
- carrier
- line_type
- country

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

NumVerify validate JSON on --json.

### Not used by CreepyEYE

- Number formatting batch endpoint
- Full location object fields in card

## Upstream API — maximum available data

### GET `/validate`
Validate and enrich phone number

**Response fields:**
- `valid`: boolean
- `number`: string
- `local_format`: string
- `international_format`: string
- `country_prefix`: string
- `country_code`: string
- `country_name`: string
- `location`: string
- `carrier`: string
- `line_type`: string

## Example response

```json
{
  "valid": true,
  "carrier": "Demo Mobile",
  "line_type": "mobile",
  "country_name": "United States"
}
```

## References

- [https://numverify.com/documentation](https://numverify.com/documentation)
