# Results Summary

## Predictive performance

| City | R² |
| --- | ---: |
| Zurich | 0.76 |
| Berlin | 0.80 |

The COSIT paper reports R² as the primary predictive-performance metric. MSE, RMSE, and MAE are not currently reported in the final COSIT results.

## Leading normalized SHAP importance

Within each city, mean absolute SHAP importance is normalized by the city's highest-ranked feature.

### Zurich

| Feature | Normalized importance |
| --- | ---: |
| Hour (cos) | 1.00 |
| Facade continuity | 0.81 |
| Hour (sin) | 0.76 |
| Built volume density | 0.71 |
| Transit stop distance | 0.59 |

### Berlin

| Feature | Normalized importance |
| --- | ---: |
| Hour (cos) | 1.00 |
| Hour (sin) | 0.68 |
| Temperature | 0.64 |
| Street enclosure | 0.60 |
| Weekend | 0.40 |

## Interpretation

The common result is a strong temporal foundation in both cities.

Beyond time of day:

- Zurich has relatively stronger morphology and accessibility signals.
- Berlin has relatively stronger environmental, enclosure, and weekend signals.
- The cross-city differences are descriptive differences in **within-city relative importance**.
- They are not statistical effect sizes, significance tests, or causal estimates.

## Local SHAP patterns

In Zurich, facade continuity, built-volume density, and transit-stop distance have broad, mixed SHAP distributions. Their contributions are therefore less uniformly directional.

In Berlin, temperature shows a clearer directional pattern: higher temperatures tend to push the model prediction upward, while lower temperatures tend to push it downward.

## Robustness

Feature-ranking robustness is evaluated across five random seeds and five independent 80/20 train-validation splits.

Top-feature summaries:

### Zurich

| Feature | Mean normalized SHAP | SD | Rank range |
| --- | ---: | ---: | --- |
| Hour (cos) | 1.00 | 0.00 | 1–1 |
| Facade continuity | 0.81 | 0.04 | 2–3 |
| Hour (sin) | 0.76 | 0.03 | 2–4 |
| Built volume density | 0.71 | 0.05 | 3–5 |
| Transit stop distance | 0.59 | 0.06 | 4–6 |

### Berlin

| Feature | Mean normalized SHAP | SD | Rank range |
| --- | ---: | ---: | --- |
| Hour (cos) | 1.00 | 0.00 | 1–1 |
| Hour (sin) | 0.68 | 0.03 | 2–3 |
| Temperature | 0.64 | 0.05 | 2–4 |
| Street enclosure | 0.60 | 0.04 | 3–5 |
| Weekend | 0.40 | 0.05 | 4–6 |

## Main conclusion

> **Cities share daily rhythms, but they encode movement-relevant information through different urban configurations.**
