<svg fill="none" viewBox="0 0 600 300" width="600" height="300" xmlns="http://www.w3.org/2000/svg">
  <foreignObject width="100%" height="100%">
    <div xmlns="http://www.w3.org/1999/xhtml">
      <style>
        @keyframes hi  {
            0% { transform: rotate( 0.0deg) }
           10% { transform: rotate(14.0deg) }
           20% { transform: rotate(-8.0deg) }
           30% { transform: rotate(14.0deg) }
           40% { transform: rotate(-4.0deg) }
           50% { transform: rotate(10.0deg) }
           60% { transform: rotate( 0.0deg) }
          100% { transform: rotate( 0.0deg) }
        }

        @keyframes gradient {
          0% {
            background-position: 0% 50%;
          }
          50% {
            background-position: 100% 50%;
          }
          100% {
            background-position: 0% 50%;
          }
        }

        .container {
          background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
          background-size: 400% 400%;
          animation: gradient 15s ease infinite;

          width: 100%;
          height: 300px;

          display: flex;
          justify-content: center;
          align-items: center;
          color: white;

          font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
        }

        .hi {
          animation: hi 1.5s linear -0.5s infinite;
          display: inline-block;
          transform-origin: 70% 70%;
        }

        @media (prefers-reduced-motion) {
          .container {
            animation: none;
          }

          .hi {
            animation: none;
          }
        }
      </style>

      <div class="container">
        <h1>Hi there, my name is Nikola <div class="hi">👋</div></h1>
      </div>
    </div>
  </foreignObject>
</svg>


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

- **F1 Score**: `0.83`
- **Precision**: `0.85`
- **Recall**: `0.81`

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
