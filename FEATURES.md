# Feature Contract

The COSIT analysis uses a harmonized set of **21 features**, grouped into four conceptual dimensions.

## 1. Temporal dynamics

| Feature | Interpretation |
| --- | --- |
| `hour_cos` | Cosine component of the 24-hour cycle |
| `hour_sin` | Sine component of the 24-hour cycle |
| `is_weekend` | Weekend indicator |

The sine/cosine pair represents time of day as a circular variable, so adjacent times around midnight remain close in the encoded space.

## 2. Urban morphology and spatial structure

| Feature | Interpretation |
| --- | --- |
| `built_volume_density_200m` | Built-volume density within 200 m |
| `building_density_200m` | Building density within 200 m |
| `facade_continuity_proxy` | Proxy for continuity of street-facing built form |
| `street_enclosure_index_proxy` | Proxy for street enclosure |
| `street_canyon_ratio_mean_200m` | Mean street-canyon ratio within 200 m |
| `ndbi_mean_s2` | Sentinel-2-derived mean NDBI |
| `poi_count_300m` | Point-of-interest count within 300 m |
| `intersection_density_300m` | Intersection density within 300 m |
| `betweenness_centrality` | Network betweenness centrality |
| `street_orientation_entropy` | Diversity/entropy of street orientations |

## 3. Accessibility and transport

| Feature | Interpretation |
| --- | --- |
| `transit_stop_distance` | Distance to a transit stop |
| `transit_frequency_index` | Transit-service frequency index |
| `bus_stop_density_400m` | Bus-stop density within 400 m |
| `access_to_services_index` | Composite access-to-services measure |

## 4. Environmental and weather

| Feature | Interpretation |
| --- | --- |
| `temp` | Air temperature |
| `precip` | Precipitation |
| `sensor_canopy_pct` | Tree-canopy percentage near the sensor |
| `sensor_ndvi_mean` | Mean NDVI near the sensor |

## Important modelling decision

Historical pedestrian-count lag features are excluded. The purpose is to reduce the dominance of short-term count persistence and place greater interpretive emphasis on temporal and urban-context information.

This choice should **not** be described as eliminating leakage or proving that the remaining features represent causal spatial dependencies.
