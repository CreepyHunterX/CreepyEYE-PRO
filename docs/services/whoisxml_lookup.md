# WhoisXML (`whoisxml_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `whoisxml_lookup` |
| **Provider** | WhoisXML API |
| **Category** | network |
| **Query types** | domain, ip, network |
| **API key env** | `WHOISXML_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/whoisserver/WhoisService` — WHOIS lookup (full or lite mode)
  - uses: `parse_whois_record output keys (registrant, registrar, dates, nameservers, status, dnssec)`

### UI entity-card fields

- registrar
- created
- expires
- nameservers

### Parsed / normalized keys

- domainName
- registrant_name
- registrant_organization
- registrant_email
- registrant_phone
- registrant_country
- registrar_name
- registry_data
- createdDate
- updatedDate
- expiresDate
- nameservers
- status
- dnssec

### CLI `--json` output

Full WhoisXML JSON on --json; TUI uses parse_whois_record subset.

### Not used by CreepyEYE

- Reverse WHOIS, WHOIS history, brand monitoring APIs
- Raw WhoisRecord audit sections beyond parse_whois_record
- DNS / SSL / subdomain products on same vendor

## Upstream API — maximum available data

### GET `/whoisserver/WhoisService`
Standard WHOIS

**Response fields:**
- **WhoisRecord**
  - `domainName`: string
  - `createdDate`: datetime
  - `updatedDate`: datetime
  - `expiresDate`: datetime
  - `registrant`: {name, organization, email, telephone, country, ...}
  - `registrar`: {name, ianaId, url, ...}
  - `registryData`: {createdDate, updatedDate, expiresDate, status[], nameServers, dnssec, rawText}
  - `contactEmail`: string
  - `domainAvailability`: string

## Example response

```json
{
  "WhoisRecord": {
    "domainName": "creepycore.com",
    "registrarName": "NameCheap, Inc.",
    "createdDate": "2020-01-15",
    "expiresDate": "2027-01-15"
  }
}
```

## References

- [https://whoisxmlapi.com/documentation](https://whoisxmlapi.com/documentation)
