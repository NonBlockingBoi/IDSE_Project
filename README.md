# IDSE Project

Repository containing two machine learning and data science projects developed by **Alluri Akash Varma (EC24I2027)**, **Lohith Chandra Gogineni (EC24I1006)**, and **Krishna Prakash (EC24I2028)**:

1. **WM-811K Wafer Map Defect Classification (`WaferResNet`)** — A 9-class PyTorch deep learning pipeline for classifying semiconductor wafer bin maps.

2. **Last Bet (`Madras_Race_Club.html`)** — An interactive, single-file 3D horse-racing game that teaches multiple linear regression and Ordinary Least Squares (OLS).

## Repository Structure

```
IDSE_Project/
├── Dataset                        # Link / reference to the WM-811K (LSWMD.pkl) wafer map dataset
├── WM811K_CNN.ipynb               # PyTorch Colab notebook implementing the 9-stage WaferResNet pipeline
├── WM811K_WaferResNet_Report.pdf  # 7-page technical report documenting the pipeline, metrics, and future work
├── Madras_Race_Club.html          # Self-contained HTML5 + Three.js interactive regression game ("Last Bet")
├── Madras_Race_Club.md            # Detailed gameplay, feature table, and code structure guide for Last Bet
└── README.md                      # Root repository overview and project structure

```

## Projects Overview

### 1. WM-811K Wafer Map Defect Classification

* **Notebook:** [`WM811K_CNN.ipynb`](https://github.com/NonBlockingBoi/IDSE_Project/blob/main/WM811K_CNN.ipynb)

* **Report:** `WM811K_WaferResNet_Report.pdf`

* **Dataset:** [Dataset](https://www.google.com/search?q=./Dataset) — WM-811K (`LSWMD.pkl`, 811,457 raw wafers; 172,950 labeled across `none` + 8 defect classes)

* **Model & Results:** Single-model `WaferResNet` (174,905 parameters, 0.6672 MB FP32) trained on `56×56` nearest-neighbor resized wafer maps with stratified splitting prior to geometric augmentation, achieving **96.32% test accuracy** and **0.86 macro-F1** on the untouched 25,943-sample test set.

### 2. Madras_Race_Club — Linear Regression Racing Game

* **App:** `Madras_Race_Club.html`

* **Documentation:** [Madras_Race_Club.md](https://www.google.com/search?q=./Madras_Race_Club.md)

* **Overview:** Players start with ₹25,000 across 6 races, buy up to 5 racing clues per race, tune regression weights manually or via an in-browser OLS solver (`Auto-fit`), bet on an 8-horse field, and watch the race live in a **Three.js** 3D oval stadium.

## Quick Start

* **Wafer Map Pipeline:** Open `WM811K_CNN.ipynb` in Google Colab (GPU runtime recommended) and run the cells sequentially to download `LSWMD.pkl` via `kagglehub`, train `WaferResNet`, and generate evaluation plots.

* **Last Bet Game:** Open `Madras_Race_Club.html` directly in any modern web browser (requires internet access on load for the Three.js `r128` CDN). See [Madras_Race_Club.md](https://www.google.com/search?q=./Madras_Race_Club.md) for full rules and code breakdown.
