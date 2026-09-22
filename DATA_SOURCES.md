# Data Sources and Release Policy

The study integrates multiple public or externally maintained sources. The public repository should preserve **provenance and acquisition instructions** even when raw files cannot be redistributed.

## Source classes

| Data class | Source used in the study | Main role |
| --- | --- | --- |
| Pedestrian counts | Municipal open-data platforms in Zurich and Berlin | Hourly pedestrian-flow target |
| Weather | Meteostat | Temperature and precipitation |
| Street/building/network data | OpenStreetMap | Morphology, network, POI, accessibility features |
| Transit | GTFS / public transit feeds | Stop proximity, stop density, service frequency |
| Earth observation | Sentinel-2 | NDVI/NDBI and environmental context |

## Release rule

Do **not** automatically upload third-party raw datasets to GitHub.

For each raw source, first verify:

1. the source licence;
2. whether redistribution is permitted;
3. attribution requirements;
4. whether the licence applies to the raw data, derived data, or both;
5. whether a stable source/download URL can be provided instead.

## Recommended public-release pattern

```text
data/
├── README.md
├── provenance/
│   └── source_provenance.csv
├── processed_example/
│   └── small_example_only.csv
└── acquisition/
    └── source_download_instructions.md
```

For conference reproducibility, it is acceptable to provide acquisition instructions and derived results without redistributing restricted or uncertain-license raw files.

## Sensor-count note

The study reports approximately 60 Zurich sensors and 33 Berlin sensors. The current mapping audit identifies 60 Zurich sensor IDs corresponding to 49 unique mapped coordinate locations, and 33 Berlin sensor IDs corresponding to 33 unique mapped locations. If this distinction is exposed publicly, explain it explicitly rather than treating sensor IDs and unique coordinates as interchangeable.
