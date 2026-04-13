#  Breast Cancer Diagnosis Prediction

---

##  Project Structure

```
Breast-Cancer-Diagnosis/
│
├── breast_cancer_analysis.ipynb
├── README.md
├── data/
│   └── data.csv
└── images/
```

##  Project Overview

This project aims to build a machine learning model to predict whether a breast tumor is **Benign (non-cancerous)** or **Malignant (cancerous)** using features extracted from digitized images of fine needle aspirate (FNA) of breast masses.

The workflow includes:

* Exploratory Data Analysis (EDA)
* Feature Selection
* Handling Skewness & Outliers
* Multicollinearity Detection using VIF
* Data Preprocessing (Scaling & Transformation)
* Model Building using Logistic Regression
* Performance Evaluation

---

##  Dataset Description

The dataset used is the **Breast Cancer Wisconsin (Diagnostic) Dataset**.

###  General Information

* Total Records: **569 samples**
* Total Features: **30 numerical features**
* Target Variable: `diagnosis`

  * **0 → Benign**
  * **1 → Malignant**

---

###  Feature Explanation

The features describe characteristics of the cell nuclei present in the image:

####  Size-related Features

* `radius`: Mean distance from center to points on the perimeter
* `perimeter`: Length of the boundary of the cell
* `area`: Area of the cell nucleus

####  Texture Feature

* `texture`: Standard deviation of gray-scale values (variation in intensity)

####  Shape Features

* `smoothness`: Smoothness of the cell boundary
* `compactness`: Measure of shape compactness
* `concavity`: Severity of concave portions
* `concave points`: Number of concave points
* `symmetry`: Symmetry of the cell
* `fractal_dimension`: Complexity of the boundary

---

###  Feature Types

Each feature appears in three forms:

* **_mean** → Average value
* **_se** → Standard error
* **_worst** → Worst (largest) value

Example:

* `radius_mean`
* `radius_se`
* `radius_worst`

---

##  Exploratory Data Analysis (EDA)

* Checked for missing values → Dataset is clean
* Detected skewness in multiple features → Applied log transformation
* Identified outliers using boxplots and IQR method
* Visualized distributions using histograms and KDE plots

---

##  Feature Selection

* Selected features with **correlation > 0.5** with the target
* Detected multicollinearity using **Variance Inflation Factor (VIF)**
* Iteratively removed features with **VIF > 10**

###  Final Selected Features:

* `concave points_worst`
* `radius_mean`
* `concavity_worst`
* `compactness_mean`
* `compactness_worst`
* `perimeter_se`

---

##  Data Preprocessing

* Applied **log transformation** to reduce skewness
* Applied **StandardScaler** to normalize features (mean=0, std=1)
* Prepared final dataset for modeling

---

##  Model Building

* Model Used: **Logistic Regression**
* Train/Test Split: **80% / 20%**
* Stratified sampling used to preserve class distribution

---

##  Model Performance

* **Accuracy: 96%**

### Classification Report:

* **Benign**

  * Precision: 0.94
  * Recall: 1.00
* **Malignant**

  * Precision: 1.00
  * Recall: 0.88

###  Key Observation:

The model achieves **high precision for malignant cases**, minimizing false positives, which is critical in medical diagnosis.

---

##  Key Insights

* Strong predictors:

  * `concave points_worst`
  * `radius_mean`
  * `concavity_worst`

* Removing multicollinearity significantly improved model stability

* Scaling and handling skewness enhanced model performance

* Model performs well in detecting both classes with high reliability

---

##  How to Run

```bash
git clone https://github.com/<your-username>/Breast-Cancer-Diagnosis.git
cd Breast-Cancer-Diagnosis
pip install -r requirements.txt
jupyter notebook
```

---



---

##  Future Improvements

* Try advanced models (Random Forest, XGBoost)
* Apply cross-validation
* Hyperparameter tuning
* Deploy as a web app (Streamlit)

---

##  Conclusion

This project demonstrates how proper **EDA, feature engineering, and preprocessing** can significantly improve model performance, even with a simple algorithm like Logistic Regression.

---

##  License

This project is for educational purposes and open-source use.
