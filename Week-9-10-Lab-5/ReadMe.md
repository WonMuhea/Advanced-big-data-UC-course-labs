# Clustering Lab Report – Wine Dataset

## Purpose

The purpose of this lab was to apply unsupervised learning techniques—specifically **DBSCAN** and **hierarchical clustering**—to the UCI Wine dataset in order to explore natural groupings of wines based on their chemical composition. We aimed to:

- Evaluate clustering quality using internal and external metrics.
- Compare density-based and hierarchical approaches.
- Visualize clusters in PCA-reduced 2D space.
- Interpret how well clusters align with known wine classes.

---

## Key Insights

- **DBSCAN** was able to discover **5 density-based clusters** at ε = 0.5, `min_samples` = 5, with **moderate alignment** to the known wine classes (homogeneity ≈ 0.63).
- **Noise points (31)** were identified, suggesting DBSCAN’s utility in outlier detection.
- **Hierarchical clustering (Ward linkage)** revealed a **clear 3-cluster structure**, matching the actual number of varietals in the dataset.
- Cutting the dendrogram at a **distance ≈ 28** yielded clusters that strongly aligned with ground truth (homogeneity ≈ 0.78, completeness ≈ 0.76).
- PCA plots confirmed cluster separation visually, especially under Ward linkage.

---

## Challenges & Decisions

- **Parameter tuning in DBSCAN**: Choosing appropriate ε and min_samples was critical—too low led to over-segmentation, too high to collapsing all points into one cluster.
- **DBSCAN over-clustering**: Though the dataset has 3 true classes, DBSCAN detected more than 3 clusters due to local density variations.
- **Choosing evaluation metrics**: Since ground truth labels were available, we used **homogeneity** and **completeness** to measure how well clusters matched true labels in addition to **silhouette score**.
- **Visual interpretation**: PCA was used to reduce dimensionality to 2D for clear visual analysis, though some variance was naturally lost in projection.

---

## ✅ Conclusion

DBSCAN is useful for **outlier detection and discovering fine-grained subclusters**, but requires careful tuning. **Hierarchical clustering** (Ward linkage) is **more consistent and interpretable** when the number of natural groups is known. The wine dataset's structure lends itself well to Ward clustering, which cleanly recovers the three varietals.
