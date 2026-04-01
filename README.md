# 🚗 Car Market Clustering: K-Means vs DBSCAN on 3.55 Million Listings

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0%2B-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-blue?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.5%2B-green?logo=matplotlib&logoColor=white)](https://matplotlib.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**End-to-end unsupervised learning project** that turns a massive raw car dataset into meaningful market segments using **K-Means** and **DBSCAN**.

> From 3,552,912 real listings (Nov 2015 – Mar 2017) → clear clusters of **budget**, **premium**, and **high-performance** cars with full EDA, smart preprocessing, PCA visualization, and rigorous model comparison.

---

## ✨ Key Highlights
- **Dataset**: 3.55 million rows × 16 features (mileage, price, manufacture year, maker, fuel type, etc.)
- **Major Challenges Tackled**: Extreme outliers (9,999,999 km, €2.7 trillion prices), 94% missing `color_slug`, 85% missing `stk_year`
- **Clustering Results**:
  - **K-Means (k=4)** → Silhouette Score **0.141** | Davies-Bouldin **1.816**
  - **DBSCAN (eps=2.0)** → Silhouette Score **0.015** | Davies-Bouldin **1.376** (better separation excluding noise)
- **Business Insight**: Discovered distinct segments (newer low-mileage premium cars vs older high-mileage budget cars)
- **Visuals**: Histograms, correlation heatmaps, count plots, elbow method, silhouette analysis, and beautiful 2D PCA cluster plots

---

## 📊 What You'll Find Inside

### 1. Exploratory Data Analysis (EDA)
- Right-skewed distributions for **mileage** and **price**
- Strong positive correlation: newer cars = higher price
- Strong negative correlation: higher mileage = lower price
- Dominant categories: Gasoline & Diesel fuel, manual transmission, Škoda as most frequent maker

### 2. Preprocessing Pipeline
- Dropped highly missing columns (`color_slug`, `stk_year`)
- Imputed `model` with mode (`octavia`)
- Filled numerical columns with median (robust to outliers)
- Engineered **days_active** feature from `date_created` & `date_last_seen`
- Scaled numerical features + label-encoded categoricals

### 3. Clustering & Evaluation
- **K-Means** (spherical clusters, k=4 chosen via elbow + silhouette)
- **DBSCAN** (density-based, handles arbitrary shapes & noise automatically)
- PCA → 2D visualization of both algorithms
- Quantitative comparison using Silhouette & Davies-Bouldin scores

**Cluster Profiles (K-Means)**

| Cluster | Size     | Mean Year | Mean Mileage (km) | Mean Price (€) | Interpretation          |
|---------|----------|-----------|-------------------|----------------|-------------------------|
| 0       | 72,756   | 2009      | 114,619           | 2,360          | Budget / older cars     |
| 1       | 525,526  | 2012      | 57,630            | 18,272         | Premium / low mileage   |
| 2       | 678,642  | 2011      | 47,682            | 10,927         | Mid-range               |
| 3       | 938,682  | 2004      | 148,822           | 2,831          | High-mileage budget     |

---

## 📸 Visualizations (included in notebook)

- Mileage & Price distributions with KDE
- Top 10 fuel types & transmission counts
- Full correlation matrix + pairwise plots
- Elbow method & Silhouette scores
- PCA scatter plots of K-Means vs DBSCAN clusters

*(Screenshots of all figures are in the `images/` folder — they look stunning on the repo!)*

---

## 🛠️ How to Run the Project

1. Clone the repo
   ```bash
   git clone https://github.com/yourusername/car-market-clustering-kmeans-dbscan.git
   cd car-market-clustering-kmeans-dbscan
