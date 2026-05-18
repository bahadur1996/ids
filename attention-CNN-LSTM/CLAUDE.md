# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Python Environment

This project uses **Python 3.12.13** managed by `uv`, located at:
```
C:/Users/BA/AppData/Roaming/uv/python/cpython-3.12.13-windows-x86_64-none/python.exe
```

To install packages into this environment (required flag due to uv management):
```powershell
& "c:/Users/BA/AppData/Roaming/uv/python/cpython-3.12.13-windows-x86_64-none/python.exe" -m pip install <package> --break-system-packages
```

All notebooks must use the **Python 3.12.13** kernel in VS Code. If the kernel isn't available after fresh install, `ipykernel` must be installed first:
```powershell
& "c:/Users/BA/AppData/Roaming/uv/python/cpython-3.12.13-windows-x86_64-none/python.exe" -m pip install ipykernel -U --break-system-packages
```

## Installed Packages

- `torch 2.6.0+cu124`, `torchvision`, `torchaudio` (CUDA 12.4, GPU: NVIDIA GTX 1050 — 4 GB VRAM)
- `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `tqdm`

## Project Architecture

Implementation of the paper *"Deep learning for network security: an Attention-CNN-LSTM model"* (Alashjaee, Scientific Reports 2025) for network intrusion detection on the **Bot-IoT dataset**.

### Model Pipeline
```
Raw traffic flows (93 features)
    → Preprocessing & normalization
    → CNN layers           (spatial feature extraction)
    → LSTM layers          (temporal sequence modeling)
    → Attention mechanism  (feature importance weighting)
    → Classification output (Normal / DDoS / DoS / Reconnaissance / Theft)
```

### Notebook Sequence
| Notebook | Purpose |
|---|---|
| `01_setup_and_download.ipynb` | Environment check, dataset loading, EDA |
| `02_preprocessing.ipynb` | Feature encoding, normalization, train/val/test split *(to be created)* |
| `03_model.ipynb` | CNN-LSTM-Attention architecture definition *(to be created)* |
| `04_training.ipynb` | Training loop, checkpointing *(to be created)* |
| `05_evaluation.ipynb` | Metrics, confusion matrix, plots *(to be created)* |

### Dataset: Bot-IoT (UNSW 2018)
- **Location:** `data/raw/` — 4 CSV files, ~935 MB total, ~4 million records, 93 columns
- **Label columns:** `Attack` (binary), `Category` (attack family), `Subcategory` (specific type)
- **Class imbalance:** heavily skewed toward attack traffic — requires stratified sampling or class weights
- **Feature metadata:** `data/Features Explanation/Total Feature Description.xlsx`

### Key Data Notes
- The raw CSVs have **no header row** — the first row is data, not column names. Column names must be assigned manually from the feature description Excel file.
- Many columns have large amounts of missing values; dropping or imputing is required in preprocessing.
- Processed artifacts go in `data/processed/`; model checkpoints in `models/`; plots/metrics in `results/`.
