# Clearbit (`clearbit_domain_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `clearbit_domain_lookup` |
| **Provider** | Clearbit |
| **Category** | people |
| **Query types** | domain |
| **API key env** | `CLEARBIT_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `https://company.clearbit.com/v2/companies/find` — Company enrichment by domain
  - uses: `domain`
  - uses: `name`
  - uses: `industry`
  - uses: `location`
  - uses: `metrics (key count)`
  - uses: `linkedin, twitter, facebook (presence count)`

### UI entity-card fields

- company
- employees
- sector
- location
- name
- employment
- work_domain
- social_handles
- metrics_keys
- social_links

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Full Clearbit company object on --json.

### Not used by CreepyEYE

- Autocomplete API
- Full metrics breakdown (employees, raised, marketCap, etc.)
- tech, tags, type, ticker, phone, email, site details

## Upstream API — maximum available data

### GET `/v2/companies/find`
Company profile by domain

**Response fields:**
- `id`: string
- `name`: string
- `legalName`: string
- `domain`: string
- `domainAliases`: array
- `site`: {phoneNumbers[], emailAddresses[], url}
- `category`: {sector, industryGroup, industry, subIndustry, sicCode, naicsCode}
- `tags`: array
- `description`: string
- `foundedYear`: integer
- `location`: string
- `timeZone`: string
- `utcOffset`: integer
- `geo`: object
- `logo`: url
- `facebook`: object
- `linkedin`: object
- `twitter`: object
- `crunchbase`: object
- `emailProvider`: boolean
- `type`: string
- `ticker`: string
- `identifiers`: object
- `phone`: string
- `metrics`: {alexaUsRank, alexaGlobalRank, employees, employeesRange, marketCap, raised, annualRevenue, estimatedAnnualRevenue, fiscalYearEnd}
- `indexedAt`: datetime
- `tech`: array
- `techCategories`: array
- `parent`: object
- `ultimateParent`: object

## Example response

```json
{
  "domain": "example.com",
  "name": "CreepyCORE Ltd",
  "industry": "Security",
  "location": "UA",
  "metrics": {
    "employees": 25,
    "employeesRange": "11-50"
  }
}
```

## References

- [https://dashboard.clearbit.com/docs#enrichment-api-company-api](https://dashboard.clearbit.com/docs#enrichment-api-company-api)
