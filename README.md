# Hong Kong Administrative Divisions / 香港

Open dataset of Hong Kong's administrative hierarchy — 18 districts and 452 District Council Constituency Areas (DCCA 2019). This repository provides structured, bilingual (Traditional Chinese + English) reference data with geographic coordinates at every level. Designed for developers, researchers, government agencies, and AI agents.

Note: Hong Kong has no postal code system. The DCCA 2019 boundary set aligns with current Care Teams sub-district zones.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| District | 18 |
| Constituency | 452 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-05-27 |
| Website | [openadmindata.org/hk](https://openadmindata.org/hk/) |
| API | [openadmindata.org/api/hk](https://openadmindata.org/api/hk/) |

## Browse by District

| # | District | Constituencys | Link |
|---|----|----|------|
| 1 | 中西區 (Central and Western) | 15 | [Browse](divisions/central-and-western-hcw/) |
| 2 | 東區 (Eastern) | 35 | [Browse](divisions/eastern-hea/) |
| 3 | 離島 (Islands) | 10 | [Browse](divisions/islands-nis/) |
| 4 | 九龍城 (Kowloon City) | 25 | [Browse](divisions/kowloon-city-kkc/) |
| 5 | 葵青 (Kwai Tsing) | 31 | [Browse](divisions/kwai-tsing-nkt/) |
| 6 | 觀塘 (Kwun Tong) | 40 | [Browse](divisions/kwun-tong-kkt/) |
| 7 | 北區 (North) | 18 | [Browse](divisions/north-nno/) |
| 8 | 西貢區 (Sai Kung) | 29 | [Browse](divisions/sai-kung-nsk/) |
| 9 | 沙田區 (Sha Tin) | 41 | [Browse](divisions/sha-tin-nst/) |
| 10 | 深水埗區 (Sham Shui Po) | 25 | [Browse](divisions/sham-shui-po-kss/) |
| 11 | 南區 (Southern) | 17 | [Browse](divisions/southern-hso/) |
| 12 | 大埔 (Tai Po) | 19 | [Browse](divisions/tai-po-ntp/) |
| 13 | 荃灣 (Tsuen Wan) | 19 | [Browse](divisions/tsuen-wan-ntw/) |
| 14 | 屯門 (Tuen Mun) | 31 | [Browse](divisions/tuen-mun-ntm/) |
| 15 | 灣仔 (Wan Chai) | 13 | [Browse](divisions/wan-chai-hwc/) |
| 16 | 黃大仙 (Wong Tai Sin) | 25 | [Browse](divisions/wong-tai-sin-kwt/) |
| 17 | 油尖旺 (Yau Tsim Mong) | 20 | [Browse](divisions/yau-tsim-mong-kyt/) |
| 18 | 元朗 (Yuen Long) | 39 | [Browse](divisions/yuen-long-nyl/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-district.json](data/all-district.json) | JSON | All 18 district records |
| [all-constituency.json](data/all-constituency.json) | JSON | All 452 constituency records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-1 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-district.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['constituency']} constituencys")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-district.json", "utf-8"));
console.log(`Total: ${data.length} districts`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=district, 2=constituency |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{district-slug}/
```

Constituencys are listed inline in each district's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-district links
- [Per-district data](docs/llms-full/) — Full data by district

## Citation

```
Hong Kong Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/hong-kong-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
