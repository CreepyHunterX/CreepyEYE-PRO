# Have I Been Pwned (`haveibeenpwned`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `haveibeenpwned` |
| **Provider** | Have I Been Pwned |
| **Category** | breaches |
| **Query types** | email, username |
| **API key env** | `HAVEIBEENPWNED_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/api/v3/breachedaccount/{email}` — Breach list for email
  - uses: `breaches[] (Name, counts in UI)`
- **GET** `/api/v3/pasteaccount/{email}` — Paste exposures for email
  - uses: `pastes[] (count in UI)`

### UI entity-card fields

- breaches
- pastes

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type: email, result: {breaches, pastes}}` envelope on --json.

### Not used by CreepyEYE

- GET /api/v3/breach/{name} (single breach metadata)
- GET /api/v3/breaches (all breaches catalog)
- GET /api/v3/latestbreach
- GET /api/v3/dataclasses
- Stealer logs endpoints
- hibp_password() k-anonymity range API (implemented but not in main email scan card)

## Upstream API — maximum available data

**Rate limits:** 429 with Retry-After; API key required for most endpoints.

### GET `/breachedaccount/{account}`
Breaches containing account

**Response fields:**
- `Name`: string
- `Title`: string
- `Domain`: string
- `BreachDate`: date
- `AddedDate`: datetime
- `ModifiedDate`: datetime
- `PwnCount`: integer
- `Description`: html
- `DataClasses`: array
- `IsVerified`: boolean
- `IsFabricated`: boolean
- `IsSensitive`: boolean
- `IsRetired`: boolean
- `IsSpamList`: boolean
- `IsMalware`: boolean
- `IsSubscriptionFree`: boolean
- `LogoPath`: string

### GET `/pasteaccount/{account}`
Pastes mentioning account

**Response fields:**
- `Source`: string
- `Id`: string
- `Title`: string
- `Date`: datetime
- `EmailCount`: integer

## Example response

```json
[
  {
    "Name": "ExampleBreach2024",
    "Title": "Example Breach",
    "BreachDate": "2024-01-01",
    "DataClasses": [
      "Email addresses",
      "Passwords"
    ]
  }
]
```

## References

- [https://haveibeenpwned.com/API/v3](https://haveibeenpwned.com/API/v3)
- [https://haveibeenpwned.com/API/v3#PwnedPasswords](https://haveibeenpwned.com/API/v3#PwnedPasswords)
