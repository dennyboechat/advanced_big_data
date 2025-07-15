Student: Denny Boechat.

Course: Advanced Big Data and Data Mining (MSCS-634-B01).

Lab 3: Clustering Analysis Using K-Means and K-Medoids Algorithms

## Lab Purpose
In this lab, we applied both K‑Means and K‑Medoids to the Wine dataset from scikit‑learn. First, we preprocessed the data with z‑score scaling and fit each algorithm. Next, we visualized the clusters to see how the samples grouped together. Finally, we calculated the Silhouette Score to judge how tight and well‑separated each cluster was, and the Adjusted Rand Index to compare our clusters against the true wine classes. By looking at the plots alongside these metrics, we learned which method gave the most meaningful groupings.

## Key Insights
### Clusters show only weak separation
- Silhouette Scores were low for both methods (K‑Means ≈ 0.285; K‑Medoids ≈ 0.268), indicating that samples overlap considerably at the edges rather than forming sharply distinct blobs.

### K‑Means aligns much better with true labels
- Adjusted Rand Index for K‑Means was very high (≈ 0.897), showing its clusters almost perfectly recover the three wine varieties.
- K‑Medoids achieved a lower ARI (≈ 0.741), meaning it captures the broad class structure but misses more true‑class distinctions than K‑Means.

## Models Comparison
### Cluster “quality” (Silhouette Score)
- K‑Means (0.285): Weak cluster separation suggests points are only slightly closer to their own centroid than to other centroids.
- K‑Medoids (0.268): Similarly low, trading some compactness for robustness to outliers but yielding little improvement in separation.

### Agreement with true classes (Adjusted Rand Index)
- K‑Means (0.897): Clusters correspond very closely to actual wine types.
- K‑Medoids (0.741): Reasonable agreement, but significantly less accurate than K‑Means.

### Cluster shapes & positioning
- K‑Means: Produces roughly spherical clusters in PCA‐projected space, with centroids at geometric centers of tight groups.
- K‑Medoids: Clusters can appear more irregular because medoids are actual samples; this sometimes pulls a cluster toward outlier points.

### When to use each
- K‑Means is fast and excels when you expect roughly convex/spherical clusters and value precise recovery of class-like groupings.
- K‑Medoids is more robust to noise and gives you real-sample exemplars, making it preferable for smaller datasets or when interpretability of cluster centers is crucial.

### Side-by-side scatter plots
- The plots reveal that, while both algorithms yield similar clusterings, K‑Means produces noticeably more compact groups, with points appearing tighter and more cohesive than in K‑Medoids.