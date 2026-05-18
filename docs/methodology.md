# Methodology

## Data Sources

This dataset is compiled from multiple open sources:

- **GeoNames** (CC BY 4.0) — 18 district records with coordinates and HAD administrative codes
- **snowiewdev/hkdistricts** — Bilingual district names (Traditional Chinese + Simplified + English) and region grouping (Hong Kong Island / Kowloon / New Territories)
- **hkdce/dcca-boundaries** — 452 DCCA (District Council Constituency Area) 2019 boundary polygons with bilingual names, sourced from the Electoral Affairs Commission

## Processing

1. District list from GeoNames ADM1 features (18 records with lat/lon)
2. Traditional Chinese names joined from snowiewdev district data
3. DCCA polygons from hkdce → centroid computation for coordinates
4. Parent assignment via CACODE first-letter mapping to HAD district codes
5. Multi-format export: JSON, NDJSON, CSV
6. Hierarchy folder structure with READMEs generated via EJS templates

## Structure

- **18 Districts** (區) — the only statutory administrative tier below HKSAR
- **452 Constituencies** (選區) — DCCA 2019 boundary set, also used as Care Teams sub-district zones

## Important Notes

- Hong Kong has **no postal code system** (confirmed by Hongkong Post and UPU)
- ISO 3166-2:HK defines no subdivision codes; we use HAD 3-letter codes (e.g., HCW, KKC)
- `name_local` uses Traditional Chinese (繁體中文) in HK orthography
- DCCA boundaries were redrawn in 2023 to 44 constituencies for elections, but the 452-zone layer remains in use for Care Teams service delivery

## Accuracy

- All coordinates computed from authoritative polygon boundaries or GeoNames centroids
- 100% coordinate coverage at all levels
- Bilingual names verified against HAD and EAC official sources
- Build script is idempotent: same input always produces same output