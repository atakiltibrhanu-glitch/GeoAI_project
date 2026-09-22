# From Feature Attribution to Spatial Information Structure

**Interpreting Urban Pedestrian Flows with Explainable AI**  
COSIT 2026 — 17th International Conference on Spatial Information Theory

**Authors:** Atakilti Kiros, Achituv Cohen, Yuri Ribakov, Israel Klein  
**Affiliation:** Ariel University, Israel

## Official publication

Atakilti Kiros, Achituv Cohen, Yuri Ribakov, and Israel Klein.  
*From Feature Attribution to Spatial Information Structure: Interpreting Urban Pedestrian Flows with Explainable AI (Short Paper).*  
In **17th International Conference on Spatial Information Theory (COSIT 2026)**, Leibniz International Proceedings in Informatics (LIPIcs), Volume 393, Article 30, pp. 30:1–30:8, 2026.

- **DOI:** https://doi.org/10.4230/LIPIcs.COSIT.2026.30
- **Official proceedings page:** https://drops.dagstuhl.de/entities/document/10.4230/LIPIcs.COSIT.2026.30
- **Publication date:** 10 September 2026
- **Paper license:** CC BY 4.0
- Full citation and BibTeX: [`PAPER.md`](PAPER.md)
- Machine-readable citation metadata: [`CITATION.cff`](CITATION.cff)

## Overview

This repository provides supporting materials for the COSIT 2026 paper **“From Feature Attribution to Spatial Information Structure: Interpreting Urban Pedestrian Flows with Explainable AI.”**

The study examines whether different urban contexts encode movement-relevant information in systematically different ways. Comparable CatBoost models were trained separately for Zurich and Berlin, and SHAP was used to interpret the contribution of temporal, urban-morphology, accessibility/transport, and environmental/weather features.

The analysis is interpretive rather than causal. SHAP values are used as **model-based evidence of feature contributions** and should not be interpreted as proof that a feature causes pedestrian activity.

## Study design

- **Study period:** full year of 2024
- **Cities:** Zurich and Berlin
- **Pedestrian sensors:** approximately 60 in Zurich and 33 in Berlin
- **Harmonized features:** 21
- **Model:** separate CatBoost regressors using comparable preprocessing and model settings
- **Pedestrian-count lag features:** intentionally excluded
- **Robustness analysis:** 5 random seeds × 5 independent 80/20 train-validation splits
- **Interpretation:** global and local SHAP contribution patterns

Historical pedestrian-count lag features were excluded to reduce the dominance of short-term persistence and place greater interpretive emphasis on temporal and urban-context information.

## Reported model performance

| City | R² |
| --- | ---: |
| Zurich | 0.76 |
| Berlin | 0.80 |

R² is the predictive-performance metric reported in the COSIT paper. MSE, RMSE, and MAE were not reported in the final COSIT results.

## Main finding

> **Cities share daily rhythms, but they encode movement-relevant information through different urban configurations.**

Time of day is the strongest shared signal in both cities. Beyond this shared temporal foundation, Zurich shows relatively stronger morphology and accessibility signals, whereas Berlin shows relatively stronger temperature, street-enclosure, and weekend signals.

Cross-city SHAP comparisons in this repository should be interpreted using **within-city normalized importance profiles**. Raw SHAP magnitudes from separately trained city models are not treated as directly comparable effect sizes.

## Repository contents

```text
GeoAI_project/
├── README.md
├── PAPER.md
├── CITATION.cff
├── FEATURES.md
├── DATA_SOURCES.md
├── REPRODUCIBILITY.md
├── RESULTS_SUMMARY.md
├── results/
├── figures/
└── conference/
```

### Documentation

- [`FEATURES.md`](FEATURES.md) — definitions and conceptual grouping of the 21 harmonized features
- [`DATA_SOURCES.md`](DATA_SOURCES.md) — source classes, provenance guidance, and redistribution cautions
- [`REPRODUCIBILITY.md`](REPRODUCIBILITY.md) — documented analytical workflow
- [`RESULTS_SUMMARY.md`](RESULTS_SUMMARY.md) — headline predictive, SHAP, and robustness results
- [`PAPER.md`](PAPER.md) — official publication metadata and BibTeX
- [`CITATION.cff`](CITATION.cff) — machine-readable citation metadata

### Results

The [`results/`](results/) directory contains the derived SHAP and robustness outputs used to support the conference analysis:

- `shap_importance_zurich.csv`
- `shap_importance_berlin.csv`
- `robustness_all_runs_zurich.csv`
- `robustness_all_runs_berlin.csv`
- `robustness_summary_zurich.csv`
- `robustness_summary_berlin.csv`
- `robustness_summary_combined.csv`

### Figures

The [`figures/`](figures/) directory contains the main study figures, including:

- Zurich and Berlin study-area / sensor-location maps
- predicted-versus-actual performance plot
- Zurich and Berlin SHAP beeswarm plots
- combined Zurich–Berlin SHAP beeswarm
- normalized city-specific SHAP importance plots
- normalized cross-city SHAP heatmap

For cross-city interpretation, the **normalized** SHAP figures should be preferred over raw SHAP magnitude comparisons.

### Conference material

The [`conference/`](conference/) directory contains the QR code linking to this repository for COSIT 2026 attendees.

## Code availability

The **original analysis scripts used to produce the published study are no longer available**. For that reason, this repository should not be interpreted as a complete executable reproduction package.

Instead, it preserves:

- the official paper and citation metadata;
- feature definitions;
- data-source documentation;
- derived SHAP importance results;
- robustness outputs;
- conference figures; and
- a documented analytical workflow.

If code is reconstructed in the future, it will be clearly identified as **reconstructed reproduction code**, rather than the original scripts used to generate the published results.

## Data availability

Raw third-party data are not redistributed in this repository. The study used municipal pedestrian-count data together with Meteostat, OpenStreetMap, GTFS/public-transit data, and Sentinel-2-derived information.

See [`DATA_SOURCES.md`](DATA_SOURCES.md) for source categories, provenance guidance, and release considerations.

## Interpretation safeguards

When using these materials:

- SHAP explains the trained model; it does not establish causality.
- Positive SHAP values push an individual prediction upward; negative SHAP values push it downward.
- Raw SHAP magnitudes from separately trained city models should not be interpreted as directly comparable theoretical effect sizes.
- Normalized cross-city differences are descriptive, not statistical significance tests.
- The hour sine/cosine features jointly encode phases of the 24-hour daily cycle.

## Citation

If you use these materials, please cite the COSIT 2026 paper:

**Kiros, A., Cohen, A., Ribakov, Y., & Klein, I. (2026).**  
*From Feature Attribution to Spatial Information Structure: Interpreting Urban Pedestrian Flows with Explainable AI.*  
17th International Conference on Spatial Information Theory (COSIT 2026), LIPIcs 393, Article 30.  
https://doi.org/10.4230/LIPIcs.COSIT.2026.30

## Repository

https://github.com/atakiltibrhanu-glitch/GeoAI_project
