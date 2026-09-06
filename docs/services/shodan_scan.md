# Shodan (`shodan_scan`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `shodan_scan` |
| **Provider** | Shodan |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `SHODAN_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/shodan/host/search` — Search hosts (CIDR/network queries)
  - uses: `matches[].ip_str`
  - uses: `matches[].org`
  - uses: `matches[].asn`
  - uses: `total`
- **GET** `/shodan/host/{ip}` — Host report for single IP
  - uses: `ports, org, asn, hostnames, vulns (in full JSON)`

### UI entity-card fields

- matches
- org
- asn
- ports

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Shodan host or search JSON on --json.

### Not used by CreepyEYE

- DNS domain info, exploits, honeyscore, scan/on-demand scan
- Account profile, alert management, network monitor
- Full banner data per port in TUI card (available in JSON)

## Upstream API — maximum available data

### GET `/shodan/host/{ip}`
Host services and banners

**Response fields:**
- `ip_str`: string
- `ports`: array
- `hostnames`: array
- `country_code`: string
- `city`: string
- `org`: string
- `isp`: string
- `asn`: string
- `last_update`: datetime
- `tags`: array
- `vulns`: array
- `data`: array of banners {port, transport, product, version, cpe, banner, ssl, http, ...}

### GET `/shodan/host/search`
Search the index

**Response fields:**
- `matches`: array
- `total`: integer
- `facets`: object

## Example response

```json
{
  "search": {
    "total": 1,
    "matches": [
      {
        "ip_str": "8.8.8.8",
        "org": "Google LLC",
        "asn": "AS15169",
        "port": 443
      }
    ]
  }
}
```

## References

- [https://developer.shodan.io/api](https://developer.shodan.io/api)
