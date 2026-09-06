# SpiderFoot (`spiderfoot`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `spiderfoot` |
| **Provider** | SpiderFoot |
| **Category** | integrations |
| **Query types** | domain, email |
| **API key env** | `_(none)_` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET/POST** `http://127.0.0.1:{port}/...` — SpiderFoot local REST API for scan start/status/results
  - uses: `finding_count`
  - uses: `findings (kind, value)`
  - uses: `scan_status`

### UI entity-card fields

- findings
- status

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Summary with findings array and wizard metadata (_wizard_sf).

### Not used by CreepyEYE

- Full correlation graph export
- All 200+ module types individually surfaced in card
- Multi-target batch CLI outside wizard

## Upstream API — maximum available data

**Type:** Local SpiderFoot API (subprocess + HTTP to 127.0.0.1)

### Capabilities

- Passive OSINT scan for domain/email/username
- Aggregate findings from DNS, WHOIS, breaches, social, ports, etc.
- Module types include sfp_dnsresolve, sfp_whois, sfp_email, sfp_spider, etc.

### Output fields


**scan**
- finding_count
- scan_status
- status

**finding**
- kind
- value
- module
- data
- source_event

SpiderFoot is bundled as an unmodified upstream vendor tree and keeps its own (GPL) licence.

## Example response

```json
{
  "finding_count": 12,
  "scan_status": "FINISHED",
  "findings": [
    {
      "kind": "domain",
      "value": "creepycore.com"
    },
    {
      "kind": "ip",
      "value": "104.21.89.84"
    }
  ]
}
```

## References

- [https://www.spiderfoot.net/documentation/](https://www.spiderfoot.net/documentation/)
- [https://github.com/smicallef/spiderfoot](https://github.com/smicallef/spiderfoot)
