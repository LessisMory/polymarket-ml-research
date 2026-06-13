# Polymarket Inverse Reinforcement Learning Analysis

This repository contains a research workflow for modeling Polymarket trading behavior with engineered market microstructure features and supervised/sequence models used as inputs for inverse reinforcement learning analysis.

## Repository Layout

```text
.
├── data/                  # Local parquet datasets and intermediate feature tables
├── models/                # Trained model checkpoints and exported estimators
├── notebooks/             # Numbered research workflow notebooks
├── reports/               # Figures, papers, and presentation artifacts
└── src/polymarket_irl/    # Shared Python package scaffold for reusable project code
```

## Notebook Workflow

Run notebooks from the `notebooks/` directory. Relative paths are organized so notebooks read datasets from `../data/` and write trained model artifacts to `../models/`.

| Notebook | Purpose |
| --- | --- |
| `00_scratch_f_data_engineering.ipynb` | Scratch placeholder from the original workspace |
| `01_data_engineering.ipynb` | Base data ingestion and engineering |
| `02_transaction_engineering.ipynb` | Transaction-level feature engineering |
| `03_merge_orderbook_hft.ipynb` | Order-book and HFT feature merge |
| `04_feature_engineering.ipynb` | Model feature generation |
| `05_feature_filtering.ipynb` | Feature filtering and final LSTM dataset creation |
| `06_attach_execution_prices.ipynb` | Execution price attachment |
| `07_train_mlp.ipynb` | MLP alpha model training |
| `08_train_rnn.ipynb` | RNN alpha model training |
| `09_train_lstm.ipynb` | LSTM alpha model training |
| `10_train_xgboost.ipynb` | XGBoost alpha model training |
| `99_experimental_lstm_copy.ipynb` | Experimental LSTM copy retained for reproducibility |

## Setup

Create an environment and install dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install -e .
```

Then start Jupyter:

```bash
jupyter lab
```

## Data And Model Artifacts

The local datasets are large and should not be committed directly to GitHub. The `.gitignore` keeps parquet datasets, trained checkpoints, local caches, and OS metadata out of version control. For a production repository, use a durable artifact store such as DVC, S3, Hugging Face Datasets, or a private release asset workflow.

## GitHub Authentication

The local GitHub CLI account is present but currently has an invalid token. Re-authenticate with:

```bash
gh auth login -h github.com
```

After re-authentication, confirm access with:

```bash
gh auth status
```
