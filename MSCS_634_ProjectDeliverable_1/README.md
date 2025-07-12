Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Project Deliverable 1: Data Collection, Cleaning, and Exploration

## The Dataset
The selected dataset comes from a personal project I developed to support healthcare organizations in collecting patient data from underserved regions. It includes records of health appointments, both general and dental, for individuals in Fiji and Madagascar.

This dataset is well-suited for the project, as it focuses on healthcare-related information, contains over 500 entries, and features a total of 17 attributes.

## Inspecting the dataset

The dataset was loaded in Jupyter Notebook (Pandas) and inspected using info() and describe() as per image 01_dataset_inspection.

## Data cleaning

- General and dental appointments were merged into a single row per patient to eliminate duplication.
- Medications and treated teeth had duplicate values, which were removed.
- Data from the project named "Test" was excluded.
- The phone number column was removed.
- Rows without both general and dental appointments were removed.
- Duplicate rows were deleted.
- Height and weight values were carried over from previous appointments when newer ones were missing.
- Older appointment data was deleted, keeping only the most recent patient records.
- Missing temperature values were filled with the mean.

As a result, the number of rows was reduced from 661 to 413.

## Exploratory data analysis

### Data Distribution (Histograms)
Check image 02_Data_Distribution.
Most numeric features like patient temperature and weight show unimodal distributions, with the majority of values clustered around a central range.
For example, patient_temperature is tightly distributed around 36–37°C, which aligns with expected human body temperatures.
Height and weight distributions may vary more depending on the population (adults vs. children), with height showing possible bimodality due to mixed age groups.

### Outlier Detection (Boxplots)
Check image 03_Outlier_Detection.
Outliers were observed in features like patient_weight and blood_glucose, suggesting either data entry errors or medically significant cases.
For instance, some weight values are well above or below typical human ranges, which could be children or patients with health issues.
Temperature had very few or no outliers, indicating consistent recording across patients.

### Feature Relationships (Scatter Plot: height vs. weight)
Check image 04_Feature_Relationships.
The scatter plot of patient_height vs. patient_weight reveals a clear positive relationship — taller individuals generally weigh more.
However, the data also shows distinct clusters, likely separating adults from pediatric patients.
A few points fall far from the general trend, which may indicate outliers due to data errors or patients with atypical proportions.

## Insights from EDA
The data cleaning and exploratory analysis steps taken provide a strong foundation for reliable and meaningful modeling. By merging general and dental appointments into a single row per patient and removing duplicate rows, we ensure that each individual is represented uniquely, avoiding data leakage and inflated sample sizes. Cleaning errors such as duplicated medications and treated teeth improves feature clarity and prevents overemphasis during training. Excluding irrelevant records—such as those from test projects or entries missing critical data like appointments—helps maintain consistency and relevance. Additionally, carrying forward valid height and weight data from older appointments fills critical gaps without introducing synthetic values, while filling missing temperatures with the mean supports model stability. These steps collectively enhance data quality, reduce noise, and ensure that any predictive models built on this dataset are based on consistent, real-world, and clinically meaningful information.

## Challenges
- Initially, the goal was to learn how to work with Jupyter Notebook and install dependencies like Pandas and Matplotlib.
- Cleaning the dataset took a long time. I initially tried using AI, but eventually decided to do it manually myself for better accuracy.
- Interpreting the charts took some time, especially to understand how the data was structured visually. However, since I was already familiar with the dataset, it wasn’t too difficult.