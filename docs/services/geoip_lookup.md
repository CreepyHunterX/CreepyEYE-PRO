# GeoIP (`geoip_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `geoip_lookup` |
| **Provider** | GeoIP API (geoipapi.com) |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `GEOIP_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://geoipapi.com/api/v1` — IP geolocation enrichment
  - uses: `latitude, longitude, timezone, currency`

### UI entity-card fields

- latitude
- longitude
- timezone
- currency

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type: ip, result}` envelope.

### Not used by CreepyEYE

- Bulk endpoint
- Threat / anonymous IP flags

## Upstream API — maximum available data

### GET `/api/v1`
IP lookup

**Response fields:**
- `ip`: string
- `type`: string
- `continent_code`: string
- `country_code`: string
- `country_name`: string
- `region_code`: string
- `region_name`: string
- `city`: string
- `latitude`: float
- `longitude`: float
- `currency`: object
- `time_zone`: object
- `isp`: string
- `organization`: string

## Example response

```json
{
  "type": "ip",
  "result": {
    "latitude": 50.45,
    "longitude": 30.52,
    "timezone": "Europe/Kyiv",
    "currency": {
      "code": "UAH"
    }
  }
}
```

## References

- [https://geoipapi.com/documentation](https://geoipapi.com/documentation)
