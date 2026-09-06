# FullContact (`fullcontact_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `fullcontact_lookup` |
| **Provider** | FullContact |
| **Category** | people |
| **Query types** | name |
| **API key env** | `FULLCONTACT_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **POST** `https://api.fullcontact.com/v3/person.enrich` — Person enrich by email, phone, or profile URL
  - uses: `fullName`
  - uses: `organization`
  - uses: `location`
  - uses: `emails, phones (contact branches)`
  - uses: `twitter, linkedin, etc. (meta branches)`

### UI entity-card fields

- full_name
- organization
- location
- fullName
- gender
- ageRange
- emails
- email
- phones
- phone
- socialProfiles
- locations
- employment
- education

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full FullContact person object on --json.

### Not used by CreepyEYE

- Company enrich v3
- Resolve API
- Bulk enrich
- Affinity, tags, photos full arrays in UI

## Upstream API — maximum available data

### POST `/v3/person.enrich`
Person enrichment

**Response fields:**
- `fullName`: string
- `ageRange`: string
- `gender`: string
- `location`: string
- `title`: string
- `organization`: string
- `twitter`: string
- `linkedin`: string
- `facebook`: string
- `bio`: string
- `avatar`: url
- `website`: string
- **details**
  - `name`: object
  - `age`: object
  - `gender`: object
  - `emails`: array
  - `phones`: array
  - `profiles`: array
  - `locations`: array
  - `employment`: array
  - `photos`: array
  - `urls`: array

## Example response

```json
{
  "fullName": "Alex Demo",
  "organization": "Acme Corp",
  "location": "Kyiv"
}
```

## References

- [https://docs.fullcontact.com/](https://docs.fullcontact.com/)
