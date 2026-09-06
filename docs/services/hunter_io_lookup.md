# Hunter.io (`hunter_io_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `hunter_io_lookup` |
| **Provider** | Hunter.io |
| **Category** | people |
| **Query types** | email |
| **API key env** | `HUNTERIO_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/v2/domain-search` — Derives domain from email, searches professional emails
  - uses: `data.emails[].value`
  - uses: `data.emails[].confidence`
  - uses: `data.emails (count)`

### UI entity-card fields

- emails
- pattern
- confidence

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full Hunter.io JSON via emit_ok(data) on --json.

### Not used by CreepyEYE

- GET /v2/email-finder
- GET /v2/email-verifier
- GET /v2/domain-search (pattern, organization, webmail, disposable fields)
- GET /v2/companies/find
- Account usage / leads endpoints

## Upstream API — maximum available data

**Rate limits:** Plan-dependent; 429 with Retry-After on exhaustion.

### GET `/v2/domain-search`
List emails associated with a domain

**Response fields:**
- **data**
  - `domain`: string
  - `organization`: string
  - `description`: string
  - `industry`: string
  - `twitter`: string
  - `facebook`: string
  - `linkedin`: string
  - `instagram`: string
  - `youtube`: string
  - `technologies`: array
  - `country`: string
  - `state`: string
  - `city`: string
  - `postal_code`: string
  - `street`: string
  - `headcount`: string
  - `company_type`: string
  - `emails`: array of {value, type, confidence, first_name, last_name, position, seniority, department, linkedin, twitter, phone_number, sources[]}
  - `linked_domains`: array
- **meta**
  - `results`: integer
  - `limit`: integer
  - `offset`: integer
  - `params`: object

### GET `/v2/email-finder`
Find email for domain + name

**Response fields:**
- `data`: {first_name, last_name, email, score, domain, accept_all, position, twitter, linkedin, phone_number, sources[]}
- `meta`: {results, limit, offset, params}

### GET `/v2/email-verifier`
Verify deliverability and risk signals

**Response fields:**
- `data`: {status, result, score, email, regexp, gibberish, disposable, webmail, mx_records, smtp_server, smtp_check, accept_all, block, sources[]}

## Example response

```json
{
  "data": {
    "domain": "example.com",
    "organization": "Example Inc",
    "pattern": "{first}.{last}",
    "emails": [
      {
        "value": "user@example.com",
        "type": "personal",
        "confidence": 92
      }
    ]
  },
  "meta": {
    "results": 1,
    "limit": 10,
    "offset": 0
  }
}
```

## References

- [https://hunter.io/api-documentation/v2](https://hunter.io/api-documentation/v2)
