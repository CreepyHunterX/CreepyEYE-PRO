# IP-API (`ip_api_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `ip_api_lookup` |
| **Provider** | IP-API |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `IP_API_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `http://ip-api.com/json/{ip}` — Free IP geolocation (selected fields param)
  - uses: `status, country, regionName, city, lat, lon, isp, org, as, query`

### UI entity-card fields

- status
- country
- city
- isp

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type, result}` with IP-API fields.

### Not used by CreepyEYE

- Pro HTTPS endpoint with API key
- Batch POST /batch (up to 100 IPs)
- fields=mobile,proxy,hosting on pro tier

## Upstream API — maximum available data

**Rate limits:** Free tier 45 req/min; HTTP only on free plan.

### GET `/json/{query}`
Single IP/hostname lookup

**Response fields:**
- `status`: success | fail
- `message`: string
- `continent`: string
- `continentCode`: string
- `country`: string
- `countryCode`: string
- `region`: string
- `regionName`: string
- `city`: string
- `district`: string
- `zip`: string
- `lat`: float
- `lon`: float
- `timezone`: string
- `offset`: integer
- `currency`: string
- `isp`: string
- `org`: string
- `as`: string
- `asname`: string
- `reverse`: string
- `mobile`: boolean
- `proxy`: boolean
- `hosting`: boolean
- `query`: string

## Example response

```json
{
  "type": "ip",
  "result": {
    "status": "success",
    "country": "United States",
    "city": "Ashburn",
    "isp": "Google LLC"
  }
}
```

## References

- [https://ip-api.com/docs](https://ip-api.com/docs)
