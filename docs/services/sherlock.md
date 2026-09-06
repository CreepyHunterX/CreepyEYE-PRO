# Sherlock (`sherlock`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `sherlock` |
| **Provider** | Sherlock (via Apify actor or local CLI) |
| **Category** | username |
| **Query types** | username |
| **API key env** | `APIFY_API_KEY (optional)` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **POST** `https://api.apify.com/v2/acts/{actor}/run-sync` — Apify-hosted Sherlock when APIFY_API_KEY set
- **CLI** `` — Local Integration/sherlock when Apify unavailable
  - uses: `found sites list`
  - uses: `checked count`
  - uses: `not_found count`

### UI entity-card fields

- found
- checked
- not_found
- accounts
- raw_files

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{found[], not_found[], raw_files?, ...}` dict on --json.

### Not used by CreepyEYE

- Full claim URLs export per site in card (truncated)
- NSFW site toggles, Tor routing options from upstream Sherlock CLI

## Upstream API — maximum available data

**Type:** Subprocess or Apify cloud actor

### Capabilities

- Check username across 300+ websites
- Return claimed profile URLs where detected
- Optional Apify cloud execution

### Output fields


**result**
- found
- checked
- not_found
- sites_found
- raw_files

## Example response

```json
{
  "found": 8,
  "checked": 300,
  "not_found": 292
}
```

## References

- [https://github.com/sherlock-project/sherlock](https://github.com/sherlock-project/sherlock)
- [https://docs.apify.com/api/v2](https://docs.apify.com/api/v2)
