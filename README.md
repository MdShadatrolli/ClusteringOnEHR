# 🏥 Clustering on EHR (Electronic Health Records)

This project applies **Unsupervised Machine Learning (K-Means Clustering)** to Electronic Health Records (EHR) to identify meaningful **patient subgroups** based on clinical biomarkers.  

The goal is to help doctors and hospitals better understand patient risk categories using data-driven segmentation.

---

## 🚀 Project Workflow

### **1. Data Preprocessing**
- Loaded raw `Dataset.csv` containing EHR biomarkers.
- Handled missing values.
- Converted object columns → numeric where needed.
- Applied **StandardScaler** to normalize measurement units.

### **2. Dimensionality Reduction**
- Applied **PCA (Principal Component Analysis)**.
- Generated:
  - `PCA1`
  - `PCA2`
- Used later for visualization & understanding cluster separation.

### **3. K-Means Clustering**
- Used **Elbow Method** and **Silhouette Score** → best value: **k = 5**
- Trained final model:
