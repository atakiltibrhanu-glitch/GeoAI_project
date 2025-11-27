# Explainable GeoAI — Starter Project


This repository contains a starter, working pipeline for downloading and preprocessing free Tel-Aviv datasets (OSM, Mapillary, CBS, GTFS, Sentinel/Copernicus DEM), building a spatial graph, training a Graph Neural Network for walkability prediction, and running explainability/fairness modules.


Structure overview
- `data/` raw downloads
- `src/preprocessing/` dataset downloaders and cleaners
- `src/features/` graph construction and feature engineering
- `src/gnn_model/` PyTorch Geometric model, training, utils
- `src/explainability/` explainers and fairness audits
- `src/visualization/` quick plotting utilities
- `run_pipeline.py` orchestrator


How to run
1. Create environment: `conda env create -f environment.yml`
2. Activate: `conda activate geoai-walkability`
3. Configure `config/paths.yaml` and `config/settings.yaml` (place your Mapillary token in settings)
4. Run: `python run_pipeline.py --step download`


License: MIT — use freely for research. Cite dataset providers (OSM, Mapillary, CBS, Copernicus).
