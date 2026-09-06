# IPQualityScore (`ipqualityscore_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `ipqualityscore_lookup` |
| **Provider** | IPQualityScore |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `IPQUALITYSCORE_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/json/ip/{key}/{ip}` — IP fraud and proxy detection
  - uses: `fraud_score`
  - uses: `proxy`
  - uses: `vpn`
  - uses: `tor`

### UI entity-card fields

- fraud_score
- proxy
- vpn
- tor

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type, result}` with IPQualityScore payload.

### Not used by CreepyEYE

- Email / phone / URL / device fingerprint endpoints
- Full ISP, ASN, abuse contact, bot status fields in card

## Upstream API — maximum available data

### GET `/api/json/ip/{key}/{ip}`
IP reputation

**Response fields:**
- `success`: boolean
- `fraud_score`: integer
- `country_code`: string
- `region`: string
- `city`: string
- `ISP`: string
- `ASN`: integer
- `organization`: string
- `is_crawler`: boolean
- `timezone`: string
- `mobile`: boolean
- `host`: string
- `proxy`: boolean
- `vpn`: boolean
- `tor`: boolean
- `active_vpn`: boolean
- `active_tor`: boolean
- `recent_abuse`: boolean
- `bot_status`: boolean
- `connection_type`: string
- `abuse_velocity`: string
- `zip_code`: string
- `latitude`: float
- `longitude`: float

## Example response

```json
{
  "fraud_score": 12,
  "proxy": false,
  "vpn": false,
  "tor": false
}
```

## References

- [https://www.ipqualityscore.com/documentation](https://www.ipqualityscore.com/documentation)
