# GeoNames (`geonames_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `geonames_lookup` |
| **Provider** | GeoNames |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `GEONAMES_USERNAME` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/searchJSON` — Place name search (used for geo/name queries tied to module)
  - uses: `geonames matches (name, countryCode)`

### UI entity-card fields

- geonames
- matches
- country

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{query, result}` with geonames array.

### Not used by CreepyEYE

- postalCodeLookup, findNearby, timezone, elevation APIs
- Wikipedia, weather, countryInfo full datasets

## Upstream API — maximum available data

### GET `/searchJSON`
Search placenames

**Response fields:**
- `geonames`: array of {geonameId, name, toponymName, lat, lng, countryCode, countryName, adminCode1, adminName1, fcl, fcode, population, timezone, score}

### GET `/getJSON`
Get feature by geonameId

**Response fields:**
- `geonameId`: integer
- `name`: string
- `lat`: string
- `lng`: string
- `countryCode`: string
- `timezone`: object

## Example response

```json
{
  "query": "Kyiv",
  "result": {
    "geonames": [
      {
        "name": "Kyiv",
        "countryCode": "UA"
      }
    ]
  }
}
```

## References

- [https://www.geonames.org/export/web-services.html](https://www.geonames.org/export/web-services.html)
