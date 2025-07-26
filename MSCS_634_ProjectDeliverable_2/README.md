Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Project Deliverable 2: Regression Modeling and Performance Evaluation

## The dataset
The dataset contains medical and dental appointment data for 413 patients. Each record includes:
- Demographics: age, gender, date of birth.
- Vital signs: weight, height, temperature, pulse, blood glucose, etc.
- Appointment info: whether a patient had a general or dental visit.
- Prescriptions and notes: if medications were prescribed and doctor notes.
- Derived features: like BMI, note length, count of treated teeth, and flags for abnormal vitals.

We engineered 12 features to better predict the blood glucose level (patient_blood_glucose), which was our target variable.

## Model Evaluation Summary
We tested three models: Linear Regression, Lasso, and Ridge. Here's what we found:

R² Scores (Higher is Better):
Model	            R²
Linear Regression	0.1155
Lasso Regression	0.1161
Ridge Regression	0.1167

MSE Scores (Lower is Better):
Model	            MSE
Linear Regression	2794.37
Lasso Regression	2792.49
Ridge Regression	2790.67

Cross-Validation (5-Fold Mean MSE):
Model	            Mean MSE	Std Dev
Linear Regression	2539.67	    1463.93
Lasso Regression	2534.04     1446.85
Ridge Regression	2540.32	    1450.25

## Insights and Observations
1) Overall Model Performance was Modest.

All three models explained only about 11.6% of the variance in blood glucose (R² ≈ 0.11). This suggests that the available features don't strongly predict blood glucose — maybe other unmeasured factors like diet, diabetes history, or medications outside this data influence it more.

2) Ridge Regression Performed Best

Ridge had the highest R² and lowest MSE, both in basic training and on unseen test data.

It did not shrink any coefficients to zero but smoothed them, indicating regularization helped reduce overfitting slightly.

3) Lasso for Feature Selection

Lasso shrunk the coefficient for has_general_appointment to 0, implying it wasn’t useful in predicting glucose.

It also reduced the impact of other weak features, useful if we want a simpler model with fewer predictors.

4) Important Features (based on coefficients):

abnormal_oxygen_saturation and abnormal_pulse had the strongest positive impact on blood glucose.

abnormal_temperature and treated_teeth_count had notable negative effects.

This suggests a relationship between vital sign abnormalities and glucose levels, possibly signaling stress or metabolic issues.

5) Model Stability

All models had high variance in MSE across folds (std ≈ 1450), showing sensitivity to training data.

This again highlights the need for either more predictive features or a different modeling approach (like nonlinear models).

## Final Thoughts
- Feature engineering plays a big role in model success.
- Regularization (Lasso, Ridge) improves model generalization.
- Evaluation with cross-validation is more trustworthy than a single test/train split.
- Even with good preprocessing, some targets (like glucose) might need richer data to model accurately.