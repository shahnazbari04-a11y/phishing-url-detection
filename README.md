# Phishing URL Detection with Probabilistic & Bayesian Models

This repository explores phishing URL detection on the **PhiUSIIL Phishing URL Dataset** using three complementary probabilistic and Bayesian approaches:

1. **Gaussian Naïve Bayes (Baseline):** Fast discriminative/generative baseline evaluated with 10-fold stratified cross-validation.
2. **Bayesian Belief Network (`pgmpy`):** Structure learning via Hill Climb Search (`BicScore`), parameter estimation via `BayesianEstimator` (`BDeu`), and exact probabilistic inference using `VariableElimination`.
3. **Bayesian Logistic Regression (`pymc`):** Full posterior estimation and uncertainty quantification over key URL and webpage indicators (`URLSimilarityIndex`, `HasSocialNet`, `HasCopyrightInfo`, `HasDescription`, `IsHTTPS`), diagnosed with `arviz`.

---

## Dataset Overview

- **Source:** [PhiUSIIL Phishing URL Dataset](https://www.kaggle.com/datasets/ndarvind/phiusiil-phishing-url-dataset) (UCI Machine Learning Repository / Kaggle)
- **Size:** 235,795 rows × 56 columns
- **Target Variable (`label`):**
  - `1` (Legitimate): 134,850 samples (~57.2%)
  - `0` (Phishing): 100,945 samples (~42.8%)
- **Preprocessing:** High-cardinality string identifiers (`FILENAME`, `URL`, `Title`, `Domain`, `TLD`) are excluded prior to modeling. Continuous features such as `NoOfExternalRef` are discretized (`low`, `medium`, `high`) for discrete Bayesian Belief Network structure learning.

---

## Repository Structure

```text
├── notebooks/
│   └── phishing_bayesian_analysis.ipynb   # Main exploratory & modeling notebook
├── README.md                              # Project documentation
└── requirements.txt                       # Python dependencies
