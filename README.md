# Differential Privacy Synthetic Tabular Data Generation for Federated Learning

Bachelor's thesis project (UPC, FIB). Tutor: Prof. Cecilio Angulo.

This project extends a UMAP-based synthetic healthcare data generator to a **federated** multi-hospital setting and adds **(ε, δ)-Differential Privacy** to every quantity shared between hospitals, so institutions can collaborate without ever exchanging raw patient records. Two generators are studied — a *partially synthetic* pipeline (Pipeline A) and a *fully synthetic* one (Pipeline B) — each evaluated in three settings: centralized, federated, and federated + DP. Experiments use the PI-CAI prostate cancer dataset, measuring fidelity, downstream utility (TSTR), and the privacy budget tracked by a custom privacy accountant.

## Repository contents

- `UMAP_data_generation*.ipynb` — Pipeline A (partially synthetic): centralized, federated, and federated + DP variants.
- `Fully_UMAP_data_generation*.ipynb` / `Federated_UMAP*` — Pipeline B (fully synthetic): centralized, federated, and federated + DP variants.
- `Use_case_A–D.ipynb` — additional clinical scenarios (varying missingness, different missing feature per hospital, PSAD reconstruction, small-hospital augmentation).
- `marksheet_minimal.csv` — preprocessed PI-CAI data used by the notebooks.

## Requirements

Python 3.10 with `numpy`, `pandas`, `scikit-learn`, `umap-learn`, `matplotlib`. Open the notebooks in Jupyter and run top to bottom.
