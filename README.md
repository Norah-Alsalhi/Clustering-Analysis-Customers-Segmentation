## Mall Customer Segmentation (K-Means & Hierarchical Clustering)

Unsupervised learning project for customer segmentation, built as **Project 3** of the **Clarusway Machine Learning Bootcamp**. The goal is to group mall customers into meaningful segments using **K-Means** and **Agglomerative (Hierarchical) Clustering**, then interpret each segment to suggest marketing strategies.

## Dataset

**Mall Customers Dataset** (`Mall_Customers.csv`) — 200 customers with the following features:

| Feature | Description |
|---|---|
| `CustomerID` | Unique customer ID (dropped — acts as an index) |
| `Gender` | Male / Female |
| `Age` | Customer age |
| `Annual_Income` | Annual income (k$) |
| `Spending_Score` | Score assigned by the mall (1–100) based on spending behavior |

## Project Workflow

### 1. Data Exploration & Cleaning
- Renamed columns for easier handling, dropped `CustomerID`
- Checked data types, missing values, and duplicates (none found)

### 2. Exploratory Data Analysis (EDA)
- Distribution plots for Age, Annual Income, and Spending Score
- Gender breakdown (more females than males in the data)
- Violin, box, and swarm plots comparing income and spending across genders
- Correlation heatmap and pairplot to spot potential cluster structure

### 3. Clustering Tendency
- **Hopkins statistic** used to verify the data is actually clusterable before applying any algorithm

### 4. K-Means Clustering
Applied on two feature pairs:
- **Age vs. Spending Score** → optimal **k = 4**
- **Annual Income vs. Spending Score** → optimal **k = 5**

Optimal *k* determined using:
- **Elbow Method** (WCSS / inertia)
- **Silhouette Score** + Yellowbrick `SilhouetteVisualizer`

### 5. Hierarchical (Agglomerative) Clustering
- Dendrograms built with four linkage methods: `ward`, `complete`, `average`, `single`
- Silhouette scores compared across cluster counts
- Results visualized side-by-side with K-Means — **K-Means produced sharper, better-separated clusters**

### 6. Cluster Interpretation & Business Insights
Segments from Annual Income vs. Spending Score (k = 5) include, for example:
- **Loyal high-value customers** — high income, high spending → the main profit source; keep them satisfied
- **High income, low spending** — the key *target audience*; needs dedicated strategies to convert income into spending
- **Low income, low spending** — can be nudged with gift certificates and promotions
- **Young, low income but high spending** — engaged young customers worth retaining

Cluster profiles were also broken down by **gender** to refine the marketing recommendations.

## ️ Tech Stack

- **Python** — pandas, NumPy
- **Visualization** — Matplotlib, Seaborn
- **ML** — scikit-learn (`KMeans`, `AgglomerativeClustering`, silhouette metrics), SciPy (`linkage`, `dendrogram`)
- **Diagnostics** — Yellowbrick (SilhouetteVisualizer), custom Hopkins statistic implementation

## How to Run

1. Clone the repo:
   ```bash
   git clone <repo-url>
   cd <repo-folder>
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn scipy yellowbrick
   ```
3. Place `Mall_Customers.csv` in the project folder (or update the path in the notebook — the original notebook loads it from Google Drive via Colab).
4. Open and run the notebook:
   ```bash
   jupyter notebook Project3_Clustring.ipynb
   ```

>  The notebook was developed on **Google Colab**; if running there, just upload the CSV to your Drive and keep the `drive.mount` cell.

## Key Takeaways

- Silhouette analysis is more decisive than the elbow method when the elbow is ambiguous
- K-Means outperformed hierarchical clustering on this dataset in terms of cluster separation
- The 5-cluster segmentation on **Income × Spending Score** gives the clearest, most actionable customer segments

---

<img width="600" height="71" alt="408671304-1fadf25b-848a-42ec-950c-0125f5c90047" src="https://github.com/user-attachments/assets/45fa494a-4662-46f1-9d70-b2f3aebe5dd4" />
<img width="442" height="114" alt="408671675-06fe6c8b-99cb-4948-a9b1-48c1cf0c0b3f" src="https://github.com/user-attachments/assets/439f943d-ae6c-4ed0-8a82-ae3641c79aa7" />

