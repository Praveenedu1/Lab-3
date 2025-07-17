# Lab 3: Clustering Analysis Using K-Means and K-Medoids Algorithms

**Name:** Praveen Kumar Rayapati  
**Course:** Advanced Big Data and Data Mining  
**Assignment:** Lab 3 - Clustering Analysis

## Purpose of Lab Work

This lab explores unsupervised learning techniques by implementing and comparing two popular clustering algorithms: K-Means and K-Medoids. The primary objectives include:

- **Algorithm Implementation**: Apply both K-Means and K-Medoids clustering algorithms to the Wine dataset from sklearn
- **Performance Evaluation**: Compare clustering quality using Silhouette Score and Adjusted Rand Index (ARI)
- **Data Preprocessing**: Demonstrate proper data standardization techniques for clustering
- **Visualization**: Create meaningful visualizations to interpret clustering results
- **Comparative Analysis**: Understand the strengths and weaknesses of each clustering approach

## Dataset Overview

The Wine dataset contains 178 samples with 13 features representing different chemical properties of wines from three different cultivars (classes). The dataset characteristics:

- **Samples**: 178 wine samples
- **Features**: 13 chemical properties (alcohol, malic_acid, ash, etc.)
- **Classes**: 3 wine cultivars (59, 71, and 48 samples respectively)
- **Data Quality**: No missing values, well-balanced classes

## Key Insights from Clustering Results

### Performance Comparison

| Algorithm | Silhouette Score | Adjusted Rand Index (ARI) | Cluster Distribution |
|-----------|------------------|---------------------------|---------------------|
| K-Means   | 0.2849          | 0.8975                    | [65, 51, 62]       |
| K-Medoids | 0.1548          | 0.3413                    | [89, 24, 65]       |

### Major Observations

1. **K-Means Superior Performance**: K-Means significantly outperformed K-Medoids in both evaluation metrics:
   - **Silhouette Score**: K-Means (0.2849) vs K-Medoids (0.1548) - 84% higher
   - **ARI Score**: K-Means (0.8975) vs K-Medoids (0.3413) - 163% higher

2. **Cluster Distribution Patterns**:
   - **K-Means**: More balanced cluster sizes (65, 51, 62 samples)
   - **K-Medoids**: Unbalanced distribution with one dominant cluster (89, 24, 65 samples)

3. **Algorithm-Specific Insights**:
   - **K-Means**: Created well-separated, spherical clusters that closely matched the true wine classes
   - **K-Medoids**: Struggled with cluster separation, likely due to the high-dimensional nature of the data

4. **Data Characteristics Impact**:
   - The Wine dataset appears to have naturally spherical clusters, favoring K-Means
   - High dimensionality (13 features) may have disadvantaged K-Medoids' distance-based optimization

## Challenges Faced and Solutions

### 1. Library Dependencies
**Challenge**: Initial code used `sklearn_extra.cluster.KMedoids` which wasn't available in the environment.

**Solution**: Implemented a custom K-Medoids algorithm from scratch with the following features:
- Random initialization of medoids
- Iterative optimization based on total intra-cluster distance
- Convergence checking
- Compatible interface with sklearn standards

### 2. High-Dimensional Visualization
**Challenge**: Visualizing 13-dimensional clustering results in 2D space.

**Solution**: Applied Principal Component Analysis (PCA) to reduce dimensionality to 2D while preserving variance structure for meaningful visualization.

### 3. Performance Metric Interpretation
**Challenge**: Understanding why K-Medoids performed significantly worse than expected.

**Decision**: Conducted detailed analysis considering:
- Dataset characteristics (continuous features, spherical clusters)
- Algorithm assumptions (K-Means assumes spherical clusters)
- Distance metric effects in high-dimensional spaces

### 4. Data Preprocessing
**Challenge**: Ensuring fair comparison between algorithms with different scales of features.

**Solution**: Applied z-score standardization to normalize all features to mean=0 and std=1, ensuring no single feature dominated the clustering process.

## Technical Decisions Made

1. **Random Seed Setting**: Used `random_state=42` for reproducible results across multiple runs
2. **Cluster Number**: Set k=3 to match the true number of wine classes for meaningful comparison
3. **Distance Metric**: Used Euclidean distance for both algorithms to ensure fair comparison
4. **Evaluation Metrics**: 
   - Silhouette Score for internal cluster quality assessment
   - ARI for external validation against true labels

## Conclusions and Recommendations

### For the Wine Dataset:
K-Means is the clear winner due to the dataset's characteristics:
- Continuous chemical measurements
- Naturally spherical cluster structure
- High correlation with true wine classes (ARI = 0.8975)


---
