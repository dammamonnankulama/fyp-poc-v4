# Accident Severity PoC

Proof of concept for *An Intelligent Traffic Violation Management System for Sri Lanka with ML-Based Dynamic Severity Assessment and Driver Risk Scoring* (BEng Software Engineering, IIT / University of Westminster).

Dataset: Road Traffic Accident records from the Addis Ababa Sub-City police departments (Kaggle, CC BY 4.0).

> **The dataset is not included in this repository.** Download `RTA Dataset.csv` from Kaggle and place it at `data/raw/RTA Dataset.csv`. Running notebook 02 regenerates `data/processed/`.

## Notebooks

Run them in order. Each one reads the previous one's output.

| Notebook | Purpose | Output |
|---|---|---|
| `notebooks/01_data_exploration.ipynb` | Data quality, target imbalance, temporal/context patterns, leakage review | `reports/figures/*.png` |
| `notebooks/02_data_preprocessing.ipynb` | Cleaning, feature engineering, Model 1 feature selection, validation | `data/processed/*.csv`, `preprocessing_metadata.json` |

## Run locally (conda)

One-time setup:

```bash
conda env create -f environment.yml
conda activate accident-severity-poc
python -m ipykernel install --user --name accident-severity-poc --display-name "Python (accident-severity-poc)"
```

Then either:

- **VS Code:** open a notebook and pick the kernel **Python (accident-severity-poc)** (top right), or
- **Browser:** `conda activate accident-severity-poc && jupyter lab`

If `environment.yml` changes later: `conda env update -f environment.yml --prune`

## Run on Google Colab

1. Upload this whole project folder to Google Drive as `MyDrive/fyp-poc-v4`.
2. Open a notebook from Drive with Google Colab.
3. Run the first code cell. It mounts Drive and sets the paths. If you put the folder somewhere else, edit `PROJECT_ROOT` in that cell.

Colab already has pandas, scikit-learn, matplotlib and scipy, so notebooks 01–02 need no extra installs.

## Project layout

```
data/raw/          original dataset (never modified)
data/processed/    cleaned outputs from notebook 02
notebooks/         step-by-step analysis and modelling
reports/figures/   charts saved by the notebooks
models/            trained models (later)
src/               reusable code (later)
tests/             pytest tests (later)
```
