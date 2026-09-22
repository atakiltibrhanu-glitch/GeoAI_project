# From Feature Attribution to Spatial Information Structure

**Interpreting Urban Pedestrian Flows with Explainable AI**  
COSIT 2026 — Conference on Spatial Information Theory

**Authors:** Atakilti Kiros, Achituv Cohen, Yuri Ribakov, Israel Klein  
**Affiliation:** Ariel University, Israel


## Official publication

**Atakilti Kiros, Achituv Cohen, Yuri Ribakov, and Israel Klein.**  
*From Feature Attribution to Spatial Information Structure: Interpreting Urban Pedestrian Flows with Explainable AI (Short Paper).*  
In **17th International Conference on Spatial Information Theory (COSIT 2026)**, Leibniz International Proceedings in Informatics (LIPIcs), Volume 393, Article 30, pp. 30:1–30:8, Schloss Dagstuhl – Leibniz-Zentrum für Informatik, 2026.

- DOI: [https://doi.org/10.4230/LIPIcs.COSIT.2026.30](https://doi.org/10.4230/LIPIcs.COSIT.2026.30)
- Official proceedings page: [https://drops.dagstuhl.de/entities/document/10.4230/LIPIcs.COSIT.2026.30](https://drops.dagstuhl.de/entities/document/10.4230/LIPIcs.COSIT.2026.30)
- Publication date: 10 September 2026
- Paper license: CC BY 4.0


## Overview

This repository accompanies the COSIT 2026 study **“From Feature Attribution to Spatial Information Structure: Interpreting Urban Pedestrian Flows with Explainable AI.”**

The study examines whether different urban contexts encode movement-relevant information in systematically different ways. We train comparable CatBoost models for Zurich and Berlin and use SHAP to interpret the contribution of temporal, urban-morphology, accessibility/transport, and environmental/weather features.

The emphasis is **model interpretation rather than causal inference**. SHAP values are treated as model-based evidence about feature contributions, not as proof that a feature causes pedestrian activity.

## Study design

- Study period: full year of 2024
- Cities: Zurich and Berlin
- Pedestrian sensors: approximately 60 in Zurich and 33 in Berlin
- Harmonized predictors: 21 features
- Model: separate CatBoost regressors for each city using the same modelling configuration
- Historical pedestrian-count lag features: intentionally excluded
- Robustness: 5 random seeds × 5 independent 80/20 train-validation splits
- Interpretation: SHAP global and local contribution patterns

## Reported model performance

| City | R² |
| --- | ---: |
| Zurich | 0.76 |
| Berlin | 0.80 |

R² is the predictive-performance metric reported in the COSIT paper. MSE, RMSE, and MAE are not part of the final reported COSIT results in the current manuscript.

## Main finding

> **Cities share daily rhythms, but they encode movement-relevant information through different urban configurations.**

Time of day is the strongest shared signal in both cities. Beyond this temporal foundation, Zurich shows relatively stronger morphology and accessibility signals, whereas Berlin shows relatively stronger temperature, street-enclosure, and weekend signals.

## Repository structure

```text
.
├── README.md
├── CITATION.cff
├── FEATURES.md
├── DATA_SOURCES.md
├── RESULTS_SUMMARY.md
├── REPRODUCIBILITY.md
├── LICENSE_GUIDANCE.md
├── requirements.txt
├── .gitignore
├── figures/
│   └── README.md
├── results/
│   └── README.md
└── conference/
    ├── SLIDE_TEXT.md
    └── COSIT_2026_GitHub_QR.png
```

## What will be shared

The public release should include, where licensing allows:

- feature definitions and provenance;
- scripts for preprocessing, CatBoost training, SHAP calculation, normalization, robustness analysis, and figure generation;
- derived SHAP importance tables and robustness summaries;
- conference figures;
- instructions for obtaining the original public data from their authoritative sources.

Raw third-party data should only be redistributed when the corresponding source licence permits it.

## Reproducibility

See [`REPRODUCIBILITY.md`](REPRODUCIBILITY.md) for the intended workflow and [`FEATURES.md`](FEATURES.md) for the 21-feature contract.


## Repository

https://github.com/atakiltibrhanu-glitch/GeoAI_project
