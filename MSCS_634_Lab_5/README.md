Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Lab 5: Clustering Techniques Using DBSCAN and Hierarchical Clustering

## Lab Purpose

This lab explores clustering techniques using Hierarchical and DBSCAN algorithms on the Wine dataset from scikit-learn. The objective is to deepen the understanding of clustering through practical application, evaluation metrics, and visual analysis.

## Key insights and models comparison

When comparing Hierarchical Clustering and DBSCAN, the differences in performance become quite clear. For the Wine dataset, Hierarchical Clustering worked well because it produced clearly defined clusters that matched the true labels. It was easy to choose the number of clusters (since we know there are three wine types), and the algorithm performed fairly consistently. The evaluation metrics, like Silhouette Score and Homogeneity/Completeness, indicated that the clusters formed were well-separated and aligned with the true wine classes.

On the other hand, DBSCAN gave us some challenges at first. Initially, using eps=1.2 and min_samples=5, all points were labeled as noise (-1), meaning that DBSCAN couldn’t find any meaningful clusters. Even after adjusting the eps parameter, the clustering results were not as stable or clear as with hierarchical clustering. The key issue with DBSCAN is that it requires careful tuning of parameters, particularly eps and min_samples. Without setting these parameters correctly, DBSCAN can either fail to find any clusters or overfit the data, leading to incorrect groupings.

The choice of parameters plays a huge role in both algorithms, but especially in DBSCAN. In Hierarchical Clustering, the number of clusters (n_clusters) is typically predefined, making it easier to control. However, the number of clusters needs to be set correctly in advance, and this can sometimes be tricky if the true number of clusters isn’t known. In contrast, DBSCAN doesn’t require the number of clusters to be set, but it’s highly sensitive to the values of eps (the distance that defines a neighborhood) and min_samples (the minimum number of points needed to form a dense region). If these are set incorrectly, DBSCAN may label all points as noise or fail to identify proper clusters.

When it comes to strengths and weaknesses, each algorithm has its advantages. Hierarchical clustering is great when the clusters are well-separated and easy to define, as it doesn’t require assumptions about the data’s density or shape. It also gives us a visual representation of the clustering process through a dendrogram, which can help us understand how the clusters are formed. However, it does require choosing the number of clusters ahead of time, and it can be computationally expensive, especially for large datasets.

DBSCAN, on the other hand, shines when dealing with datasets that contain noise or when the clusters are of arbitrary shape. It doesn’t require us to specify the number of clusters beforehand, and it is particularly useful when we have outliers that we want to identify. However, its main weakness is the sensitivity to the eps and min_samples parameters, which can make tuning difficult. DBSCAN can also struggle when clusters vary in density, leading to poor results if the data isn't relatively uniform in terms of density.

In conclusion, for the Wine dataset, Hierarchical Clustering performed better because the data had well-separated, spherical clusters that were easy to define. DBSCAN, while powerful for other types of data (especially noisy or non-globular clusters), struggled here without careful tuning of parameters. For datasets with a known number of clusters and well-defined groupings, Hierarchical Clustering is often the better choice. However, if you're working with data that has outliers or complex cluster shapes, DBSCAN can be a very useful algorithm.