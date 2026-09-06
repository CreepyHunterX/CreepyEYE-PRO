# Pipl (`pipl_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `pipl_lookup` |
| **Provider** | Pipl |
| **Category** | people |
| **Query types** | name |
| **API key env** | `PIPL_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://api.pipl.com/search` — Person search by email, phone, username, or name
  - uses: `persons[] (match counts)`
  - uses: `emails (count)`
  - uses: `phones (count)`

### UI entity-card fields

- matches
- emails
- phones
- phone

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full Pipl search response on --json.

### Not used by CreepyEYE

- Social API
- Contact API granular fields
- Full person object (addresses, jobs, educations, images, relationships)

## Upstream API — maximum available data

### GET `/search`
Multi-identifier person search

**Response fields:**
- `query`: object
- `persons`: array of Person objects
- **Person**
  - `names`: array
  - `emails`: array
  - `phones`: array
  - `usernames`: array
  - `addresses`: array
  - `jobs`: array
  - `educations`: array
  - `images`: array
  - `relationships`: array
  - `urls`: array
  - `dob`: object
  - `gender`: object
  - `languages`: array
  - `origin_countries`: array
- `available_data`: object
- `match_requirements`: object
- `warnings`: array

## Example response

```json
{
  "person": {
    "names": [
      {
        "display": "Alex Demo"
      }
    ],
    "emails": [
      {
        "address": "user@example.com"
      }
    ],
    "phones": [
      {
        "display": "+15551234567"
      }
    ]
  }
}
```

## References

- [https://docs.pipl.com/](https://docs.pipl.com/)
