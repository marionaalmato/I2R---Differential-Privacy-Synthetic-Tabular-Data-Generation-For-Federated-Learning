# Differential Privacy Synthetic Tabular Data Generation for Federated Learning

Bachelor's thesis project — Facultat d'Informàtica de Barcelona (UPC). Tutor: Prof. Cecilio Angulo.

## Overview

Machine learning in healthcare is limited by the scarcity of large, diverse datasets: medical records are sensitive, and legal and ethical constraints make sharing them between hospitals very difficult. Synthetic data is a common workaround, but on its own it gives no formal privacy guarantee and can still leak information about real patients.

This project takes an existing UMAP-based synthetic data generator and extends it so that (1) several hospitals can collaborate **without ever exchanging raw records** (Federated Learning), and (2) every quantity shared between them carries a formal **(ε, δ)-Differential Privacy** guarantee, tracked by a custom privacy accountant.

Two generators are studied, each evaluated in three settings — **centralized**, **federated**, and **federated + DP**:

- **Pipeline A (partially synthetic):** one reference hospital holds complete records; the others are missing one feature, which is the only column synthesised.
- **Pipeline B (fully synthetic):** every feature is generated, so the output contains no real patient records.

The method is evaluated on the PI-CAI prostate cancer dataset, measuring fidelity (Kolmogorov–Smirnov distance), downstream utility (train-on-synthetic / test-on-real), and the cumulative privacy budget.

## Repository structure

**`Code_partially/` — Pipeline A (partially synthetic)**

- `UMAP_data_generation.ipynb` — centralized baseline
- `UMAP_data_generation_federated_moreHospitals.ipynb` — federated variant
- `UMAP_data_generation_federated_moreHospitals_DP.ipynb` — federated + Differential Privacy

**`Code_fully/` — Pipeline B (fully synthetic)**

- `Fully_UMAP_data_generation.ipynb` — centralized baseline
- `Federated_UMAP_data_generation.ipynb` — federated variant
- `Federated_UMAP_DP_data_generation.ipynb` — federated + Differential Privacy

Each notebook is self-contained and can be run top to bottom to reproduce the corresponding results (UMAP embeddings, validation, synthetic samples, and the fidelity/utility metrics reported in the thesis).

## Data

Experiments use the public PI-CAI prostate cancer dataset. The notebooks expect the preprocessed table (`patient_age`, `psa`, `psad`, `psad_computed`, `prostate_volume`, and the binary target `case_csPCa`); the federated experiments simulate multiple hospitals via a stratified split on the target label.

## Author

Mariona Almató Baucells — UPC, June 2026.
