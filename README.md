# Statistical Analysis and Predictive Feature Engineering of California Seismicity (1995-2025)

This repository contains a comprehensive statistical and machine learning framework designed to analyze seismic activity and identify predictive precursors to moderate-to-large earthquakes (M ≥ 4.0). By bridging statistical seismology with gradient boosting techniques, this study develops physically interpretable features that capture underlying tectonic stress dynamics.

##  Project Overview
Earthquake forecasting is a complex problem due to the dynamic nature of fault systems. This project moves beyond standard data-driven approaches by incorporating fundamental principles of statistical physics to engineer robust features for a predictive XGBoost model.

### Key Contributions:
* **Aki’s Maximum Likelihood Estimation (MLE):** Implemented MLE over traditional least squares to yield a precise regional b-value (~0.81).
* **"Seismic Ignition" Identification:** Discovered rapid short-term stress accumulation phases preceding the 2019 M7.1 Ridgecrest earthquake.
* **Physics-Informed Feature Engineering:** Developed spatiotemporal features including rolling b-values, cumulative Benioff strain, and spatial variance.
* **Robust Performance:** Achieved a **Recall of 0.73** and an **ROC-AUC of 0.862** in detecting moderate-to-large events.

##  Methodology

### 1. Data Quality & Preprocessing
* **Source:** USGS Earthquake Catalog (California, 1995-2025).
* **Filtering:** Applied strict quality constraints (Azimuthal Gap < 180°, Horizontal Error < 10km, Magnitude Error < 0.3) to eliminate sensor noise.
* **Declustering:** Utilized the Gardner-Knopoff (1974) windowing algorithm to isolate independent mainshocks from dependent aftershock sequences.

### 2. Statistical Analysis
* **Gutenberg-Richter Law:** Validated the magnitude-frequency distribution using Monte Carlo bootstrapping to confirm a power-law fit (p > 0.05).
* **Omori’s Law:** Modeled aftershock decay post-Ridgecrest, finding a decay exponent (p) of ~1.14.
* **Rolling b-value:** Used as an "inverse stress meter"—a sudden drop in b-value indicates fault locking and stress accumulation.

### 3. Predictive Framework
The study uses a spatial gridding approach (0.5° × 0.5° cells) to transform raw seismic catalogs into a structured rolling feature matrix. 
* **Model:** Extreme Gradient Boosting (XGBoost).
* **Target:** Binary classification—occurrence of an M ≥ 4.0 event within the next 30 days.
* **Leakage Prevention:** Employed a strict time-based split (Cutoff: Jan 1, 2020) and a lag-1 shift on all rolling calculations.

##  Results
* **Recall:** 0.73
* **ROC-AUC:** 0.862
* **Feature Importance:** Identified rolling b-value and spatial variance as the most critical predictors of impending ruptures.

##  Built With
* **Python:** Primary programming language.
* **XGBoost:** Gradient boosting library for classification.
* **Scipy/Numpy:** For statistical computations and MLE.
* **Matplotlib/Seaborn:** For spatiotemporal visualization and epicenter mapping.

##  Authors
* **Avantika Patil** (EP23BTECH11004)
* **Jaideep Nirmal AJ** (EP23BTECH11013)
* *Date: April 15, 2026*

##  References
1. Gutenberg, B. & Richter, C. F. (1944). "Frequency of earthquakes in California."
2. Aki, K. (1965). "Maximum likelihood estimate of b."
3. Gardner, J. K. & Knopoff, L. (1974). "Is the sequence of earthquakes in southern California... Poissonian?"
