Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Deliverable 3: Classification, Clustering, and Pattern Mining

## The dataset
The dataset contains medical and dental appointment data for 413 patients. Each record includes:
- Demographics: age, gender, date of birth.
- Vital signs: weight, height, temperature, pulse, blood glucose, etc.
- Appointment info: whether a patient had a general or dental visit.
- Prescriptions and notes: if medications were prescribed and doctor notes.
- Derived features: like BMI, note length, count of treated teeth, and flags for abnormal vitals.

We engineered 12 features to better predict the blood glucose level (patient_blood_glucose), which was our target variable.

## Insights and observations
From the classification models, we learned that patient appointment outcomes can be predicted fairly well using features like demographics, medical history, and appointment details. Hyperparameter tuning improved accuracy, and evaluation with confusion matrices, ROC curves, and F1 scores showed that our models could reliably flag which patients are more likely to cancel or miss appointments. This insight can help the clinic focus reminders or rescheduling efforts on higher-risk cases.

The clustering analysis revealed three main patient groups with distinct profiles—one with generally higher blood glucose levels, another with lower height and weight but higher pulse, and one with healthier average measures. While the silhouette scores suggest moderate separation, these clusters can still guide targeted care strategies, such as personalized follow-up plans or specialized health advice for each group.

From the association rule mining (Apriori and FP-Growth), we found patterns linking certain treatments, patient conditions, and follow-up behaviors. These patterns could help the clinic in real life by improving scheduling efficiency (pre-booking follow-ups for procedures that often require them), better inventory planning (ensuring needed materials are ready), and more personalized marketing (targeted offers based on treatment patterns).

In practice, combining these three approaches means the clinic can predict patient behavior, group patients into actionable categories, and discover hidden relationships in treatment patterns. This can lead to better patient care, reduced no-shows, optimized resources, and improved operational planning.