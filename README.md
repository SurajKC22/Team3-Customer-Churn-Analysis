# Team 3 – Customer Churn Analysis

ACS Work Integrated Learning – Data Analytics (WILDA26_09)

We are analysing customer data from a telecommunications company to understand why customers leave and which customers are most at risk. The work is split into three parts: preparing the data, grouping customers with K-Means clustering, and predicting churn with an Artificial Neural Network (ANN).

## Team

| Member | Role | Folder |
|---|---|---|
| Suraj K C | Project Manager | Reports |
| Tek Raj Bhatta | Data Engineer – data preparation | Data_Preparation |
| Harpreet Kaur | Data Engineer – data preparation | Data_Preparation |
| Abhishek Shakya | Data Analyst – clustering | Clustering_Analysis |
| Zannatul Ferdous (Annie) | Data Analyst – predictive modelling | Predictive_Modelling |
| Muhammad Haziq Sameed | Business Analyst – insights and reporting | Reports |

## Repository structure

```
Team3-Customer-Churn-Analysis/
├── Data_Preparation/       Stage 2-1: cleaned dataset, train/test sets, scaling
├── Clustering_Analysis/    Stage 2-2: elbow method, K-Means model, cluster visuals
├── Predictive_Modelling/   Stage 3: ANN churn model and results
└── Reports/                Business insights, recommendations and meeting documents
```

## Stage 2 deliverables – where to find them

### 2-1 Data Preparation (`Data_Preparation/`)

| Requirement | File(s) |
|---|---|
| Preprocessed dataset (missing data checked, categories encoded) | `Final_Files_Both_version/Customer_Churn_Preprocessed_v2.csv` |
| Training and testing sets | `Final_Files_Both_version/X_train_scaled_v2.csv`, `X_test_scaled_v2.csv`, `y_train_v2.csv`, `y_test_v2.csv` |
| Size and composition of the sets | `data preprocessing documentation.docx` (section on the train/test split) |
| Scaling techniques with code snippets | `data preprocessing documentation.docx` |
| Code | `Final_Files_Both_version/Data_Engineering.ipynb` |

Summary:
- The original data has 7,043 records and 10 columns, with no missing values.
- 302 exact duplicate rows were removed in Version 2, leaving 6,741 records.
- Categorical columns were encoded as numbers.
- The data was split 80/20 with stratification and `random_state=42`: 5,392 training records and 1,349 testing records.
- Features were scaled with `StandardScaler`.

**Version 2 is the final version** and is the one used by the clustering and ANN work. Version 1 (which keeps the duplicate rows) is kept for reference.

### 2-2 Clustering Analysis (`Clustering_Analysis/`)

| Requirement | File(s) |
|---|---|
| Optimal number of clusters (elbow method) | `Clustering_Analysis_Elbow_Plot.png`, `Customer_Clustering_Analysis_Documentation.docx` |
| Trained K-Means model and code | `kmeans_model.pkl`, `Abhishek___Clustering_Analysis_V2.ipynb` |
| Labelled cluster visualisation and insights | `Clustering_Analysis_Cluster_Scatter_Plot.png`, `Customer_Clusters_Results.csv`, `Customer_Clustering_Analysis_README.md` |

Summary:
- Customers were grouped on `tenure` and `MonthlyCharges`, scaled with `StandardScaler`. Churn was left out of the clustering and only used afterwards to profile each group.
- The elbow plot (K = 1 to 10) flattens at **K = 4**.

| Cluster | Customers | Avg tenure (months) | Avg monthly charge | Churn rate |
|---|---:|---:|---:|---:|
| 0 – Long-term, low spend | 1,118 | 54.0 | $34.54 | 4.9% |
| 1 – Long-term, high spend | 1,914 | 58.6 | $93.03 | 15.8% |
| 2 – New, low spend | 1,584 | 11.2 | $33.84 | 25.0% |
| 3 – New, high spend | 2,125 | 15.0 | $81.68 | 48.8% |

**Key finding:** newer customers on higher monthly charges (Cluster 3) are the largest group and churn the most, at almost half. This is the group to focus retention efforts on.

## Stage 3 – Predictive Modelling (`Predictive_Modelling/`)

This folder holds the ANN churn model, its test-set predictions and the evaluation charts. See `Predictive_Modelling/README.md` for details.

## Tools

Python, Pandas, NumPy, Matplotlib, scikit-learn and Google Colab. Tasks are tracked in Jira (project CHURN), and commits reference the Jira issue key.
