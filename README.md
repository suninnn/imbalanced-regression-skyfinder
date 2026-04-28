# SkyFinder DIR Temperature Regression

This project adapts **Distributionally Robust Regression (DIR)** to the SkyFinder temperature prediction task. It evaluates whether imbalance-aware regression methods improve performance on underrepresented temperature ranges.

## Overview

SkyFinder contains outdoor sky images collected from static cameras under different weather, lighting, and seasonal conditions. This project formulates temperature prediction as an imbalanced regression problem and compares a vanilla regression baseline with DIR-based methods using **Label Distribution Smoothing (LDS)** and **Feature Distribution Smoothing (FDS)**.

## Repository Structure

```text
.
├── code/
│   ├── 01_skyfinder_data_preprocessing.ipynb  # Data preprocessing
│   ├── 02_dir_training_evaluation.ipynb       # DIR training and evaluation
│   └── dir_training_pipeline.py               # Python training pipeline
├── metadata.csv                               # SkyFinder metadata
├── README.md
└── .gitignore
```

## Methods

| Model | Description |
|---|---|
| B1 | Vanilla regression baseline |
| D1 | DIR with LDS reweighting |
| D1_inv | DIR with inverse LDS reweighting |
| D2 | DIR with LDS and FDS |
| D2_inv | DIR with inverse LDS and FDS |

Evaluation uses **RMSE** and **MAE** across many-shot, medium-shot, few-shot, and zero-shot temperature bins.

## Main Findings

The vanilla baseline performs strongly overall, especially in many-shot regions. LDS improves performance in sparse temperature ranges, suggesting that label-density-based reweighting helps mitigate continuous label imbalance. FDS does not consistently improve over LDS-only models, likely because SkyFinder temperature prediction depends on camera location, season, time, and weather context.


## How to Run

1. Prepare the SkyFinder image folders and metadata.
2. Run `code/01_skyfinder_data_preprocessing.ipynb`.
3. Run `code/02_dir_training_evaluation.ipynb`.
4. Use `code/dir_training_pipeline.py` as the script version of the training pipeline if needed.
