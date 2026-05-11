# Individual Sports Analytics — OBA465
A statistical analysis investigating which offensive metric is the better predictor of regular-season NBA win percentage.

## Research Question
Is effective field goal percentage (eFG%) a better predictor of win percentage than three-point shooting volume (FG3A)?

## Project Files

  - main.ipynb — the analysis notebook (14 sequential cells)
  - nba_team_stats.csv — team-level NBA stats (390 team-seasons, 19 columns)
  - analysis_results.csv — generated summary table (created by Cell 14)
  - figures/ — generated PNG figures used as the report appendix (created by Cell 14)

Required Imports
- The notebook uses the following Python libraries:
- import pandas as pd
- import numpy as np
- import matplotlib.pyplot as plt
- import seaborn as sns
- from scipy import stats
- from sklearn.linear_model import LinearRegression
- from sklearn.preprocessing import StandardScaler
- import statsmodels.api as sm

Install everything with:
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels jupyter
## How to Run

1. Make sure nba_team_stats.csv is in the same folder as main.ipynb.
2. Open the notebook: jupyter notebook main.ipynb
3. Run cells top-to-bottom (Cell -> Run All).
4. The final cell writes analysis_results.csv and populates the figures/ folder.

## Notebook Breakdown
What Each Cell Does
1.        Imports and display/seaborn setup
2.        Load nba_team_stats.csv, print shape, seasons, head
3.        Missing-value check + describe on key variables
4.        Full descriptive analysis of W_PCT (mean/median/IQR/skew/CI/Q-Q/Shapiro-Wilk)
5.        Same descriptive analysis for EFG_PCT
6.        Same descriptive analysis for FG3A
7.        Correlation matrix heatmap; Pearson r and p for EFG vs W_PCT and FG3A vs W_PCT
8.        Side-by-side scatter plots with regression lines and R² in titles
9.        Two simple OLS regressions (statsmodels) with full summaries
10.       Multiple regression with standardized predictors so coefficients are directly comparable
11.      Histogram + fitted normal curve for both predictors
12.       Winners vs losers (W_PCT > 0.5) — independent t-tests with Cohen's d
13.       Final summary table comparing both predictors across all measures + conclusion
14.       Export analysis_results.csv and all figures to figures/

## Key Variables
Meaning of each Column
- W_PCT ->          Win percentage (target variable)
- EFG_PCT ->       Effective field goal % — predictor 1
- FG3A  ->         Three-point attempts — predictor 2
- PACE  ->         Possessions per 48 minutes
- OFF_RATING  ->   Points scored per 100 possessions
- TS_PCT  ->       True shooting percentage

## Methodology
The two predictors are compared on four independent measures:

1. Pearson correlation with W_PCT
2. R² from simple linear regression
3. Standardized coefficient in a multiple regression with both predictors
4. Cohen's d effect size from a t-test of winning vs losing teams

The variable that wins the majority of these comparisons is reported as the better predictor.
