# War & Economic Impact
### From Data Insight to Prediction

> A full data science pipeline exploring the economic footprint of armed conflict across 100,000 observations — from raw data to predictive modelling.

![Python](https://img.shields.io/badge/Python-3.13.9-blue)
![pandas](https://img.shields.io/badge/pandas-data--wrangling-lightgrey)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![rows](https://img.shields.io/badge/dataset-100%2C000%20rows-green)
[![GitHub](https://img.shields.io/badge/GitHub-4850--Final--Project-181717?logo=github)](https://github.com/J2ckyo/4850-Final-Project)

---

## Overview

| | |
|---|---|
| **Dataset** | [war_economic_impact_dataset.csv](https://www.kaggle.com/datasets/likithagedipudi/war-economic-and-livelihood-impact-dataset) — 100,000 rows, 35 features (28 original) |
| **Regions** | Africa · East Asia · Europe · Middle East · South Asia |
| **Conflict Types** | Asymmetric War · Civil War · Interstate War · Counter-insurgency · World War |
| **Years Covered** | 1939 – 2026 |
| **Null Values** | 0 |

**Research Questions**

- **Regression** — Which economic indicators best predict the total financial scale of a conflict?
- **Classification** — Can a conflict's economic damage profile predict whether it is still ongoing or resolved?

---

## Repository Files

### 📋 `Final_Project_Description.ipynb` — *Start here*
The project brief from the course Data Science 4850. Contains all formal requirements, grading criteria, and deliverable specifications. Read this first to understand what the project is evaluating and why each section exists.

- Dataset requirements and minimum thresholds
- Wrangling, EDA, and modelling specifications
- Grading rubric and evaluation emphasis
- Deliverable checklist and presentation guidelines

---

### ⚙️ `Project_Code.ipynb` — *Source code*
The complete, fully-runnable analysis notebook. Executes end-to-end from raw CSV to final model metrics. Every code section is preceded by a markdown cell explaining the objective and the reasoning behind each step.

- Data wrangling & feature engineering (7 steps)
- EDA — 4 targeted visualisations with written interpretations
- Statistical testing — Chi-square, Kruskal-Wallis H, Mann-Whitney U
- Regression — Linear Regression & Random Forest on `log(Cost_of_War_USD)`
- Classification — Logistic Regression & Random Forest on Conflict Status (AUC 0.937)
- K-Means clustering (k=2) with PCA projection

---

### 📄 `Written_Report.ipynb` — *Written report*
A concise written report covering every section of the project in plain language. Structured for a non-technical audience portraying the findings, results, and what they mean in practice.

- Project Overview — dataset, questions, feature engineering
- Key Visuals — purpose and finding for each figure
- Statistical Results — all three tests with effect sizes
- Model Performance Table — regression and classification metrics
- Interpretation & Conclusion — findings, limitations, and next steps

---

### 🤖 `AI_Appendix.ipynb` — *AI Appendix*
A short written report covering the use of AI for academic integrity and transparency. 

- How AI Tools Were Used — boilerplate & repetitive writing, plot enhancements, report structuring
- What I wrote — Data pipeline including, data wrangling & feature engineering, EDA, statistical tests, machine learning pipeline, K-means clustering, and all analytical findings. 

---

## Pipeline


Data Wrangling → EDA → Hypothesis Testing → Regression → Classification → Clustering → Interpretation


---

## Key Results

### Regression — Target: `log(Cost_of_War_USD)`

| Model | Val RMSE | Test RMSE | Test MAE | Test R² |
|---|---|---|---|---|
| Linear Regression | 0.9600 | 0.9708 | 0.7250 | −0.001 |
| Random Forest (100 trees) | 0.9726 | 0.9859 | 0.7510 | −0.032 |

> **Note:** R² ≈ 0 is a finding, not a failure. The economic damage a war produces does not predict how expensive that war is to fight. Financial scale is driven by geopolitical and military factors outside this dataset.

### Classification — Target: `Status` (Ongoing / Resolved)

| Model | Val Accuracy | Test Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|---|
| Logistic Regression | 0.8221 | 0.8231 | 0.8243 | 0.8582 | 0.8409 | **0.9362** |
| Random Forest (150 trees) | 0.8189 | 0.8226 | 0.8325 | 0.8442 | 0.8384 | **0.9366** |

> **Note:** Duration was excluded as a feature — all ongoing conflicts share `End_Year = 2026`, making it a data leak. Only economic damage indicators were used.

### Statistical Tests

| Test | Question | Statistic | p-value | Effect Size | Decision |
|---|---|---|---|---|---|
| Chi-square | Black market activity → Profiteering | χ² = 2.07 | 0.56 | Cramér's V = 0.005 | Fail to reject H₀ |
| Kruskal-Wallis H | GDP change across conflict types | H = 25,054 | < 0.001 | η² = 0.251 (large) | Reject H₀ |
| Mann-Whitney U | Poverty spike: Ongoing > Resolved | U = 1.62B | < 0.001 | r = −0.309 | Reject H₀ * |

> \* Direction is reversed — resolved conflicts score higher due to catastrophic historical wars. An era-level control is needed.

---

## Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/J2ckyo/4850-Final-Project.git
cd 4850-Final-Project

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# 3. Place the dataset in the project root
#    war_economic_impact_dataset.csv

# 4. Run the notebook
jupyter notebook Project_Code.ipynb
```

---

## Key Findings

1. **Conflict type explains 25% of GDP variance** (η² = 0.25) — the dominant structural predictor. Humanitarian responses calibrated by conflict archetype would be better targeted than uniform interventions.
2. **War cost cannot be predicted from economic damage** (R² ≈ 0) — financial scale requires geopolitical and military data not present in this dataset.
3. **Conflict status IS predictable from economic footprint** (AUC = 0.937) — geography and conflict type lead, with unemployment spike and GDP decline as the strongest purely economic signals.
4. **The decision boundary is linear** — Logistic Regression matches Random Forest on AUC, meaning no complex interactions are needed to separate ongoing from resolved conflicts.

---

*Python · pandas · scikit-learn · seaborn*
