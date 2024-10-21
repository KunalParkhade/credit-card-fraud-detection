# Credit Card Fraud Detection using Spectral Clustering

## Overview

This project addresses the challenge of detecting fraudulent credit card transactions by utilizing advanced clustering techniques, specifically **Laplacian Eigen Decomposition** and **K-Means Clustering**. The goal is to identify anomalous transactions (outliers) that may indicate fraud based on their behavior compared to non-fraudulent ones.

## Dataset

The dataset contains a variety of transaction-related features, including flags for declined transactions, foreign transactions, and transactions from high-risk countries. The main objective is to classify each transaction as either **fraudulent** or **non-fraudulent**.

### Key Features:
- **Is declined**: Indicates if the transaction was declined (`Y` or `N`).
- **isForeignTransaction**: Indicates if the transaction was foreign (`Y` or `N`).
- **isHighRiskCountry**: Indicates if the transaction originated from a high-risk country (`Y` or `N`).
- **isFradulent**: Binary target variable indicating whether the transaction was fraudulent (`Y` or `N`).

### Preprocessing
- Categorical features were converted into binary format (`1` for `Y`, `0` for `N`).
- Irrelevant columns like `Merchant_id` and `Transaction date` were removed.
- Feature scaling was applied using **MinMaxScaler** to normalize the data for clustering.

## Methodology

### 1. **Laplacian Eigen Decomposition**

This method helps in dimensionality reduction while preserving the relationships between the data points in the feature space. The steps include:
- Constructing a **similarity matrix** using an RBF kernel.
- Calculating the **degree matrix** and the **graph Laplacian**.
- Performing **eigenvalue decomposition** to obtain the eigenvectors, which represent the data points in a lower-dimensional space.

### 2. **K-Means Clustering**

After obtaining the top `K` eigenvectors, the data is clustered into distinct groups. Each cluster is then analyzed to detect anomalies using z-scores:
- Each point's **z-score** indicates how far it is from the cluster mean.
- Transactions with high z-scores (above a threshold) are classified as potential fraudulent transactions.

### 3. **Fraud Detection Using Z-Scores**

- Fraud detection is refined by using z-scores to highlight outliers in each cluster.
- These outliers are considered suspicious and flagged as potentially fraudulent.

## Model Performance

Performance is evaluated using standard classification metrics:
- **Precision**: Measures how many detected frauds were actually frauds.
- **Recall**: Measures how many actual frauds were detected.
- **F1 Score**: Harmonic mean of precision and recall, giving a balanced view of model performance.

### Confusion Matrix

A confusion matrix is used to visually analyze the true positives, true negatives, false positives, and false negatives for fraud detection.

## Results

- **F1 Score**: `0.84`  
- **Precision**: `0.85`
- **Recall**: `0.83`

The results are visualized using various plots, including:
- **Eigenvalue distribution**: Helps determine the optimal number of clusters.
- **Cluster visualization**: Shows the separation between detected clusters.
- **Confusion Matrix**: Offers insights into the classification performance.

## Visualizations

- **Feature Distributions**: Histograms show the distribution of key features in the dataset.
- **Clustering Results**: Scatter plot of clusters in the lower-dimensional space.
- **Confusion Matrix**: Provides a clear breakdown of predicted vs actual labels.

## Installation

To run this project locally:

1. Clone the repository:
    ```bash
    git clone https://github.com/KunalParkhade/credit-card-fraud-detection.git
    ```

2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## Future Work

Potential enhancements to improve model performance include:
- Incorporating additional features such as transaction history or user behavior patterns.
- Experimenting with other clustering techniques such as **DBSCAN** or **Spectral Clustering**.
- Fine-tuning the z-score threshold for more precise fraud detection.

## Conclusion

This project demonstrates the effectiveness of **Laplacian Eigen Decomposition** and **K-Means Clustering** for fraud detection. By identifying clusters and outliers, we can flag suspicious transactions for further investigation, providing a robust method for identifying fraud in credit card transactions.

---
