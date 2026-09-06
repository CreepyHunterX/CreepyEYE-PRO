# Telegram (`telegram_osint_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `telegram_osint_lookup` |
| **Provider** | Telegram (Telethon MTProto) |
| **Category** | people |
| **Query types** | username |
| **API key env** | `TG_API_ID (+ TG_API_HASH, Telethon session)` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **MTProto** `` — contacts.resolveUsername, getEntity, getFullUser for @username
  - uses: `user id`
  - uses: `first_name, last_name, username`
  - uses: `status (online/recently)`
  - uses: `verified, scam, fake flags when present`

### UI entity-card fields

- status
- id
- name
- title
- members
- photo

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Telegram entity dict on --json.

### Not used by CreepyEYE

- Channel/group full member exports
- Message history search across public channels
- joinChat / invite link enumeration

## Upstream API — maximum available data

**Type:** Telethon client session (MTProto, not REST)

### Capabilities

- Resolve public @username to user ID and profile metadata
- Detect account status flags (deleted, restricted)
- Requires TG_API_ID, TG_API_HASH, and authorized session

### Output fields


**user**
- id
- username
- first_name
- last_name
- phone
- status
- verified
- scam
- fake
- bot

Requires CREEPYEYE_RUN_TELEGRAM_TESTS=1 and valid Telethon session for integration tests.

## Example response

```json
{
  "status": "found",
  "id": 123456789,
  "name": "Demo User"
}
```

## References

- [https://docs.telethon.dev/](https://docs.telethon.dev/)
- [https://core.telegram.org/methods](https://core.telegram.org/methods)
