# Recon-ng (`recon_ng_lookup`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `recon_ng_lookup` |
| **Provider** | Recon-ng |
| **Category** | integrations |
| **Query types** | domain |
| **API key env** | `_(none)_` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **CLI** `` — recon-cli marketplace modules for domain recon
  - uses: `modules run count`
  - uses: `aggregated text output (hosts/contacts summary)`

### UI entity-card fields

- modules
- results

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

`{module, exit_code, output}` per module invocation.

### Not used by CreepyEYE

- Interactive recon-ng shell
- Full structured JSON per module (stdout captured as text)
- Workspace/database persistence across runs

## Upstream API — maximum available data

**Type:** Subprocess (recon-cli)

### Capabilities

- Run marketplace modules (hosts, contacts, credentials) against domain
- Modular recon framework with 80+ modules available upstream

### Output fields


**run**
- module
- exit_code
- output

## Example response

```json
{
  "modules": 3,
  "results": "hosts/contacts found"
}
```

## References

- [https://github.com/lanmaster53/recon-ng](https://github.com/lanmaster53/recon-ng)
- [https://github.com/lanmaster53/recon-ng-marketplace/blob/master/modules.yml](https://github.com/lanmaster53/recon-ng-marketplace/blob/master/modules.yml)
