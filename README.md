# Estimation of Obesity Levels Based on Eating Habits and Physical Condition

## Overview
This project presents an end-to-end statistical analysis and machine learning workflow
to estimate obesity levels based on individuals’ eating habits, physical condition,
and lifestyle factors. The analysis uses a publicly available dataset from the
UCI Machine Learning Repository and focuses on exploratory data analysis (EDA),
feature understanding, and predictive modeling.

The project was completed as part of a course final project and emphasizes
reproducibility, statistical validity, and clear communication of results.

## Dataset
**Estimation of Obesity Levels Based On Eating Habits and Physical Condition**  
UCI Machine Learning Repository (2019)  
DOI: https://doi.org/10.24432/C5H31Z  

The dataset includes demographic, dietary, and physical activity variables
(e.g., age, gender, eating frequency, physical activity level) along with a
categorical target variable representing obesity level.

### Target Variable
- Obesity Level (e.g., Insufficient Weight, Normal Weight, Overweight, Obesity Types)

## Objectives
- Clean and preprocess health-related survey data
- Perform exploratory data analysis (EDA) to understand patterns and relationships
- Build and evaluate classification models to predict obesity level
- Assess model assumptions, performance, and limitations

## Project Structure
- `data/raw/` – Original dataset (not modified)
- `data/processed/` – Cleaned and transformed data
- `notebooks/` – Jupyter notebooks for EDA and modeling
- `src/` – Python scripts for preprocessing, training, and evaluation
- `report.pdf` – Final technical report
  
## Tools & Libraries
* **Platform:** [Google Colab](https://colab.research.google.com/) (Jupyter Notebook environment)
* **Language:** Python 3.10+
**1. Data Manipulation & Core Math**
* `pandas`: DataFrame structure and data cleaning.
* `numpy`: Numerical computing and array handling.
* `math`: Standard mathematical functions.
* `ucimlrepo` / `fetch_ucirepo`: API for fetching the dataset directly from UCI.

**2. Visualization**
* `matplotlib.pyplot`: Base plotting and graph generation.
* `seaborn`: Statistical data visualization (heatmaps, distributions).

**3. Frequentist Statistics & Regression**
* `statsmodels.api`: Standard statistical modeling.
* `statsmodels.miscmodels.ordinal_model`: Used for Ordinal Regression (analyzing the ordered nature of Obesity Levels).
* `statsmodels.stats.outliers_influence`: specifically `variance_inflation_factor` (VIF) to check for multicollinearity.
* `scipy.stats`: Scientific computing and statistical tests.
* `scikit_posthocs`: Post-hoc analysis for statistical significance.

**4. Bayesian Modeling & Probabilistic Programming**
* `pgmpy`: Core library for Bayesian Network structure learning and inference.
* `pymc`: Probabilistic programming for advanced parameter learning.
* `arviz`: Exploratory analysis of Bayesian models.
* `bambi`: High-level Bayesian Model-Building Interface (built on top of PyMC).

## Methods
1.  **Structure Learning:**
    * Used **Hill Climb Search** with the **Bayesian Information Criterion (BIC)** score via `pgmpy` to discover the directed acyclic graph (DAG).
    * **Constraints:** Applied expert knowledge (e.g., *Family History* as a root node) to prevent reverse causality.
2.  **Parameter Learning:**
    * Utilized **Bayesian Estimators** to calculate Conditional Probability Tables (CPTs).
    * Leveraged **PyMC** and **Bambi** to treat probabilities as distributions, allowing for robust estimates of complex lifestyle profiles.
3.  **Inference:**
    * Performed **Variable Elimination** to calculate posterior probabilities and Lift metrics for specific risk profiles.

## Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Results
Our analysis identified three primary drivers of obesity severity:

1.  **The Dominant Driver (Family History):**
    * Family history is the strongest structural predictor. Individuals with a family history have a baseline probability of obesity >70% when combined with sedentary habits.
2.  **The "Tipping Point" (Snacking):**
    * High-calorie food frequency acts as a critical switch. Moving from "Low" to "High" frequency shifts the probability mass significantly from *Normal* to *Overweight*.
3.  **The Protective Buffer (Physical Activity):**
    * "Medium" physical activity (0.5–2.0 sessions/week) offers the highest statistical protection against weight gain for the general population.
4. **Genetics x Lifestyle Interaction:** Obesity severity reflects genetics interacting with lifestyle behaviors.
5.  **Interpretative Note:** These findings are associative. The use of SMOTE (synthetic data) limits population-level generalization.

## Team Members
- Christian Lopez
- Lash Narayan

## Notes
- GitHub is used for version control and collaboration
- Code follows PEP 8 style guidelines where applicable
- This project is for educational and analytical purposes only and does not
  constitute medical advice
