# Breast Tissue Classification

Comparing Logistic Regression and Random Forest on the [UCI Breast Tissue Impedance dataset](https://archive.ics.uci.edu/dataset/192/breast+tissue)
A small, real-world multiclass classification problem: 106 samples, 6 tissue types, 9 impedance-based features.

## Dataset

Electrical impedance measurements of freshly excised breast tissue samples, sourced from the UCI Machine Learning Repository. Each sample is one of six tissue classes: carcinoma (`car`), fibro-adenoma (`fad`), mastopathy (`mas`), glandular (`gla`), connective (`con`), or adipose (`adi`).

## Approach

- Exploratory data analysis: class balance, feature distributions, correlation between features
- Train/test split (80/20, stratified) and feature scaling
- Two models trained and compared: Logistic Regression and Random Forest
- Evaluation via confusion matrices, precision/recall/F1 per class, and 5-fold cross-validation

## Results

Random Forest slightly outperformed Logistic Regression (73% vs 68% test accuracy; confirmed by 5-fold cross-validation at 68% against 65% average accuracy).

Both models however, completely failed to correctly identify the `mas` (mastopathy) tissue class (0% recall for both), suggesting this class is genuinely hard to differentiate from the others using these 9 impedance features alone, rather than being a weakness specific to one algorithm.

Two feature pairs (`I0`/`P` and `DA`/`DR`) were found to be highly correlated (>0.95), indicating some redundancy in the measurements.

Given the small dataset size (106 rows), these results should be interpreted with some caution, cross validation scores varied notably across folds (e.g. Random Forest ranged from 0.59 to 0.76). Read these results with that uncertainty in mind.

## Files

- `ML_Classification_Breast_Tissue_Impedance_Measurements.ipynb` - full notebook: EDA, modeling, evaluation
- `data.csv` - the dataset
