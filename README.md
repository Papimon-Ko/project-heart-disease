# 🩺 End-to-End Heart Disease Classification Project

This project aims to build and refine a classification model to predict which patients are likely to have heart disease using the UCI Cleveland Heart Disease Dataset.

## 🛠️ Tools and Libraries Used

* **Language:** Python
* **Core Libraries:** Pandas, NumPy, Matplotlib, Seaborn
* **Model:** Scikit-Learn (Logistic Regression, RandomForestClassifier, KNeighborsClassifier)
* **Techniques:** `train_test_split`, `GridSearchCV`, `RandomizedSearchCV`, `cross_val_score`

---
## 📊 Exploratory Data Analysis (EDA)

Based on the initial dataset analysis, Key conclusions were as follows:

### 1. Data Structure

* **Data Size:** 303 rows and 14 columns (attributes)
* **Missing Data:** **No missing** data in the dataset
* **Target Distribution:** The data is relatively balanced, with 165 patients with heart disease (target=1) and 138 patients without heart disease (target=0).
*

### 2. Significant Relationships

* **Sex:**
* Women (sex=0) in this dataset are significantly more likely to have heart disease than men (sex=1) (approximately 75% of women have the disease).
*
* **Chest Pain (cp):**
* Patients with chest pain types **2** and **3** have significantly more heart disease than those without.
*
* **Age (age) and Maximum Heart Rate (`thalach`):**
* It was found that patients with heart disease tend to have higher maximum heart rates.
*

---

## 🧠 Model Construction and Tuning

### 1. Initial Model Results

Three models were tested with default hyperparameters on a test set separated from 20% of the data (61 samples):

| Model | Accuracy Score on the Test Set |
| :--- | :--- |
| **Logistic Regression** | **88.52%** |
| Random Forest | 83.61% |
| K-Nearest Neighbors | 68.85% |

*

### 2. Hyperparameter Tuning

The model that performed best in the initial run was **Logistic Regression** and was selected for fine-tuning using **GridSearchCV**.

* **Random Forest:** After tuning with The accuracy of Randomized Search CV increased to **86.89%**.
* **Logistic Regression (GridSearchCV):** Uses the Grid Search technique to find the best value of `C` (`log_reg_grid = {"C":np.logspace(-4,4,30), "solver":["liblinear"]}`).

**🎯 Best result:**

**Logistic Regression** model after optimization with `GridSearchCV` yielded the best results.

| Metrics | Score (on the test set) |
| :--- | :--- |
| **Accuracy Score** | **90.16%** (when using `cross_val_score` on the entire dataset) |
| Best C Value | `0.20433597178569418` |

## 🚀 Summary and Next Steps

The modified **Logistic Regression** model was the most effective for classifying this type of heart disease, with an accuracy score of over **90%**.

The next step is to evaluate the model against other metrics (e.g., Precision, Recall, F1-Score, ROC-AUC) and create a Confusion Matrix for a more complete understanding.
