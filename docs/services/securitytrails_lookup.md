# SecurityTrails (`securitytrails_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `securitytrails_lookup` |
| **Provider** | SecurityTrails |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `SECURITYTRAILS_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/v1/ip/{ip}` — IP context
- **GET** `/v1/domain/{domain}` — Domain DNS and WHOIS summary
  - uses: `hostname / domain`
  - uses: `current_dns keys (records)`
  - uses: `history event counts`

### UI entity-card fields

- hostname
- records
- history
- whois
- subdomains
- dns_history

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

SecurityTrails JSON for ip or domain on --json.

### Not used by CreepyEYE

- Subdomains scroll API (full list)
- Associated domains, SSL certificates, WHOIS history detail
- Tags, alexa rank, technology detection endpoints

## Upstream API — maximum available data

### GET `/v1/domain/{domain}`
Domain info

**Response fields:**
- `alexa_rank`: integer
- `current_dns`: {a, aaaa, mx, ns, soa, txt}
- `endpoint`: string
- `hostname`: string
- `subdomains_count`: integer
- `tags`: array

### GET `/v1/domain/{domain}/subdomains`
Subdomain list

**Response fields:**
- `subdomains`: array
- `subdomain_count`: integer

### GET `/v1/ip/{ip}`
IP info

**Response fields:**
- `hostname`: string
- `current_dns`: object
- `history`: object

## Example response

```json
{
  "hostname": "dns.google",
  "current_dns": {
    "a": {
      "values": [
        {
          "ip": "8.8.8.8"
        }
      ]
    }
  }
}
```

## References

- [https://docs.securitytrails.com/](https://docs.securitytrails.com/)
