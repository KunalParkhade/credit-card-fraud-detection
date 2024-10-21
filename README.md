<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Credit Card Fraud Detection using Spectral Clustering</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 20px;
        }

        h1, h2 {
            color: #2c3e50;
            text-align: center;
            font-weight: bold;
            animation: fadeIn 2s ease-in;
        }

        h1 {
            font-size: 3em;
        }

        h2 {
            font-size: 2em;
        }

        p {
            line-height: 1.6;
        }

        .container {
            width: 80%;
            margin: 0 auto;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            animation: slideUp 1s ease-out;
        }

        .feature-box {
            margin: 20px 0;
            padding: 15px;
            background-color: #ecf0f1;
            border-left: 5px solid #3498db;
            animation: fadeInUp 1.5s ease;
        }

        .feature-box:hover {
            transform: scale(1.02);
            transition: transform 0.2s ease;
        }

        .button {
            display: inline-block;
            margin: 20px auto;
            padding: 10px 30px;
            background-color: #3498db;
            color: #fff;
            border: none;
            border-radius: 5px;
            text-align: center;
            font-size: 1.2em;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .button:hover {
            background-color: #2980b9;
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideUp {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Credit Card Fraud Detection</h1>
        <h2>Overview</h2>
        <p>This project utilizes clustering techniques such as <strong>Laplacian Eigen Decomposition</strong> and <strong>K-Means Clustering</strong> to identify fraudulent credit card transactions. The objective is to detect anomalies within the data that signify potential fraud.</p>

        <div class="feature-box">
            <h2>Dataset</h2>
            <p>The dataset contains key transaction features, such as:</p>
            <ul>
                <li><strong>Is declined:</strong> Whether the transaction was declined.</li>
                <li><strong>isForeignTransaction:</strong> Whether the transaction was foreign.</li>
                <li><strong>isHighRiskCountry:</strong> Whether the transaction was from a high-risk country.</li>
                <li><strong>isFradulent:</strong> The label indicating if the transaction is fraudulent.</li>
            </ul>
        </div>

        <div class="feature-box">
            <h2>Methodology</h2>
            <p>Our approach involves:</p>
            <ol>
                <li>Preprocessing the dataset (handling categorical variables and scaling features).</li>
                <li>Applying <strong>Laplacian Eigen Decomposition</strong> for dimensionality reduction.</li>
                <li>Clustering the data using <strong>K-Means</strong>.</li>
                <li>Detecting outliers using z-scores, where high z-scores indicate potential fraudulent transactions.</li>
            </ol>
        </div>

        <div class="feature-box">
            <h2>Performance Metrics</h2>
            <p>The model performance is evaluated using:</p>
            <ul>
                <li><strong>Precision: 0.85</strong> How many detected frauds are actual frauds.</li>
                <li><strong>Recall: 0.81</strong> How many actual frauds were detected.</li>
                <li><strong>F1 Score: 0.83</strong> The harmonic mean of precision and recall.</li>
            </ul>
        </div>

        <div class="feature-box">
            <h2>Results</h2>
            <p>The results include various visualizations:</p>
            <ul>
                <li>Feature distribution histograms.</li>
                <li>Cluster visualization showing data separation.</li>
                <li>Confusion matrix to analyze model predictions.</li>
            </ul>
        </div>

        <div class="feature-box">
            <h2>Installation</h2>
            <p>Follow these steps to run the project:</p>
            <ol>
                <li>Clone the repository:
                    <pre><code>git clone https://github.com/KunalParkhade/credit-card-fraud-detection.git</code></pre>
                </li>
                <li>Install the dependencies:
                    <pre><code>pip install -r requirements.txt</code></pre>
                </li>
            </ol>
        </div>

        <div class="feature-box">
            <h2>Future Improvements</h2>
            <p>Future enhancements could include:</p>
            <ul>
                <li>Adding more complex features such as transaction history.</li>
                <li>Experimenting with other clustering techniques like DBSCAN.</li>
                <li>Improving the z-score thresholding for better fraud detection.</li>
            </ul>
        </div>

        <a class="button" href="https://github.com/KunalParkhade/credit-card-fraud-detection" target="_blank">View on GitHub</a>
    </div>
</body>
</html>
