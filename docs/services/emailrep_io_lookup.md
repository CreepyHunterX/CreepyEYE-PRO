# EmailRep (`emailrep_io_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `emailrep_io_lookup` |
| **Provider** | EmailRep.io |
| **Category** | people |
| **Query types** | email |
| **API key env** | `EMAILREP_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://emailrep.io/{email}` — Public email reputation lookup
  - uses: `reputation`
  - uses: `suspicious`
  - uses: `references`
  - uses: `details.data_breach`
  - uses: `details.disposable`
  - uses: `details.free_provider`
  - uses: `details.deliverable`
  - uses: `details.malicious_activity`
  - uses: `details.domain_reputation`

### UI entity-card fields

- reputation
- suspicious
- references
- data_breach
- disposable
- free_provider
- deliverable
- malicious_activity
- None
- domain reputation

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Raw EmailRep JSON returned unchanged on --json.

### Not used by CreepyEYE

- POST bulk queries
- Historical timeline endpoints (if enabled on plan)

## Upstream API — maximum available data

### GET `/{email}`
Email reputation and risk indicators

**Response fields:**
- `email`: string
- `reputation`: none | low | medium | high
- `suspicious`: boolean
- `references`: integer
- **details**
  - `blacklisted`: boolean
  - `malicious_activity`: boolean
  - `malicious_activity_recent`: boolean
  - `credentials_leaked`: boolean
  - `credentials_leaked_recent`: boolean
  - `data_breach`: boolean
  - `first_seen`: timestamp
  - `last_seen`: timestamp
  - `domain_exists`: boolean
  - `domain_reputation`: string
  - `new_domain`: boolean
  - `suspicious_tld`: boolean
  - `spam`: boolean
  - `free_provider`: boolean
  - `disposable`: boolean
  - `deliverable`: boolean
  - `accept_all`: boolean
  - `valid_mx`: boolean
  - `primary_mx`: string
  - `spoofable`: boolean
  - `spf_strict`: boolean
  - `dmarc_enforced`: boolean
  - `profiles`: array of {network, username, url, image}

## Example response

```json
{
  "email": "user@example.com",
  "reputation": "low",
  "suspicious": false,
  "references": 12,
  "details": {
    "data_breach": true,
    "disposable": false,
    "free_provider": false,
    "deliverable": true,
    "malicious_activity": false,
    "domain_reputation": "medium"
  }
}
```

## References

- [https://docs.emailrep.io/](https://docs.emailrep.io/)
