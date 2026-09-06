# People Data Labs (`pdl_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `pdl_lookup` |
| **Provider** | People Data Labs |
| **Category** | people |
| **Query types** | name |
| **API key env** | `PEOPLE_DATA_LABS_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/v5/person/enrich` — Person enrichment
  - uses: `likelihood`
  - uses: `job_title`
  - uses: `job_company_name`
  - uses: `full_name`
  - uses: `emails, phone_numbers (contact branches)`
  - uses: `experience, education (meta branches)`
- **GET** `/v5/company/enrich` — Company enrichment when query is domain-like

### UI entity-card fields

- likelihood
- job_title
- company
- name
- gender
- emails
- email
- phones
- phone
- jobs
- skills
- industry
- employees
- detail_json_hint

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{type, result}` envelope with full PDL record in result.

### Not used by CreepyEYE

- Person search / bulk enrich
- Company search
- IP enrich, job title enrich, school enrich
- Sandbox vs production field parity on lower tiers

## Upstream API — maximum available data

### GET `/v5/person/enrich`
Enrich single person

**Response fields:**
- `status`: integer
- `likelihood`: integer
- **data**
  - `id`: string
  - `full_name`: string
  - `first_name`: string
  - `last_name`: string
  - `middle_name`: string
  - `gender`: string
  - `birth_year`: integer
  - `birth_date`: string
  - `linkedin_url`: string
  - `linkedin_username`: string
  - `facebook_url`: string
  - `twitter_url`: string
  - `github_url`: string
  - `work_email`: string
  - `personal_emails`: array
  - `recommended_personal_email`: string
  - `mobile_phone`: string
  - `phone_numbers`: array
  - `job_title`: string
  - `job_title_role`: string
  - `job_title_sub_role`: string
  - `job_title_levels`: array
  - `job_company_id`: string
  - `job_company_name`: string
  - `job_company_website`: string
  - `job_company_size`: string
  - `job_company_industry`: string
  - `job_company_linkedin_url`: string
  - `job_company_founded`: integer
  - `job_start_date`: string
  - `industry`: string
  - `location_name`: string
  - `location_locality`: string
  - `location_region`: string
  - `location_country`: string
  - `location_geo`: string
  - `skills`: array
  - `interests`: array
  - `experience`: array
  - `education`: array
  - `profiles`: array

## Example response

```json
{
  "status": 200,
  "likelihood": 8,
  "data": {
    "full_name": "Alex Demo",
    "job_title": "Analyst",
    "job_company_name": "Acme Corp"
  }
}
```

## References

- [https://docs.peopledatalabs.com/](https://docs.peopledatalabs.com/)
