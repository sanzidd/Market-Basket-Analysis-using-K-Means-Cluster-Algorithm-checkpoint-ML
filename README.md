# 🛒 Market Basket Analysis using K-Means Clustering

<div align="center">

![Python](https://img.shields.io/badge/Python-3.13-blue?style=for-the-badge&logo=python)
![scikit-learn](https://img.shields.io/badge/scikit--learn-KMeans-orange?style=for-the-badge&logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter)
![Status](https://img.shields.io/badge/Status-Practice%20Project-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

**A customer segmentation project applying K-Means clustering to mall customer data, exploring how annual income and spending behavior can be used to identify distinct shopper groups.**

[📂 View on GitHub](https://github.com/sanzidd/Market-Basket-Analysis-using-K-Means-Cluster-Algorithm-checkpoint-ML) · [🚀 Quick Start](#-quick-start) · [📊 Results](#-results)

</div>

---

## 📌 Overview

Understanding customer behavior is at the heart of modern retail strategy. This practice project applies **K-Means clustering** — a fundamental unsupervised machine learning algorithm — to segment mall customers based on their **annual income** and **spending score**. The project explores the full K-Means workflow: from data preparation and exploratory analysis through optimal cluster selection using the **Elbow Method** and **KneeLocator**, to 2D and 3D cluster visualization.

---

## ✨ Features

- **Clean EDA Pipeline** — data inspection, null checking, column renaming, and dropping irrelevant features
- **Elbow Method** — WCSS (Within-Cluster Sum of Squares) computed for k=1 to 14 to determine the optimal number of clusters
- **Automated Knee Detection** — `KneeLocator` from the `kneed` library used to programmatically identify the elbow point
- **Multiple K-Means Experiments** — models trained with different values of `k` (including 8 and 5) to compare segmentation behavior
- **2D Cluster Visualization** — scatter plots of Income vs Spending Score with centroid markers
- **3D Cluster Visualization** — three-dimensional scatter plot incorporating Age, Income, and Spending Score
- **Manual Cluster Inspection** — individual cluster DataFrames explored to understand customer profiles within each group
- **Single-sample Prediction** — real-time prediction of cluster assignment for a new customer using `km.predict()`

---

## 📊 Dataset

| Property | Details |
|---|---|
| **File** | `mall customers.csv` |
| **Total Samples** | 200 customers |
| **Original Features** | `CustomerID`, `Gender`, `Age`, `Annual Income (k$)`, `Spending Score (1-100)` |
| **Features Used** | `age`, `income`, `score` (CustomerID and Gender dropped) |
| **Missing Values** | None |

### Feature Description

| Feature | Description |
|---|---|
| `age` | Customer age |
| `income` | Annual income in thousands of dollars |
| `score` | Mall-assigned spending score from 1 (low) to 100 (high) |

---

## 🏗️ Project Structure

```
Market-Basket-Analysis-using-K-Means-Cluster-Algorithm/
│
├── Market_Basket_Analysis_using_K-Means_Cluster_Algorithm.ipynb   # Main notebook
├── mall customers.csv                                               # Dataset
└── README.md
```

---

## 🔬 Methodology

### 1. Data Loading & Preprocessing
- Loaded `mall customers.csv` with 200 records and 5 features
- Dropped `CustomerID` and `Gender` as non-numeric, non-informative columns for clustering
- Renamed columns to concise lowercase aliases (`age`, `income`, `score`)
- Confirmed zero missing values across all features

### 2. Exploratory Data Analysis
- Inspected shape, data types, and descriptive statistics
- Visualized distributions of age, income, and spending score using Seaborn

### 3. Optimal K Selection — Elbow Method
- Computed **WCSS** for k = 1 through 14 by fitting K-Means models iteratively
- Plotted the WCSS curve to visually identify the "elbow" — the point of diminishing returns
- Used `KneeLocator` (from the `kneed` library) to detect the optimal `k` programmatically

### 4. K-Means Clustering
Two main clustering experiments were conducted:

**Experiment 1 — k=8 (Income × Score):**
- Fitted K-Means with 8 clusters on `income` and `score`
- Assigned cluster labels back to the DataFrame as `km1_cluster`
- Inspected individual clusters (e.g. cluster 7 — low-income, moderate-spending customers)
- Predicted cluster assignment for a new sample: `km1.predict([[20, 37]])`
- Printed all 8 cluster centroids

**Experiment 2 — k=5 (Income × Score):**
- Refitted K-Means with the optimal 5 clusters identified by the elbow method
- Visualized the 5 resulting segments as a 2D scatter plot with centroids marked

### 5. 3D Clustering
- Extended clustering to 3 features: `score`, `income`, and `age`
- Fitted a new K-Means model and visualized the resulting clusters in a 3D scatter plot using Matplotlib

---

## 📈 Results

The **Elbow Method** and **KneeLocator** together pointed to **k=5** as the optimal number of clusters when segmenting on Income and Spending Score. The 5 customer segments identified represent meaningful behavioral groups commonly seen in retail analytics:

| Segment | Income | Spending Score | Profile |
|---|---|---|---|
| 1 | High | High | 💎 Target customers — high value |
| 2 | Low | High | 🛍️ Impulsive / aspirational shoppers |
| 3 | High | Low | 💼 Cautious high earners |
| 4 | Low | Low | 🪙 Budget-conscious shoppers |
| 5 | Medium | Medium | 📊 Average / standard customers |

> Full cluster scatter plots and 3D visualizations are available inside the notebook.

---

## 🚀 Quick Start

### Prerequisites

```bash
pip install pandas scikit-learn matplotlib seaborn kneed
```

### Clone the Repository

```bash
git clone https://github.com/sanzidd/Market-Basket-Analysis-using-K-Means-Cluster-Algorithm-checkpoint-ML.git
cd Market-Basket-Analysis-using-K-Means-Cluster-Algorithm-checkpoint-ML
```

### Run the Notebook

```bash
jupyter notebook Market_Basket_Analysis_using_K-Means_Cluster_Algorithm.ipynb
```

### Predict Cluster for a New Customer

```python
from sklearn.cluster import KMeans

# Assuming model is already trained
# income=20k$, spending_score=37
cluster = km.predict([[20, 37]])
print(f"Customer belongs to cluster: {cluster[0]}")
```

---

## 📦 Tech Stack

| Category | Libraries |
|---|---|
| **Data Manipulation** | `pandas` |
| **Machine Learning** | `scikit-learn` (KMeans) |
| **Visualization** | `matplotlib`, `seaborn` |
| **Optimal K Detection** | `kneed` (KneeLocator) |
| **Environment** | Jupyter Notebook, Python 3.13, Conda |

---

## 💡 Key Concepts Practiced

- Unsupervised learning with K-Means clustering
- WCSS computation and the Elbow Method
- Automated knee/elbow detection with `KneeLocator`
- 2D and 3D cluster scatter plot visualization
- Customer segmentation for retail and marketing analytics

---

## 🤝 Contributing

This is a practice project, but contributions, suggestions, and feedback are welcome! Feel free to open an issue or submit a pull request on [GitHub](https://github.com/sanzidd/Market-Basket-Analysis-using-K-Means-Cluster-Algorithm-checkpoint-ML).

---

## 👤 Author

**Sanzid Islam**

- GitHub: [@sanzidd](https://github.com/sanzidd)
- Kaggle: [sanzidislam99](https://www.kaggle.com/sanzidislam99)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

<div align="center">
⭐ Found this helpful? Give it a star on <a href="https://github.com/sanzidd/Market-Basket-Analysis-using-K-Means-Cluster-Algorithm-checkpoint-ML">GitHub</a>!
</div>
