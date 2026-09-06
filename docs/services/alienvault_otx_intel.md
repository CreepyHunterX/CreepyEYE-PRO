# AlienVault OTX (`alienvault_otx_intel`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `alienvault_otx_intel` |
| **Provider** | AlienVault OTX |
| **Category** | intelligence |
| **Query types** | ip, network |
| **API key env** | `ALIENVAULT_OTX_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/v1/indicators/{type}/{indicator}/general` — Indicator general section (IPv4, domain, hostname, etc.)
  - uses: `pulse_info.count (pulse_count)`
  - uses: `reputation`
  - uses: `country`

### UI entity-card fields

- pulse_count
- reputation
- country

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type, result}` with OTX general (and optionally other sections in result).

### Not used by CreepyEYE

- /geo, /malware, /passive_dns, /url_list, /whois sections
- Pulse search and subscription management
- Full indicator sections in card

## Upstream API — maximum available data

### GET `/indicators/{type}/{indicator}/general`
General indicator metadata

**Response fields:**
- **pulse_info**
  - `count`: integer
  - `pulses`: array of {id, name, description, author_name, created, modified, tags[]}
- `country`: string
- `country_code`: string
- `city`: string
- `longitude`: float
- `latitude`: float
- `asn`: string
- `reputation`: integer
- `sections`: array
- `validation`: array
- `false_positive`: array

### GET `/indicators/{type}/{indicator}/passive_dns`
Passive DNS records

**Response fields:**
- `passive_dns`: array of {address, first, last, hostname, record_type, indicator, flag_url, flag_title, asset_type, asn}

### GET `/indicators/{type}/{indicator}/malware`
Related malware samples

**Response fields:**
- `data`: array
- `count`: integer

## Example response

```json
{
  "type": "ip",
  "result": {
    "pulse_info": {
      "count": 0
    },
    "reputation": 0,
    "country": "US"
  }
}
```

## References

- [https://otx.alienvault.com/api](https://otx.alienvault.com/api)
