# Clinical Predictors of PSA: Statistical Modelling in R

A student data analytics project exploring how clinical measurements are associated with log prostate-specific antigen (`lpsa`) and whether a simpler regression model can achieve comparable out-of-sample performance.

## Project question

**Which variables are most informative for log PSA, and how does model complexity affect performance on unseen data?**

## Analysis

The project uses a predefined training/test split and includes:

- exploratory data analysis
- correlation analysis and variance inflation factors (VIF)
- multiple linear regression
- regression diagnostics and influential-observation checks
- comparison of full and reduced models using a nested F-test, AIC and BIC
- holdout test-set evaluation
- 10-fold cross-validation on the training data
- an exploratory sensitivity analysis of numeric versus dummy-coded Gleason score

## Main findings

- `lcavol` shows the clearest and most consistent association with log PSA in this dataset.
- Some predictors contain overlapping information, but the observed VIF values do not indicate severe multicollinearity.
- The additional predictors in the full model are not clearly justified by the nested F-test and information criteria.
- The reduced model performs better on the predefined holdout test set, while 10-fold cross-validation gives very similar average MSE for the full and reduced models.
- Dummy coding the Gleason score does not show a clear advantage in the exploratory sensitivity analysis, and the higher Gleason categories are very sparse.

## Tools

- R
- Quarto
- tidyverse
- broom
- car
- rsample

## Repository files

- `prostate_analysis.qmd` — complete Quarto analysis and interpretation
- `prostate.csv` — dataset used in the analysis
- `README.md` — project overview
- `.gitignore` — standard R/Quarto exclusions

## Reproduce the analysis

Open `prostate_analysis.qmd` in RStudio or another Quarto-compatible environment and render the document.

Required R packages:

```r
install.packages(c("tidyverse", "broom", "car", "rsample"))
```

The analysis expects `prostate.csv` to be in the same folder as the `.qmd` file.

## Limitations

The dataset is small and observational, with 97 observations in total and 67 used for model fitting. Several predictors are correlated, some Gleason categories are extremely sparse, and the supplied exercise context describes a historical single-hospital cohort. Results should therefore be interpreted as statistical associations within this sample rather than causal or current clinical conclusions.
