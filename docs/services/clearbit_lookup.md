# Clearbit (`clearbit_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `clearbit_lookup` |
| **Provider** | Clearbit |
| **Category** | people |
| **Query types** | email |
| **API key env** | `CLEARBIT_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://person.clearbit.com/v2/people/find` — Person enrichment by email
  - uses: `email`
  - uses: `name.fullName`
  - uses: `location`
  - uses: `employment.title`
  - uses: `employment.name`
  - uses: `employment.domain`
  - uses: `twitter, linkedin, github, facebook, angellist (count only in UI)`

### UI entity-card fields

- name
- title
- company
- location
- employment
- work_domain
- social_handles
- metrics_keys
- social_links

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full Clearbit person object on --json.

### Not used by CreepyEYE

- Prospector API
- Reveal API (website visitor ID)
- Risk API
- Full social profile objects (only counts shown in card)
- Avatar, bio, site, fuzzy, geo, timeZone

## Upstream API — maximum available data

### GET `/v2/people/find`
Enrich person by email

**Response fields:**
- `id`: string
- `name`: {givenName, familyName, fullName}
- `email`: string
- `location`: string
- `timeZone`: string
- `utcOffset`: integer
- `geo`: {city, state, stateCode, country, countryCode, lat, lng}
- `bio`: string
- `site`: string
- `avatar`: url
- `employment`: {domain, name, title, role, subRole, seniority}
- `facebook`: {handle, url}
- `github`: {handle, id, avatar, company, blog, followers, following}
- `twitter`: {handle, id, bio, followers, following, statuses, favorites, location, site, avatar}
- `linkedin`: {handle, url}
- `googleplus`: object
- `gravatar`: object
- `fuzzy`: boolean
- `emailProvider`: boolean
- `indexedAt`: datetime

## Example response

```json
{
  "email": "user@example.com",
  "name": {
    "fullName": "Alex Demo"
  },
  "location": "Kyiv, UA",
  "employment": {
    "title": "Engineer",
    "name": "Acme Corp",
    "domain": "acme.com"
  }
}
```

## References

- [https://dashboard.clearbit.com/docs](https://dashboard.clearbit.com/docs)
