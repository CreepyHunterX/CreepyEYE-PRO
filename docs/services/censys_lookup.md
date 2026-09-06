# Censys (`censys_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `censys_lookup` |
| **Provider** | Censys |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `CENSYS_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/v2/hosts/{ip}` — Host lookup by IP
- **POST** `/api/v2/hosts/search` — Host search for network/CIDR queries
  - uses: `services (count)`
  - uses: `location.country`
  - uses: `autonomous_system.name`

### UI entity-card fields

- services
- location
- autonomous_system
- coords
- asn
- tls certs

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Censys host or search hit JSON on --json.

### Not used by CreepyEYE

- Certificates search API v2
- Web properties / domains API
- Full service banner and software enumeration in card

## Upstream API — maximum available data

### GET `/v2/hosts/{ip}`
Host details

**Response fields:**
- `ip`: string
- `services`: array of {port, service_name, transport_protocol, extended_service_name, certificate, software[]}
- `location`: {continent, country, city, postal_code, timezone, coordinates}
- `autonomous_system`: {asn, description, bgp_prefix, name, country_code, country_name}
- `operating_system`: object
- `dns`: object
- `last_updated_at`: datetime

### POST `/v2/hosts/search`
Query hosts

**Response fields:**
- **result**
  - `hits`: array
  - `total`: integer
- `code`: integer
- `status`: string

## Example response

```json
{
  "services": 2,
  "location": {
    "country": "US"
  },
  "autonomous_system": {
    "name": "GOOGLE"
  }
}
```

## References

- [https://search.censys.io/api](https://search.censys.io/api)
