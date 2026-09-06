# IPStack (`ipstack_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `ipstack_lookup` |
| **Provider** | IPStack (Apilayer) |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `IPSTACK_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://api.ipstack.com/{ip}` — IP geolocation
  - uses: `continent_code`
  - uses: `country_name`
  - uses: `region_name`
  - uses: `connection.isp`

### UI entity-card fields

- continent
- country
- region
- isp

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type: ipstack, result}` envelope.

### Not used by CreepyEYE

- Batch endpoint
- Security module (threat, proxy, crawler flags)
- Full currency, language, location lat/long in card

## Upstream API — maximum available data

### GET `/{ip}`
IP geolocation

**Response fields:**
- `ip`: string
- `type`: string
- `continent_code`: string
- `continent_name`: string
- `country_code`: string
- `country_name`: string
- `region_code`: string
- `region_name`: string
- `city`: string
- `zip`: string
- `latitude`: float
- `longitude`: float
- `location`: {geoname_id, capital, languages[], country_flag, ...}
- `time_zone`: {id, current_time, gmt_offset, code, is_daylight_saving}
- `currency`: {code, name, plural, symbol, symbol_native}
- `connection`: {asn, isp, sld, tld, carrier, home, organization, is_mobile, is_vpn, is_proxy, is_tor, is_datacenter, is_anonymous, is_known_abuser, is_known_attacker, is_threat, is_bogon}

## Example response

```json
{
  "type": "ipstack",
  "result": {
    "continent_code": "NA",
    "country_name": "United States",
    "region_name": "California",
    "connection": {
      "isp": "Google LLC"
    }
  }
}
```

## References

- [https://ipstack.com/documentation](https://ipstack.com/documentation)
