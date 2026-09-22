From Feature Attribution to Spatial Information Structure

Interpreting Urban Pedestrian Flows with Explainable AI
COSIT 2026 — Conference on Spatial Information Theory

Authors: Atakilti Kiros, Achituv Cohen, Yuri Ribakov, Israel Klein
Affiliation: Ariel University, Israel

Overview

This repository accompanies the COSIT 2026 study “From Feature Attribution to Spatial Information Structure: Interpreting Urban Pedestrian Flows with Explainable AI.”

The study examines whether different urban contexts encode movement-relevant information in systematically different ways. We train comparable CatBoost models for Zurich and Berlin and use SHAP to interpret the contribution of temporal, urban-morphology, accessibility/transport, and environmental/weather features.

The emphasis is model interpretation rather than causal inference. SHAP values are treated as model-based evidence about feature contributions, not as proof that a feature causes pedestrian activity.

Study design

Study period: full year of 2024

Cities: Zurich and Berlin

Pedestrian sensors: approximately 60 in Zurich and 33 in Berlin

Harmonized predictors: 21 features

Model: separate CatBoost regressors for each city using the same modelling configuration

Historical pedestrian-count lag features: intentionally excluded

Robustness: 5 random seeds × 5 independent 80/20 train-validation splits

Interpretation: SHAP global and local contribution patterns

Reported model performance

City

R²

Zurich

0.76

Berlin

0.80

R² is the predictive-performance metric reported in the COSIT paper. MSE, RMSE, and MAE are not part of the final reported COSIT results in the current manuscript.

Main finding

Cities share daily rhythms, but they encode movement-relevant information through different urban configurations.

Time of day is the strongest shared signal in both cities. Beyond this temporal foundation, Zurich shows relatively stronger morphology and accessibility signals, whereas Berlin shows relatively stronger temperature, street-enclosure, and weekend signals.

Repository structure

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
├── code/
│   └── README.md
├── data/
│   └── README.md
├── figures/
│   └── README.md
├── results/
│   └── README.md
└── conference/
    ├── SLIDE_TEXT.md
    └── COSIT_2026_GitHub_QR.png

What will be shared

The public release should include, where licensing allows:

feature definitions and provenance;

scripts for preprocessing, CatBoost training, SHAP calculation, normalization, robustness analysis, and figure generation;

derived SHAP importance tables and robustness summaries;

conference figures;

instructions for obtaining the original public data from their authoritative sources.

Raw third-party data should only be redistributed when the corresponding source licence permits it.

Reproducibility

See REPRODUCIBILITY.md for the intended workflow and FEATURES.md for the 21-feature contract.

Citation

If you use this repository, please cite the COSIT 2026 paper. A machine-readable citation template is provided in CITATION.cff.

Repository

https://github.com/atakiltibrhanu-glitch/GeoAI_project
