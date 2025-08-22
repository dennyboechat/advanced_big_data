Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Deliverable 4: Data Mining Techniques for a Healthcare Dataset

Presentation link:
https://youtu.be/jwTWTobmInQ

## The dataset
The selected dataset comes from a personal project I developed to support healthcare organizations in collecting patient data from underserved regions. It includes records of health appointments, both general and dental, for individuals in Fiji and Madagascar.

The dataset contains medical and dental appointment data for 413 patients. Each record includes:
- Demographics: age, gender, date of birth.
- Vital signs: weight, height, temperature, pulse, blood glucose, etc.
- Appointment info: whether a patient had a general or dental visit.
- Prescriptions and notes: if medications were prescribed and doctor notes.
- Derived features: like BMI, note length, count of treated teeth, and flags for abnormal vitals.

We engineered 12 features to better predict the blood glucose level (patient_blood_glucose), which was our target variable.

## Data cleaning
In this project, I worked on cleaning the general dentistry appointments dataset to make it more reliable and easier to analyze. First, I converted the date fields into proper datetime format so they could be used for calculations like patient age. Then I standardized the text columns by trimming spaces and converting everything to lowercase for consistency. For missing values, I filled numeric columns with their median values, since that avoids bias compared to filling with zeros. I also removed duplicate rows and made sure gender values were consistent. Finally, I created a new column for patient age, and in a separate step, I removed sensitive information like full names and phone numbers to protect privacy. Overall, the cleaning process helped transform the raw dataset into a structured and safer version for further analysis.

## Exploratory data analysis

### Data Distribution (Histograms)
Most numeric features like patient temperature and weight show unimodal distributions, with the majority of values clustered around a central range.
For example, patient_temperature is tightly distributed around 36–37°C, which aligns with expected human body temperatures.
Height and weight distributions may vary more depending on the population (adults vs. children), with height showing possible bimodality due to mixed age groups.

### Outlier Detection (Boxplots)
Outliers were observed in features like patient_weight and blood_glucose, suggesting either data entry errors or medically significant cases.
For instance, some weight values are well above or below typical human ranges, which could be children or patients with health issues.
Temperature had very few or no outliers, indicating consistent recording across patients.

### Feature Relationships (Scatter Plot: height vs. weight)
The scatter plot of patient_height vs. patient_weight reveals a clear positive relationship — taller individuals generally weigh more.
However, the data also shows distinct clusters, likely separating adults from pediatric patients.
A few points fall far from the general trend, which may indicate outliers due to data errors or patients with atypical proportions.

## Insights from EDA
When exploring the cleaned dataset through EDA, some interesting patterns started to show up. For example, analyzing the patient age distribution revealed that most appointments came from young adults and middle-aged patients, while children and elderly patients made up a smaller portion of visits. By plotting appointment frequency over time, I noticed seasonal variations, suggesting that people may seek dental care more often in certain months, possibly aligning with school breaks or holiday seasons. Looking at the clinical measurements, such as weight, temperature, and blood glucose, gave an idea of the general health profile of the patients, with a few outliers that could represent either recording errors or patients with special health conditions worth further attention.

For feature engineering, it focuses on creating only the most essential variables while keeping the dataset simple. I generated patient age from the date of birth and added BMI to capture overall health indicators. From the appointment date, I extracted month, weekday, and weekend flags, which can help identify scheduling patterns. To capture patient condition, I included basic vitals flags such as fever (temperature ≥ 38°C) and low oxygen saturation (< 95%). Finally, I performed a simple text check on the appointment notes to flag keywords related to pain and checkups, which can highlight common reasons for visits. This smaller set of features provides meaningful insights without making the dataset overly complex, making it a good starting point for exploratory analysis or early predictive models.

## Project Steps
1. Data Preparation & Exploration
- Importing Libraries (pandas, matplotlib)
- Data Distribution Analysis: Histograms plotted for numeric attributes.
- Outlier Detection: Boxplots generated to identify anomalies.
2. Feature Analysis
- Feature Relationships: Scatterplots to visualize correlations (e.g., patient height vs. weight).
3. Data Cleanup
- Standardizing Date Columns (ensuring consistent date formats).
- Sensitive Data Cleanup: Dropping columns that contain personally identifiable information.
4. Feature Engineering
- Creation or improvement of features to enhance model performance.
- Re-import and manipulation of data for engineered features.

## Key Findings

- Data Cleaning: Standardized dates/text, filled missing values with medians, removed duplicates, added age, and removed sensitive info
- EDA:
 - Most vitals normal; outliers in weight and blood glucose.
 - Height–weight correlation with child vs. adult clusters.
 - Seasonal patterns in appointments
- Feature Engineering: Created BMI, age, date flags, fever/oxygen flags, text-based indicators
- Regression Models: Linear, Lasso, Ridge all weak (R² ≈ 0.04–0.05). Age and note length were strongest predictors. More data needed
- Clustering:
 - K-Means/Agglomerative → 3 groups: high-glucose patients, fever-like patients, and “normal” group.
 - DBSCAN failed; clusters not well separated
- Association Rules: Found practical patterns (e.g., root canals → follow-ups, diabetics → deep cleaning, whitening → young adults). Useful for scheduling, resources, marketing