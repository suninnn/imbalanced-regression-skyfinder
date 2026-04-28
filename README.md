# SkyFinder DIR Temperature Regression

This project adapts **Distributionally Robust Regression (DIR)** to the SkyFinder temperature prediction task. The goal is to evaluate whether imbalance-aware regression methods can improve prediction performance on underrepresented temperature ranges.

## Project Overview

SkyFinder contains outdoor sky images collected from multiple static cameras under diverse weather, lighting, and seasonal conditions. In this project, I formulate temperature prediction as an imbalanced regression problem, where some temperature ranges have many training samples while others are underrepresented.

The project evaluates the effectiveness of DIR components, including:

- **Label Distribution Smoothing (LDS)**
- **Feature Distribution Smoothing (FDS)**
- Vanilla regression baseline
- Imbalance-aware evaluation across many-shot, medium-shot, few-shot, and zero-shot temperature bins

## Main Findings

The vanilla baseline performs strongly on the overall dataset, especially in many-shot temperature regions. Applying LDS improves performance in sparse temperature regions, suggesting that smoothed label-density-based reweighting can help mitigate continuous label imbalance.

However, FDS does not consistently improve over LDS-only models in this setting. This may be because SkyFinder temperature prediction depends heavily on camera location, season, time, and weather context, making the feature distribution less smoothly aligned across neighboring temperature bins.

## Repository Structure

```text
.
├── SkyFinder_DIR_training.ipynb          # Main training and evaluation notebook
├── skyfinder_dir_training.py             # Python script version of the training pipeline
├── SkyFinderTemperatureRegression.ipynb  # Data preprocessing notebook
├── SkyFinder_DIR_Results.pdf             # Final project report
├── README.md
└── .gitignore
