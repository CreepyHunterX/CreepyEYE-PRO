# Ipinfo (`ipinfo_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `ipinfo_lookup` |
| **Provider** | Ipinfo |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `IPINFO_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://ipinfo.io/{ip}/json` — IP geolocation and ASN
  - uses: `org, city, country, hostname`
  - uses: `asn object (asn branches)`
  - uses: `carrier (when phone/IP context)`

### UI entity-card fields

- org
- city
- country
- hostname
- geo
- domains
- loc
- network

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Ipinfo JSON object on --json.

### Not used by CreepyEYE

- Bulk API
- Hosted domains, anycast, privacy detection fields in card
- Company API enrichment tier

## Upstream API — maximum available data

### GET `/{ip}/json`
IP details

**Response fields:**
- `ip`: string
- `hostname`: string
- `city`: string
- `region`: string
- `country`: string
- `loc`: string
- `org`: string
- `postal`: string
- `timezone`: string
- `asn`: {asn, name, domain, route, type}
- `company`: {name, domain, type}
- `carrier`: {name, mcc, mnc}
- `privacy`: {vpn, proxy, tor, relay, hosting, service}

## Example response

```json
{
  "ip": "8.8.8.8",
  "city": "Mountain View",
  "country": "US",
  "org": "AS15169 Google LLC",
  "hostname": "dns.google"
}
```

## References

- [https://ipinfo.io/developers](https://ipinfo.io/developers)
