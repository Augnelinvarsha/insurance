# insurance
insurance-project
Insurance Claim Prediction
This project uses a dataset of insurance policyholders to predict whether an individual will file an insurance claim based on demographic and health-related features.

📁 Dataset Description
The dataset contains the following columns:

Column	Description
age	Age of the policyholder
sex	Gender of the policyholder (0 = Female, 1 = Male)
bmi	Body Mass Index
children	Number of children/dependents
smoker	Smoking status (1 = Smoker, 0 = Non-smoker)
region	Geographic region (0–3 categorical)
charges	Medical insurance charges
insuranceclaim	Target variable (1 = Claim made, 0 = No claim)
🎯 Objective
Predict the likelihood that a person will file an insurance claim using features like age, BMI, smoking status, etc.

🧪 Models Used
Logistic Regression
Random Forest
Gradient Boosting
(Optional) Neural Network
⚙️ Setup
Clone the repo
Install dependencies:
pip install -r requirements.txt
python main.py
[![researchgate.net/figure/...](https://images.openai.com/thumbnails/url/CBCEZXicu1mSUVJSUGylr5-al1xUWVCSmqJbkpRnoJdeXJJYkpmsl5yfq5-Zm5ieWmxfaAuUsXL0S7F0Tw52jfT08TSpqCj2Kc-u9EkKT0suNXaMtzDOD_D38_es9A3J9jDK9U4vdjUtMsw0zTc3zPcpMSh1jC8LDVQrBgAeVSnG)](https://www.researchgate.net/figure/Scatter-plot-of-BMI-vs-Charges_fig4_379486812)

Here are some deeper insights and analyses from various projects and studies on this dataset:

---

## 🔍 Key Statistical Findings

* **Distributions & outliers**

  * *BMI* is approximately normally distributed, but *charges* are right‑skewed with substantial outliers (max ≈ \$63,770, min ≈ \$1,122) ([Codecademy Forums][1], [a-s620.github.io][2]).
  * Typically, the **median** is used to evaluate "typical" charges due to skew.

* **Demographics**

  * Mean: age ≈ 39 years, BMI ≈ 30.66, children ≈ 1.09 ([a-s620.github.io][2]).
  * Gender split is \~50:50 (676 male, 662 female). Smokers comprised \~20.5% (274/1,338) ([GitHub][3], [a-s620.github.io][2]).

---

## 🩺 Relationships Between Predictors & Charges

* **Smoking**
  Smokers are charged \~4× more on average.

  * Smokers avg ≈ \$32k vs non-smokers ≈ \$8.4k ([GitHub][4]).
  * Among smokers, those with BMI ≥ 30 have average charges \~ \$41,558 vs \~ \$20,167 for BMI < 30 ([GitHub][4]).

* **BMI**

  * Higher BMI correlates with higher charges, especially pronounced for smokers ([amlyfe.github.io][5], [a-s620.github.io][2]).
  * Comparing BMI categories: underweight \~\$8.8k, normal \~\$10.4k, overweight \~\$13.9k — showing a clear upward trend ([Medium][6]).

* **Age**

  * Charges increase with age, though correlation is moderate (\~0.3) ([GitHub][4]).
  * Breakdown by life stage: teens \~\$8.4k, adults \~\$10.6k, middle-aged \~\$15.4k, seniors \~\$21.2k ([GitHub][7]).

* **Children**

  * Minimal or no linear correlation to charges (correlation ≈ 0.07) ([GitHub][4]).

* **Sex**

  * Slight differences exist; median charges: females \~\$9.41k, males \~\$9.37k ([GitHub][4]).

* **Region**

  * Generally similar costs, though Southeast had the highest median/mean and Southwest the lowest, largely influenced by regional smoking rates ([GitHub][7], [a-s620.github.io][2]).

---

## 📊 Modeling & Feature Importance

* **Decision-tree & Random Forest**
  Studies ranked feature importance (continuous BMI):

  * **Smoker** \~62%, **BMI** \~21%, **Age** \~14%, children/region/sex <5% combined ([amlyfe.github.io][5], [actuaries.digital][8]).

* **Regression Performance**

  * Random forest yielded R² ≈ 0.78 and MAE ≈ \$2,833 — outperforming linear (R² ≈ 0.71, MAE ≈ \$4,163) and standalone decision-tree models ([amlyfe.github.io][5], [a-s620.github.io][2]).

---

## building

1. **Data prep**

   * Encode categorical variables (`sex`, `smoker`, `region`).
   * Optionally bin BMI into health categories.
   * Deal with outliers in `charges` (often by analyzing or capping). ([amlyfe.github.io][5], [GitHub][7])

2. **Exploratory Data Analysis**

   * Visualize distributions (boxplots, KDE) and relationships (scatter, violin, bar charts grouped by categorical variables). ([Codecademy Forums][1])

3. **Feature correlation & importance**

   * Calculate correlation matrix; run basic models (e.g., decision trees) to assess importance scores.

4. **Modeling pipeline**

   * Split into train/test sets
   * Train regression (linear, tree‑based) and classification (predicting `insuranceclaim`) models
   * Evaluate using RMSE, MAE, R² (regression), and accuracy/AUC (classification)
   * Random Forest
Consistently the top performer across insurance claim and fraud detection datasets, typically achieving 85–92% accuracy and high AUC values (~0.98) 
SCIRP
+15
Medium
+15
Reddit
+15
.

Known for high sensitivity (TP detection) and low false positives compared to simpler models 
Readkong
ResearchGate
.

Example: Random Forest achieved 86.77% accuracy and strong classification metrics in an auto‑insurance claim dataset 
Readkong
+1
IJISAE
+1
.

Decision Tree
More interpretable but often underperforms ensemble models.

Example: accuracy around 79–80%, sometimes comparable to logistic regression 
Scribd
+15
Medium
+15
Reddit
+15
Reddit
+8
IJRASET
+8
Scribd
+8
.

In some academic studies (e.g., heart disease prediction), a well-tuned single decision tree even outperformed Random Forest—though this is more exception than rule 
arXiv
.

Logistic Regression
Simple, fast, and interpretable, with decent baseline accuracy (often in 80–85% range) 
Medium
MedRxiv
.

However, less powerful than Random Forest on non-linear patterns; tends to sacrifice predictive power for simplicity 
MedRxiv
Reddit
.

Naive Bayes
Typically the least accurate; performs well only with strong conditional-independence assumptions.

Used mostly as a baseline model; often achieves around 60–80% accuracy depending on dataset

---

## 📈 Summary Table of Variable Impact

| Variable | Effect on Charges | Model Importance |
| :------: | :---------------: | :--------------: |
|  Smoker  |    Huge (+400%)   |  Highest (\~62%) |
|    BMI   |   Moderate–high   |       \~21%      |
|    Age   |  Steady increase  |       \~14%      |
| Children |     Negligible    |        <3%       |
|  Region  |   Minor variance  |        <2%       |
|    Sex   |  Minimal (\~±5%)  |        <2%       |

---

