# DeHashed (`dehashed`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `dehashed` |
| **Provider** | DeHashed |
| **Category** | breaches |
| **Query types** | email, username |
| **API key env** | `DEHASHED_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **POST** `/v2/search` — Search leaked credentials and PII
  - uses: `entries[].email`
  - uses: `entries[].username`
  - uses: `entries[].password (hashed/masked in display)`
  - uses: `entries[].database`
  - uses: `total`

### UI entity-card fields

- breaches
- database
- sample

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{entries[], total}` object on --json.

### Not used by CreepyEYE

- Pagination cursors beyond first page aggregation
- IP, name, phone, address field facets in card (available in entries)
- WHOIS / domain pivot endpoints on higher tiers

## Upstream API — maximum available data

### POST `/v2/search`
Search breach corpus

**Response fields:**
- `balance`: integer
- `entries`: array of {id, email, username, password, hashed_password, name, vin, address, ip_address, phone, database, source, ob_source, dob, license_plate, passport, ssn, hash_type, password_strength, ...}
- `total`: integer
- `took`: string

## Example response

```json
{
  "entries": [
    {
      "email": "user@example.com",
      "database": "ExampleBreach2024",
      "username": "user123"
    }
  ],
  "total": 1
}
```

## References

- [https://www.dehashed.com/docs](https://www.dehashed.com/docs)
