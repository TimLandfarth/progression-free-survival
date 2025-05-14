# Statistical Analysis for Prediction of Progression-Free Survival under Immune Checkpoint Inhibition

This repository contains the R code used for the development and validation of Cox proportional hazards models to predict progression-free survival (PFS) in patients treated with immune checkpoint inhibitors (ICI). The analysis included multiple imputation for missing data, model building via forward selection based on AIC and BIC criteria, and performance evaluation using repeated cross-validation, the concordance index, and the Brier score. The results are part of a retrospective study currently under preparation for publication.
Note that the real data cannot be included in this repository. However, we have provided pseudo data with similar properties to the original data. Consequently, the results obtained using the pseudo data will differ from those of the original analysis.

The structure of the repository is as follows:

- **R Code**
  - **diagnostic.R**: Required data: *imputed_dataset.Rda*, *models.Rda*. Calculation of the Schoenfeld residuals and testing the proportional hazard assumption.
  - **functions.R**: Required data: none. Functions for imputing data and index formation for cross-validation.
  - **generation_of_pseudo_data.R**: Required data: original data (not included here). Generation of a pseudo data set from the original data
  - **graphic_parameters.R**: Required data: none. Colors, heights and widths for generating graphics.
  - **libraries.R**: Required data: none. Loading of all packages used.
  - **model.R**: Required data: *pseudo_data.RData*. Construction of the model with stepfunction according to AIC and BIC.
  - **preparation.R**: Required data: none. Preparation of the original data (not included here).
  - **validation.R**: Required data: *pseudo_data.RData*. Validation of the model and the cut-off values.

- **Data**:
  - **imputed_dataset.Rda**: (*df_imp*) 20-fold stacked, imputed data set from the pseudo data
  - **models.Rda**: Original Coxph models, selected using AIC (*cox_aic*) and BIC (*cox_bic*)
  - **prep.RData**: prepared dataset from pseudo data (*df*)
  - **pseudo_data.RData**: generated pseudo data set from the original data (*df*)
  - **session_info.Rda**: Version information of R and packages
  - **validation.Rda**: Brier and Cindex with respect to the AIC and BIC model from each iteration of the repeated cross-valdiation (res) and boxplot of these values (performance_plot).

- **Plots**
  - **Performance_validated_cox.pdf**: Brier and Cindex for five-fold cross-validation (Graphic is saved in *Data/validation.Rda* and calculated in *R Code/validation.R*)
  - **schoenfeldres_AICmodel.pdf**: Schoenfeld residuals for the original AIC model (Graphic is calculated in *R Code/diagnostic.R*)
  - **schoenfeldres_BICmodel.pdf**: Schoenfeld residuals for the original BIC model (Graphic is calculated in *R Code/diagnostic.R*)
  