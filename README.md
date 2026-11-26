# STEM Mismatch Ecuador

Machine learning and statistical analysis of field-of-study mismatch among employed STEM university graduates in Ecuador using ENEMDU microdata (2021–2025).

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Machine%20Learning-blue)
![LaTeX](https://img.shields.io/badge/LaTeX-008080?style=flat&logo=latex&logoColor=white)
![Status](https://img.shields.io/badge/Research-In%20Progress-orange)

## Overview

Obtaining a university degree does not necessarily guarantee employment in an occupation related to one's academic background. This phenomenon, known as field-of-study mismatch or horizontal educational mismatch, represents an important challenge for understanding the relationship between higher education and the labour market.

This research investigates field-of-study mismatch among employed university graduates in Science, Technology, Engineering, and Mathematics (STEM) in Ecuador.

Using official annual microdata from the National Survey of Employment, Unemployment, and Underemployment (ENEMDU) for the period 2021–2025, the project combines statistical analysis and supervised machine learning to examine occupational alignment and evaluate the predictive contribution of socioeconomic, demographic, and educational characteristics.

The research emphasizes methodological transparency, temporal validation, statistical robustness, and reproducibility.

## Research Question

How accurately can machine learning models classify field-of-study mismatch among employed university graduates with STEM degrees in Ecuador during 2021–2025, and which socioeconomic, demographic, and educational variables contribute most to this classification?

## Research Objectives

### General Objective

Develop and compare machine learning models to classify field-of-study mismatch among employed STEM university graduates in Ecuador during 2021–2025.

### Specific Objectives

- Collect, harmonize, and process annual ENEMDU microdata.
- Construct a documented indicator of field-of-study mismatch based on educational and occupational classifications.
- Estimate the prevalence of mismatch across demographic, educational, and geographical groups.
- Train and compare supervised machine learning classifiers using temporal validation.
- Identify the variables with the greatest contribution to predictive performance.
- Evaluate the robustness of the results through sensitivity analysis and statistical uncertainty estimation.
- Document a reproducible computational workflow for future research.

## Data Sources

The research uses publicly available official microdata and classification systems.

| Source | Description |
|---|---|
| ENEMDU | Annual employment and socioeconomic microdata, 2021–2025 |
| CNTP | National Classification of Professional Degrees |
| CIUO-08 | International Standard Classification of Occupations |
| ISCED-F 2013 | International classification of fields of education and training |

The primary data provider is the National Institute of Statistics and Censuses of Ecuador (INEC).

Official resources:

- [INEC — Ecuador en Cifras](https://www.ecuadorencifras.gob.ec/)
- [ENEMDU Annual Statistics](https://www.ecuadorencifras.gob.ec/enemdu-anual/)
- [INEC Data Repository](https://anda.inec.gob.ec/)
- [Integrated Classification System](https://aplicaciones2.ecuadorencifras.gob.ec/SIN/)
- [International Standard Classification of Occupations](https://isco.ilo.org/en/isco-08/)

## Study Population

The target population consists of employed individuals holding university or postgraduate qualifications in STEM fields in Ecuador.

The operational definition of STEM includes the following ISCED-F 2013 categories:

| Code | Field of study |
|---|---|
| 05 | Natural Sciences, Mathematics and Statistics |
| 06 | Information and Communication Technologies |
| 07 | Engineering, Manufacturing and Construction |

Records with insufficient information to determine educational or occupational compatibility are excluded from the corresponding analysis.

## Methodology

The study follows a quantitative, observational, descriptive, and predictive research design.

### Data Preprocessing

- Annual microdata extraction and harmonization.
- Validation of educational and occupational codes.
- Identification of eligible STEM university graduates.
- Missing-value analysis and treatment.
- Survey-weight processing.
- Auditing of potentially related observations.
- Prevention of information leakage.

### Target Variable

Field-of-study mismatch is represented as a binary classification problem:

| Class | Description |
|---|---|
| 0 | Occupation compatible with the field of study |
| 1 | Occupation not compatible with the field of study |

The target variable is constructed using a documented normative correspondence between educational fields and occupational groups, adapted from previous research.

This approach measures occupational compatibility under an explicit classification rule. It does not directly measure individual skills, job satisfaction, or educational overqualification.

### Statistical Analysis

The descriptive component examines:

- Annual weighted mismatch prevalence.
- Differences across STEM fields.
- Gender disparities.
- Geographical distribution.
- Age groups.
- University qualifications.
- Labour income.
- Employment conditions.
- Occupational distribution among mismatched graduates.

Survey expansion factors are incorporated into population-oriented estimates, with appropriate consideration of the sampling design.

### Machine Learning Models

Three supervised learning algorithms are evaluated:

| Model | Purpose |
|---|---|
| Logistic Regression | Interpretable statistical baseline |
| Random Forest | Nonlinear ensemble classification |
| XGBoost | Gradient-boosted tree classification |

A constant classifier is also included as a reference baseline.

### Temporal Validation

The datasets are separated chronologically to reduce information leakage and evaluate performance across different periods.

| Period | Purpose |
|---|---|
| 2021–2023 | Model training and hyperparameter optimization |
| 2024 | Validation, probability calibration, and threshold selection |
| 2025 | Temporal test evaluation |

Data preprocessing and model fitting are performed using the corresponding development partitions.

### Evaluation Metrics

Predictive performance is assessed using:

- Average Precision (AP)
- ROC-AUC
- Precision
- Recall
- Specificity
- F1-Score
- Balanced Accuracy
- Brier Score
- Confusion Matrix
- Probability Calibration

### Model Interpretability

The contribution of individual predictors is examined through:

- Permutation feature importance.
- Logistic regression coefficients.
- SHAP values, where applicable.

Predictive associations are interpreted without attributing causal relationships.

### Sensitivity Analysis

Additional experiments assess the robustness of the results under different methodological conditions:

1. Exclusion of the 2021 dataset.
2. Training without survey weights.
3. Exclusion of the STEM field from the predictor set.
4. Conservative exclusion of potentially overlapping household records.
5. Comparison of alternative measurement rules when documentary support is available.

Bootstrap procedures are used to estimate statistical uncertainty where the available sampling information permits.

## Computational Workflow

The computational pipeline consists of the following stages:

1. Raw ENEMDU microdata.
2. Data auditing and preprocessing.
3. STEM population selection.
4. Educational–occupational correspondence.
5. Binary target construction.
6. Descriptive statistical analysis.
7. Temporal data partitioning.
8. Model training and optimization.
9. Predictive performance evaluation.
10. Model interpretation and sensitivity analysis.
11. Export of scientific tables and figures.

## Repository Structure

```text
STEM-Mismatch-Ecuador/
├── data/
│   ├── ENEMDU annual datasets (2021–2025)
│   ├── titulos2019.xlsx
│   └── ciuo.xlsx
├── ENEMDU_STEM_v2.ipynb
├── outputs_v2/
└── README.md
```

The `data/` directory contains the original datasets and classification catalogues.

The `outputs_v2/` directory is generated by the notebook and contains the resulting statistical tables, evaluation metrics, figures, and experimental outputs.

## Technologies

| Technology | Application |
|---|---|
| Python | Computational implementation |
| Pandas | Data manipulation and preprocessing |
| NumPy | Numerical computation |
| Scikit-learn | Machine learning and evaluation |
| XGBoost | Gradient boosting |
| Matplotlib | Scientific visualization |
| SHAP | Model interpretability |
| Jupyter Notebook | Reproducible experimental workflow |
| LaTeX / MDPI | Scientific manuscript preparation |
| Mendeley / BibTeX | Reference management |

## Installation and Execution

Create and activate a Python virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the required dependencies:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib openpyxl joblib shap jupyter ipykernel
```

Download the five annual ENEMDU datasets and the two classification catalogues from the official INEC repositories.

Place all seven files inside the `data/` directory, preserving their original filenames.

Open `ENEMDU_STEM_v2.ipynb` in Jupyter Notebook or Visual Studio Code, select the corresponding Python environment, and execute all cells sequentially.

The experimental results will be exported automatically to `outputs_v2/`.

## Research Scope and Limitations

This research focuses on observed field-of-study mismatch among employed STEM university graduates.

The study does not attempt to:

- Establish causal relationships between individual characteristics and occupational mismatch.
- Estimate the number of unfilled STEM vacancies.
- Determine the shortage or oversupply of professionals in specific occupations.
- Predict individual employment trajectories before graduation.

The interpretation of the results is subject to the limitations of secondary survey data, occupational classification rules, sampling design, and the identification of potentially repeated observations.

## Reproducibility and Ethics

The project is designed to support transparent and reproducible research through documented preprocessing procedures, explicit classification rules, fixed experimental seeds, and chronological evaluation.

All analyses are based on publicly available anonymized microdata. No attempt is made to identify individual survey respondents.

The resulting models are intended for academic research and statistical analysis, not automated individual employment decisions.

## Authors

- **Harolt S. Farinango Palacios** — ORCID: [0000-0001-5682-9705](https://orcid.org/0000-0001-5682-9705)
- **Steven Paúl Rodríguez Guerrero** — ORCID: [0009-0008-1980-6086](https://orcid.org/0009-0008-1980-6086)
- **Kevin Andrés Erazo Yépez** — ORCID: [0000-0002-1691-1947](https://orcid.org/0000-0002-1691-1947)

### Institutional Affiliation

School of Mathematical and Computational Sciences  
Yachay Tech University  
San Miguel de Urcuquí, Ecuador

## Research Status

This repository is part of an ongoing academic research project. The statistical analysis, experimental results, scientific manuscript, and supporting materials are being developed and documented.

The final manuscript will present the complete methodology, empirical findings, discussion, conclusions, and bibliographic references.

---

Developed as an academic research project at Yachay Tech University, Ecuador — 2026.
