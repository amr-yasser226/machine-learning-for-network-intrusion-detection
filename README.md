# Machine Learning for Network Intrusion Detection

This repository implements a reproducible pipeline to detect network intrusions, comparing **Label Encoding** vs. **One‑Hot Encoding** and culminating in ensemble methods. The notebooks walk through data ingestion, cleaning, feature engineering, model training, and evaluation.

## Repository Structure

```

.
├── Data
│   └── Project\_Phase1\_before\_cleaning.csv
├── LICENSE
├── .gitattributes
├── .gitignore
├── model
│   ├── Final\_(ADDED\_LABEL\_ENCODING).ipynb
│   └── Final\_(One\_Hot\_Encoding).ipynb
├── REPORT.pdf
└── README.md

````

- **Data/**  
  Raw CSV dataset (pre‑cleaning).

- **model/Final_(ADDED_LABEL_ENCODING).ipynb**  
  Full pipeline using **Label Encoding**  
  1. Mount & load data  
  2. Missing‑value analysis & outlier handling (IQR + winsorization)  
  3. Data‑type corrections & new feature creation  
  4. Label encoding + mutual information for feature selection  
  5. SMOTE resampling for class imbalance  
  6. Training and comparing 5 classifiers (RF, KNN, SVM, Logistic Regression, Decision Tree)  
  7. Hyperparameter tuning, feature‑importance filtering, stacking ensembles  
  8. Final metrics & recommendation  

- **model/Final_(One_Hot_Encoding).ipynb**  
  Identical pipeline, but uses **One‑Hot Encoding** (drop‑first) instead of label encoding. Facilitates direct comparison of encoding strategies.

- **REPORT.pdf**  
  Narrative report with tables, charts, and a concise recommendation.

## Key Results

| Encoding       | Best Model     | Accuracy | False Negatives | Notes                                  |
|----------------|----------------|---------:|----------------:|----------------------------------------|
| Label Encoding | Random Forest  |   99.75% |               0 | Chosen for zero FN in test set         |
| One‑Hot        | XGBoost        |   99.82% |               1 | Slightly higher accuracy but 1 FN      |

- **Random Forest (Label Encoding)** achieved 99.75% accuracy with **0 false negatives**, critical for intrusion detection.
- **XGBoost (One‑Hot Encoding)** delivered 99.82% accuracy but incurred 1 false negative.
- All other models (KNN, SVM, Logistic Regression, Decision Tree) performed competitively but with higher FN rates.
- **Stacking** ensembles (RF/DT/SVM) did not improve upon a single Random Forest for zero-FN performance.

## Quickstart

```bash
git clone https://github.com/amr-yasser226/machine-learning-for-network-intrusion-detection.git
cd machine-learning-for-network-intrusion-detection

python3 -m venv venv
source venv/bin/activate

jupyter lab
````

Open the two notebooks under `model/` and run end-to-end.

## Dependencies

* Python 3.8+
* pandas, numpy, matplotlib, seaborn
* scikit‑learn, imbalanced‑learn
* xgboost

## What This Solves

* Demonstrates best practices in **EDA**, **feature engineering**, and **model evaluation**
* Compares two encoding strategies for categorical data
* Addresses class imbalance with **SMOTE**
* Benchmarks multiple classifiers and stacking ensembles
* Prioritizes **zero false negatives**—paramount in intrusion detection

## License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.
