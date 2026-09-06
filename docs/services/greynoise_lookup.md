# GreyNoise (`greynoise_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `greynoise_lookup` |
| **Provider** | GreyNoise |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `GREYNOISE_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/v3/community/{ip}` — Free community IP context
- **GET** `/v3/ip/{ip}` — Paid enterprise context when key allows
  - uses: `classification`
  - uses: `noise (internet background noise)`
  - uses: `riot (known good service)`

### UI entity-card fields

- classification
- noise
- riot

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

GreyNoise IP context JSON on --json.

### Not used by CreepyEYE

- GNQL search API
- Tag metadata, CVE references, actor details in card
- Similar IPs, source lists

## Upstream API — maximum available data

### GET `/v3/ip/{ip}`
Full IP context

**Response fields:**
- `ip`: string
- `noise`: boolean
- `riot`: boolean
- `classification`: string
- `name`: string
- `link`: url
- `last_seen`: datetime
- `message`: string
- `tags`: array
- `metadata`: {organization, asn, category, source, region, actor, ...}
- `cvss`: object
- `cve`: array

## Example response

```json
{
  "classification": "benign",
  "noise": false,
  "riot": true
}
```

## References

- [https://docs.greynoise.io/](https://docs.greynoise.io/)
