# ExifTool (`exiftool`)


## Overview

| Property | Value |
|----------|-------|
| **service_id** | `exiftool` |
| **Provider** | ExifTool |
| **Category** | integrations |
| **Query types** | photo |
| **API key env** | `_(none)_` |

## CreepyEYE integration

### Endpoints used by CreepyEYE

- **CLI** `` — exiftool -json on local image file
  - uses: `camera Make/Model`
  - uses: `GPSLatitude, GPSLongitude (GPS branch)`
  - uses: `CreateDate / DateTimeOriginal`
  - uses: `priority and extra EXIF tags in branches`

### UI entity-card fields

- camera
- gps
- created

### Parsed / normalized keys

- _(raw API passthrough or inline parsing)_

### CLI `--json` output

Flat metadata dict from exiftool -json on --json.

### Not used by CreepyEYE

- Full ~25k tag namespace in UI (only priority + limited extra tags)
- Write/tag mutation operations
- Embedded XMP/IPTC deep structures beyond flat JSON export

## Upstream API — maximum available data

**Type:** Subprocess (exiftool binary)

### Capabilities

- Read EXIF, IPTC, XMP, GPS, maker notes from images
- 25+ file format families supported by ExifTool
- GPS coordinate extraction and camera identification

### Output fields


**priority_tags**
- Make
- Model
- LensModel
- CreateDate
- DateTimeOriginal
- GPSLatitude
- GPSLongitude
- Software
- Artist
- Copyright

**groups**

Binary expected in Integration/exiftool or on PATH; photo pipeline only (not --modules registry).

## Example response

```json
{
  "Make": "Canon",
  "Model": "Canon EOS",
  "GPSLatitude": 50.45,
  "GPSLongitude": 30.52,
  "CreateDate": "2024:03:15 12:00:00"
}
```

## References

- [https://exiftool.org/TagNames/](https://exiftool.org/TagNames/)
- [https://exiftool.org/exiftool_pod.html](https://exiftool.org/exiftool_pod.html)
