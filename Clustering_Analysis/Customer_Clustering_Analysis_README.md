# Customer Churn Analysis – Customer Segmentation Using K-Means

**ACS Work Integrated Learning – Data Analytics | Team 3**  
**Prepared by:** Abhishek Shakya  
**Role:** Data Analyst – Clustering Analysis

## Objective
Segment customers using `tenure` and `MonthlyCharges`, describe the resulting groups, and compare churn across segments after clustering.

## Dataset checks
- Dataset dimensions: 6,741 rows × 11 columns
- Duplicate rows: 0
- Missing values: 0 in all columns
- Clustering inputs: `tenure`, `MonthlyCharges`
- `Churn` was excluded from clustering and used only after cluster assignment.

## Method
1. Load the updated cleaned CSV using Pandas in Google Colab.
2. Inspect dimensions, columns and sample records.
3. Check duplicate rows and missing values.
4. Select `tenure` and `MonthlyCharges`.
5. Standardise both features using `StandardScaler`.
6. Fit K-Means for K=1 to K=10 and record inertia for the Elbow Method.
7. Select K=4 as a reasonable candidate and fit K-Means (`random_state=42`, `n_init=10`).
8. Visualise the segments using a tenure-versus-monthly-charges scatter plot.
9. Calculate customer counts and average feature values per cluster.
10. Compare churn counts and rates by cluster after clustering.
11. Export the dataset with cluster labels to `Customer_Clusters_Results.csv`.

## Results

| Cluster | Customers | Average tenure (months) | Average monthly charges | Churn rate* |
|---|---:|---:|---:|---:|
| 0 | 1,118 | 54.02 | $34.54 | 4.92% |
| 1 | 1,914 | 58.59 | $93.03 | 15.83% |
| 2 | 1,584 | 11.23 | $33.84 | 25.00% |
| 3 | 2,125 | 14.95 | $81.68 | 48.80% |

Cluster 3 is the largest segment and has the highest observed churn rate in the notebook summary. It may warrant further retention investigation. These are descriptive associations, not evidence of causation.

*The notebook calculates churn as `Churn == 1`. Confirm that 1 means churned and 0 means retained using the official dataset data dictionary before publishing these rates.*

## Tools
Python, Pandas, NumPy, Matplotlib, scikit-learn, Google Colab.

## Limitations / checks before final publication
- K=4 is a visual elbow-method choice, not a proven unique optimum. A silhouette score can be added if required.
- Cluster IDs are arbitrary labels.
- The fitted scaler and K-Means model are not saved in the notebook.
- Confirm the results CSV was downloaded successfully.
- Follow team data-governance rules; do not publish confidential or identifiable customer data.

## repository contents
- `notebooks/Abhishek___Clustering_Analysis_V2.ipynb`
- `docs/Team3_Customer_Clustering_Analysis_Documentation.docx`
- `README.md`
- `results/Customer_Clusters_Results.csv` 
