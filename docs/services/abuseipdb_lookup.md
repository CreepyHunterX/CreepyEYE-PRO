# AbuseIPDB (`abuseipdb_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `abuseipdb_lookup` |
| **Provider** | AbuseIPDB |
| **Category** | network |
| **Query types** | ip, network |
| **API key env** | `ABUSEIPDB_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/v2/check` — IP abuse confidence check
  - uses: `abuseConfidenceScore`
  - uses: `totalReports`
  - uses: `countryCode`

### UI entity-card fields

- abuse_confidence
- reports
- country

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

AbuseIPDB check response JSON on --json.

### Not used by CreepyEYE

- POST /api/v2/report
- GET /api/v2/blacklist
- Check-block endpoint
- Report categories breakdown in UI

## Upstream API — maximum available data

### GET `/check`
Check IP reputation

**Response fields:**
- **data**
  - `ipAddress`: string
  - `isPublic`: boolean
  - `ipVersion`: integer
  - `isWhitelisted`: boolean
  - `abuseConfidenceScore`: integer
  - `countryCode`: string
  - `countryName`: string
  - `usageType`: string
  - `isp`: string
  - `domain`: string
  - `hostnames`: array
  - `isTor`: boolean
  - `totalReports`: integer
  - `numDistinctUsers`: integer
  - `lastReportedAt`: datetime
  - `reports`: array of {reportedAt, comment, categories[], reporterId, reporterCountryCode}

## Example response

```json
{
  "data": {
    "abuseConfidenceScore": 0,
    "totalReports": 0,
    "countryCode": "US"
  }
}
```

## References

- [https://docs.abuseipdb.com/](https://docs.abuseipdb.com/)
