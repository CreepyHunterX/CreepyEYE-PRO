# Whitepages (`whitepages_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `whitepages_lookup` |
| **Provider** | Whitepages Pro |
| **Category** | people |
| **Query types** | name, phone |
| **API key env** | `WHITEPAGES_API_KEY` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **GET** `/3.4/phone` — Reverse phone lookup
  - uses: `name, address, line_type (phone branch)`
- **GET** `/3.4/email` — Email lookup when query is email
- **GET** `/3.4/location` — Address / name lookup

### UI entity-card fields

- name
- address
- line_type

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Raw Whitepages JSON on --json.

### Not used by CreepyEYE

- Identity Check API
- Caller ID API
- Bulk endpoints
- Full historical addresses and associated people arrays

## Upstream API — maximum available data

### GET `/3.4/phone`
Phone identity

**Response fields:**
- `phone_number`: string
- `is_valid`: boolean
- `line_type`: string
- `carrier`: string
- `is_prepaid`: boolean
- `is_commercial`: boolean
- `belongs_to`: array of {name, firstname, lastname, age_range, gender, industry, link_to_address_start_date}
- `current_addresses`: array
- `historical_addresses`: array
- `associated_people`: array
- `country_calling_code`: integer
- `country_code`: string
- `country_name`: string

### GET `/3.4/email`
Email identity

**Response fields:**
- `email_address`: string
- `is_valid`: boolean
- `is_disposable`: boolean
- `belongs_to`: array
- `current_addresses`: array

### GET `/3.4/location`
Address / geo lookup

**Response fields:**
- `street_line_1`: string
- `city`: string
- `state_code`: string
- `postal_code`: string
- `lat_long`: object
- `residents`: array
- `current_residents`: array

## Example response

```json
{
  "phone_number": "+15551234567",
  "line_type": "Mobile",
  "belongs_to": [
    {
      "name": "Alex Demo"
    }
  ],
  "current_addresses": [
    {
      "city": "Kyiv",
      "country_code": "UA"
    }
  ]
}
```

## References

- [https://pro.whitepages.com/developer/documentation/](https://pro.whitepages.com/developer/documentation/)
