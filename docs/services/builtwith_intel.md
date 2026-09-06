# BuiltWith (`builtwith_intel`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `builtwith_intel` |
| **Provider** | BuiltWith |
| **Category** | intelligence |
| **Query types** | domain, network |
| **API key env** | `BUILTWITH_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/v22/api.json` — Domain technology lookup
  - uses: `Results[].Result.Paths[].Technologies (names)`
  - uses: `technology groups`
  - uses: `first detected dates`

### UI entity-card fields

- technologies
- groups
- first_detected

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full BuiltWith JSON response on --json.

### Not used by CreepyEYE

- Lists API, Relationships API, Keywords API
- Full tech spend, sales revenue, social profiles on company object
- Historical path depth beyond summary

## Upstream API — maximum available data

### GET `/v22/api.json`
Domain profile and technologies

**Response fields:**
- **Results**
  - {'Result': {'Paths': 'array of {Domain, Url, SubDomain, FirstIndexed, LastIndexed, Technologies[]}', 'Technologies': '{Name, Tag, FirstDetected, LastDetected, Description, Link, Parent, Categories[]}', 'Meta': {'CompanyName': 'string', 'City': 'string', 'State': 'string', 'Country': 'string', 'Vertical': 'string', 'Social': 'array', 'Telephones': 'array', 'Emails': 'array', 'Names': 'array', 'ARank': 'integer', 'QRank': 'integer'}}}

## Example response

```json
{
  "Results": [
    {
      "Result": {
        "Paths": [
          {
            "Technologies": [
              {
                "Name": "Cloudflare"
              },
              {
                "Name": "nginx"
              }
            ]
          }
        ]
      }
    }
  ]
}
```

## References

- [https://api.builtwith.com/](https://api.builtwith.com/)
