🏥 Patient Subtyping for Type 2 Diabetes
K-Means Clustering on Electronic Health Record (EHR) Data

This project performs unsupervised machine learning on clinical Electronic Health Record (EHR) data to identify patient subtypes for Type 2 Diabetes Mellitus.
Using K-Means clustering and PCA, we discover meaningful patterns that help differentiate metabolic, glycemic, and dyslipidemic risk groups.

📂 Project Structure
│── data/
│    └── Dataset.csv
│── notebook/
│    └── diabetes_clustering.ipynb
│── Clustered_Diabetes_Patients.csv
│── README.md

🚀 Project Workflow
1️⃣ Data Loading

Loaded Dataset.csv

Inspected shape, columns, and types.

Verified dataset consistency.

2️⃣ Data Preprocessing

Performed essential cleaning steps:

Checked for null values

Handled missing data using:

df.fillna(df.mean()) for numeric columns

Dropped unnecessary ID/object fields

Converted all relevant clinical fields to numeric

Applied StandardScaler to normalize all features

Why scaling?
➡️ Because K-Means uses Euclidean distance, and different scales (mg/dL vs years vs kg/m²) distort results.

3️⃣ Dimensionality Reduction (PCA)

Performed PCA for:

Visualization using PCA1 & PCA2

Understanding cluster separation

Reducing noise in high-dimensional EHR data

Generated:

PCA1

PCA2

4️⃣ Finding the Optimal Number of Clusters

Used 2 methods:

✔️ Elbow Method

Computed distortion (WCSS)

Observed elbow → k = 5

✔️ Silhouette Score

Confirmed cluster separation quality

Best silhouette score also matched k = 5

5️⃣ K-Means Clustering

Trained final model:

kmeans = KMeans(n_clusters=5, random_state=42)
labels = kmeans.fit_predict(X_scaled)
df["Cluster"] = labels


Added cluster labels back into the original dataframe

Exported full results to:

Clustered_Diabetes_Patients.csv

🎨 6️⃣ Visualization
✔️ PCA 2D Cluster Plot

Shows how clusters separate in reduced dimensions.

✔️ Cluster Count Plot

Bar plot of patients in each cluster.

✔️ Heatmap of Cluster Means

Shows how each clinical feature differs across clusters.

🧬 7️⃣ Cluster Profiling (Medical Interpretation)

Based on mean biomarker values:

Cluster 0 — Moderate Metabolic Syndrome

HbA1c moderately high

BMI high

Lipids slightly abnormal

Cluster 1 — Severe Diabetes + Severe Dyslipidemia (High Risk)

Highest HbA1c (~10)

Extremely high TG, LDL, VLDL

Obese

Highest cardiovascular risk

Cluster 2 — Healthy / Low-Risk Group

Normal HbA1c (~5.3)

Normal BMI (~23)

Best lipid profile

Younger population

Cluster 3 — Stable Diabetic with Mild Lipid Issues

HbA1c 8.6

Mild hyperlipidemia

Obese

Cluster 4 — High HbA1c but Normal Lipids

HbA1c ~9.3

Lipids controlled

Obese older patients

📁 8️⃣ Saving the Results

Exported final dataset:

df.to_csv("Clustered_Diabetes_Patients.csv", index=False)


This CSV includes:

Original clinical values

Scaled values

PCA1 & PCA2

Cluster label

(Optional) cluster subtype names

🧾 9️⃣ Conclusion

This project successfully identifies five clinically meaningful patient subtypes using unsupervised learning on EHR data.
This segmentation can help hospitals and doctors understand:

Glycemic risk

Lipid-driven risk

Metabolically healthy diabetics

Patients needing urgent intervention

🛠️ 1️⃣0️⃣ Technologies Used

Python

Pandas

NumPy

Scikit-Learn

Matplotlib

Seaborn

PCA

K-Means