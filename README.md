# Automated Machine Learning Pipeline for Rare-Source Classification (MIR/FIR)

**Author:** Jonathan Raghoo (BSc Hons Physics & Astronomy | BSc Physics & Applied Mathematics, University of Pretoria)  
**Links:** [LinkedIn](https://www.linkedin.com/in/jonathan-raghoo-703473208) | [GitHub](https://github.com/jraghoo42)

---

## 📌 Project Overview & Quantitative Relevance
This repository contains an end-to-end data engineering and machine learning pipeline designed to identify and classify rare astronomical sources—specifically **Hydroxyl Megamaser (OHM) host galaxies**—across noisy, high-dimensional Mid-Infrared (MIR) and Far-Infrared (FIR) survey catalogues.

From a **Data Science and Quantitative Modelling** perspective, this research solves core production data challenges analogous to **financial fraud detection, credit default prediction, and rare-event risk modelling**:
* **Multi-Source Data Integration:** Cross-matching and reconciling heterogeneous catalogues with varying spatial resolutions and coverage.
* **Severe Class Imbalance & Missing Data:** Engineering features and imputation strategies where the target positive class represents a tiny fraction of the overall population.
* **High-Dimensional Feature Selection:** Isolating statistically significant predictors and eliminating multicollinearity using **Lasso Regression**, **PCA**, **t-SNE**, and **UMAP**.
* **Supervised & Unsupervised Classification:** Training, tuning, and validating **Random Forest Classifiers** and **K-Means** clustering models to optimize precision-recall trade-offs.

---

## 📂 Repository Structure

| Notebook | Stage | Key Responsibilities & Methods |
| :--- | :--- | :--- |
| **`Cross_matching_FINAL.ipynb`** | **1. Data Engineering & Cross-Matching** | Executes spatial and positional cross-matching across multi-wavelength astronomical catalogues using `astropy`, `pandas`, and `numpy`. Handles duplicate resolution, quality-flag filtering, and construction of unified master tables. |
| **`Master_code_Mid-IR.ipynb`** | **2. Mid-IR Feature Engineering & EDA** | Performs exploratory data analysis (EDA), color-index feature engineering, missing-value imputation, feature scaling, and manifold learning (**PCA, t-SNE, UMAP**) alongside **Lasso Regression** on Mid-Infrared photometric features. |
| **`AKARI_ML.ipynb`** | **3. Far-IR Integration & ML Classification** | Integrates Far-Infrared survey data from the **AKARI** catalogue. Implements supervised classification (**Random Forest**) and unsupervised clustering (**K-Means**) via `scikit-learn`, evaluating model performance through cross-validation, confusion matrices, and feature importance ranking. |

---

## 🛠️ Tech Stack & Environment
* **Language:** Python 3
* **Data Manipulation & Math:** `pandas`, `numpy`, `astropy`
* **Machine Learning & Dimensionality Reduction:** `scikit-learn` (Random Forest, K-Means, Lasso, PCA, t-SNE), `umap-learn` (UMAP)
* **Visualization:** `matplotlib`, `seaborn`
* **Compute Infrastructure:** Jupyter Notebooks, Linux (WSL), Slurm High-Performance Computing (HPC)

---

## 🚀 Key Methodology Workflow
1. **Catalogue Ingestion & Cross-Matching:** Raw photometric flux and magnitude measurements are ingested and spatially cross-matched to link optical/radio target identifications with Mid-IR and Far-IR (AKARI) photometry.
2. **Preprocessing & Feature Engineering:** Flux ratios and infrared color indices are computed to capture underlying spectral energy distributions. Outliers and non-detections are handled systematically prior to standardization.
3. **Dimensionality Reduction & Feature Selection:** High-dimensional photometric feature spaces are projected into lower-dimensional manifolds using **PCA**, **t-SNE**, and **UMAP** to inspect cluster separability, while **Lasso ($L_1$) regularization** shrinks redundant features.
4. **Model Training & Evaluation:** Supervised **Random Forest** models are trained to distinguish OHM host galaxies from non-OHM background populations, evaluating decision boundaries and feature importances to identify the strongest MIR/FIR diagnostic indicators.
