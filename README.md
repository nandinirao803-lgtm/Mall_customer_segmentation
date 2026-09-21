# 🛍️ Mall Customer Segmentation using K-Means Clustering

An unsupervised machine learning project that groups mall customers into **5 distinct segments** based on their **Annual Income** and **Spending Score**, so that the marketing team can design targeted campaigns for each group.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-K--Means-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Table of Contents

- [Problem Statement](#-problem-statement)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Project Workflow](#-project-workflow)
- [Results](#-results)
- [Customer Segments](#-customer-segments)
- [Business Recommendations](#-business-recommendations)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Future Improvements](#-future-improvements)
- [Author](#-author)

---

## 🎯 Problem Statement

A mall wants to understand its customers better instead of treating everyone the same. Since there are no predefined labels, this is an **unsupervised learning** problem. We use **K-Means Clustering** to discover natural groups of customers who share similar spending behaviour.

## 📊 Dataset

**File:** `Mall_Customers.csv` — 200 customers, 5 columns, no missing values, no duplicates.

| Column | Description |
|---|---|
| `CustomerID` | Unique ID of the customer |
| `Gender` | Male / Female |
| `Age` | Age of the customer |
| `Annual Income (k$)` | Yearly income in thousands of dollars |
| `Spending Score (1-100)` | Score assigned by the mall based on spending behaviour |

## 🛠️ Tech Stack

- **Language:** Python
- **Data handling:** pandas, numpy
- **Visualization:** matplotlib, seaborn
- **Machine learning:** scikit-learn (K-Means, Agglomerative Clustering, DBSCAN, PCA, StandardScaler)
- **Hierarchical clustering / dendrogram:** scipy

## 🔄 Project Workflow

1. **Data understanding** – shape, data types, statistical summary, missing values, duplicates
2. **Exploratory Data Analysis (EDA)**
   - Gender, Age, Income and Spending Score distributions
   - Boxplots and IQR-based outlier detection
   - Correlation heatmap and pairplot
   - Age-group analysis
3. **Feature selection** – `Annual Income` and `Spending Score`
4. **Feature scaling** – `StandardScaler`
5. **Finding optimal K** – Elbow Method + Silhouette Score
6. **Model training** – K-Means with `k-means++` initialization (K = 5)
7. **Cluster profiling** – statistics, gender split and boxplots per cluster
8. **Model comparison** – Hierarchical Clustering (Ward) and DBSCAN
9. **Dimensionality reduction** – PCA on all features for visualization
10. **Evaluation** – Inertia, Silhouette Score, Davies-Bouldin Index, silhouette plot
11. **Export** – final clustered dataset saved as CSV

## 📈 Results

Silhouette score was highest at **K = 5**, which agrees with the elbow curve:

| K | Silhouette Score |
|:-:|:-:|
| 2 | 0.3213 |
| 3 | 0.4666 |
| 4 | 0.4939 |
| **5** | **0.5547** |
| 6 | 0.5399 |
| 7 | 0.5281 |
| 8 | 0.4552 |
| 9 | 0.4571 |
| 10 | 0.4432 |

**Final model (K = 5):**

| Metric | Value | Better when |
|---|:-:|---|
| Inertia (WCSS) | 65.57 | Lower |
| Silhouette Score | 0.5547 | Higher |
| Davies-Bouldin Index | 0.5722 | Lower |

**Cross-check with other algorithms:**
- **Hierarchical Clustering** (Ward linkage, dendrogram) supports 5 natural groups.
- **DBSCAN** found 4 dense clusters and flagged 15 points as noise.
- **PCA** (2 components) explains about 60% of the variance when all four numeric features are used.

## 👥 Customer Segments

| Cluster | Segment | Avg Age | Avg Income (k$) | Avg Spending Score | Customers |
|:-:|---|:-:|:-:|:-:|:-:|
| 0 | **Average Customers** (medium income, medium spending) | 42.7 | 55.3 | 49.5 | 81 |
| 1 | **Target Customers** (high income, high spending) | 32.7 | 86.5 | 82.1 | 39 |
| 2 | **Impulsive Spenders** (low income, high spending) | 25.3 | 25.7 | 79.4 | 22 |
| 3 | **Careful Spenders** (high income, low spending) | 41.1 | 88.2 | 17.1 | 35 |
| 4 | **Budget Customers** (low income, low spending) | 45.2 | 26.3 | 20.9 | 23 |

> Cluster numbers can change between runs or library versions. Always match segment names against the cluster summary table before labelling.

## 💡 Business Recommendations

- **Target Customers** – most valuable group. Focus on premium launches, loyalty programs and personalized offers.
- **Careful Spenders** – have the purchasing power but spend little. Use engagement campaigns, exclusive previews and incentives.
- **Impulsive Spenders** – respond well to discounts, flash sales and EMI / installment options.
- **Budget Customers** – price sensitive. Reach them with value bundles and essential-product promotions.
- **Average Customers** – the largest group. General campaigns and seasonal offers work well.

## 📁 Project Structure

```
Mall-Customer-Segmentation/
│
├── Mall_Customer_Segmentation_KMeans_Full.ipynb   # Complete analysis notebook
├── Mall_Customers.csv                              # Original dataset
├── Mall_Customers_Clustered.csv                    # Dataset with cluster labels
├── requirements.txt                                # Python dependencies
└── README.md
```

## ▶️ How to Run

1. **Clone the repository**
```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
```

2. **Install dependencies**
```bash
   pip install -r requirements.txt
```

3. **Launch the notebook**
```bash
   jupyter notebook Mall_Customer_Segmentation_KMeans_Full.ipynb
```

4. Run all cells from top to bottom. The clustered dataset will be saved as `Mall_Customers_Clustered.csv`.

## 🚀 Future Improvements

- Include Age as a clustering feature and compare results
- Try K-Prototypes to use Gender natively as a categorical feature
- Build a Streamlit app to predict the segment of a new customer
- Create an interactive dashboard (Power BI / Tableau) for the marketing team

## 👤 Author

**Nandini Rao**


- GitHub:https://github.com/nandinirao803-lgtm

---

⭐ If you found this project useful, consider giving it a star!
