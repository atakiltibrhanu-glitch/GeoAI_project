# Reproducibility Workflow

This file describes the intended public workflow for reproducing the COSIT analysis.

## 1. Acquire source data

Obtain pedestrian counts, weather, OpenStreetMap, GTFS/transit, and Sentinel-2 inputs from the authoritative sources described in `DATA_SOURCES.md`.

## 2. Build the harmonized feature table

Construct the common 21-feature contract documented in `FEATURES.md`.

Recommended minimum keys:

- city;
- sensor identifier;
- timestamp;
- observed pedestrian count;
- the 21 harmonized features.

Preserve source timestamps, coordinate reference systems, units, and missing-data decisions in the processing logs.

## 3. Create train-validation splits

Use independent 80/20 train-validation splits.

Robustness analysis should repeat the workflow over five random seeds and five independent splits, matching the study design.

## 4. Train city-specific CatBoost models

Train Zurich and Berlin separately while keeping the model configuration and preprocessing pipeline comparable across cities.

Do not add historical pedestrian-count lag features to the COSIT reproduction unless explicitly running a separate sensitivity experiment.

## 5. Compute model performance

Reproduce the reported R² values:

- Zurich: 0.76
- Berlin: 0.80

If additional metrics such as MSE, RMSE, or MAE are computed in a future release, label them as newly reported reproducibility metrics rather than implying that they appeared in the original COSIT paper.

## 6. Compute SHAP values

For each city:

1. compute SHAP values for the trained CatBoost model;
2. calculate mean absolute SHAP by feature for global importance;
3. preserve signed SHAP values for beeswarm/local interpretation;
4. normalize mean absolute importance **within city** by the maximum feature importance.

## 7. Compare cities

Compare normalized importance profiles.

For a descriptive difference:

```text
delta = Zurich normalized importance - Berlin normalized importance
```

Interpret this as a difference in within-city relative importance. It is **not** a significance test or standardized effect size.

## 8. Robustness analysis

Aggregate normalized SHAP importance and feature ranks across repeated runs. Report means, standard deviations, and rank ranges.

## 9. Generate figures

Expected public figures include:

- Zurich/Berlin study-area and sensor-location map;
- predicted-versus-observed performance figure;
- city-specific SHAP beeswarm plots;
- combined Zurich-Berlin beeswarm;
- normalized top-feature plots;
- normalized cross-city SHAP heatmap.

## Interpretation safeguards

- SHAP explains the trained model; it does not establish causality.
- A positive SHAP value pushes the model prediction upward for that observation.
- A negative SHAP value pushes the prediction downward.
- Raw SHAP magnitudes from separately trained city models should not be interpreted as directly comparable theoretical effect sizes.
- Sine/cosine time features should be interpreted jointly as phases of the daily cycle.
