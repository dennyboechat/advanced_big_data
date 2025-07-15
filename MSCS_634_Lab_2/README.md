Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Lab 2: Classification Using KNN and RNN Algorithms

## Lab purpose
This lab focuses on comparing the performance of K-Nearest Neighbors (KNN) and Radius Neighbors (RNN) classifiers using the Wine Dataset from sklearn. It evaluates how different parameter settings affect model accuracy and use visualizations to interpret the results. The goal is to understand how parameter choices impact classification and learn how to choose optimal values.

## Key insights
### KNN
Accuracy often peaks around moderate k values
- k = 1 usually gives high accuracy on training data but may overfit and perform worse on test data due to high variance.
- As k increases (eg. 5 to 11), the model becomes more stable, often leading to better generalization and test accuracy.
- Beyond a point (eg. k = 21), accuracy may drop again due to underfitting. The model is now "too simple" and averages over too many neighbors.

Best k varies by dataset
- On the Wine dataset (well-behaved, small, low-dimensional), good values for k often fall between 5 and 11.
- No single k is always best. It’s dataset-dependent, which is why trying multiple values is essential.

We found that accuracy tends to improve as we move from k=1 to k=5 or 11, indicating reduced overfitting. However, performance may decline slightly with higher k values like 21, likely due to underfitting. The optimal value of k for this dataset appears to be in the range of 5 to 11, balancing bias and variance effectively.

### RNN
All Radii likely result in 100% coverage and identical accuracy
- Because we scaled the features (using StandardScaler), all data points now lie roughly within a range of -3 to +3 per feature. A radius as large as 350–600 (in this normalized space) is massively oversized.

Radius too large → Becomes like KNN with many neighbors
- With such large radii, you're including almost the entire training set as neighbors for every test point.
- This turns RNC into a kind of global majority voting classifier. Essentially a softened version of 1-nearest-centroid.

The radius values used (350–600) were far too large after feature scaling, resulting in 100% coverage and nearly identical accuracy across all runs. While this shows model stability, it also suggests underfitting and lost sensitivity to local structure.

## Models comparisson
- KNN provided high accuracy (typically between 94%–98%), with best results at moderate k values like 5 or 11.
- RNN with radius values 350–600 resulted in identical accuracy and full coverage, but offered no insight into neighborhood behavior due to overly large radii.
- KNN showed more consistent and predictable accuracy trends, while RNN performance was flat, highlighting a lack of sensitivity in the chosen radius range.

Based on results, KNN is clearly preferable for the standardized Wine dataset due to its strong accuracy, clear tuning behavior, and guaranteed predictions. RNN can be valuable in niche scenarios involving variable density or anomaly detection, but needs carefully chosen radius values to perform well.