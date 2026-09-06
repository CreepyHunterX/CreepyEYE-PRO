# VirusTotal (`virustotal_intel`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `virustotal_intel` |
| **Provider** | VirusTotal |
| **Category** | intelligence |
| **Query types** | domain, ip, network |
| **API key env** | `VIRUSTOTAL_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/v3/ip_addresses/{ip}` — IP report
- **GET** `/api/v3/domains/{domain}` — Domain report
- **GET** `/api/v3/files/{hash}` — File hash report
- **GET** `/api/v3/urls/{id}` — URL report (encoded URL id)
  - uses: `data.attributes.last_analysis_stats (malicious, suspicious, harmless, undetected, timeout)`
  - uses: `data.attributes.reputation`
  - uses: `data.attributes.tags`

### UI entity-card fields

- malicious
- suspicious
- harmless
- reputation

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full VirusTotal v3 JSON document on --json (entire data.attributes tree).

### Not used by CreepyEYE

- Relationships (communicating_files, resolutions, subdomains, etc.) in UI card
- last_analysis_results per-engine detail in TUI (available in full JSON)
- Comments, votes, crowdsourced IDS rules
- Live hunt / retrohunt / intelligence search endpoints

## Upstream API — maximum available data

**Rate limits:** Public API 4 req/min (varies by plan); 429 on exhaustion.

### GET `/{object_type}/{id}`
object_type: ip_addresses | domains | files | urls

**Response fields:**
- **data**
  - `type`: string
  - `id`: string
  - **attributes**
    - `last_analysis_stats`: {malicious, suspicious, harmless, undetected, timeout, confirmed-timeout, failure, type-unsupported}
    - `last_analysis_results`: map engine → {category, engine_name, engine_version, result, method, engine_update}
    - `reputation`: integer
    - `tags`: array
    - `total_votes`: {harmless, malicious}
    - `last_modification_date`: integer
    - `first_submission_date`: integer
    - `last_submission_date`: integer
    - `country`: string
    - `as_owner`: string
    - `asn`: integer
    - `network`: string
    - `whois`: string
    - `whois_date`: integer
    - `categories`: object
    - `popularity_ranks`: object
    - `last_dns_records`: array
    - `last_https_certificate`: object
    - `jarm`: string
    - `sigma_analysis_summary`: object
- **links**
  - `self`: url

## Example response

```json
{
  "data": {
    "attributes": {
      "last_analysis_stats": {
        "malicious": 0,
        "suspicious": 0,
        "harmless": 68,
        "undetected": 4,
        "timeout": 0
      },
      "reputation": 0,
      "tags": [
        "cdn",
        "cloudflare"
      ]
    }
  }
}
```

## References

- [https://docs.virustotal.com/reference/overview](https://docs.virustotal.com/reference/overview)
