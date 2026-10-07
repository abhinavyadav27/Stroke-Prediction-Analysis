# 🧠 Stroke Prediction Analysis – Sprint-Wise Data Analytics Project

An end-to-end, sprint-based data analytics project on patient healthcare records. It covers **data cleaning and validation**, **exploratory and statistical analysis**, **hypothesis testing**, and **feature engineering** to understand which patient characteristics are associated with stroke.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Sprint Breakdown](#-sprint-breakdown)
- [Key Findings](#-key-findings)
- [Engineered Features](#-engineered-features)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Future Scope](#-future-scope)
- [Author](#-author)

---

## 📖 Project Overview

Stroke is a serious medical condition, and early identification of risk patterns can support better screening and monitoring. This project analyses a patient-level stroke dataset across three structured sprints, moving from raw data to statistically supported insights:

| Sprint | Focus | Outcome |
|---|---|---|
| **Sprint 1** | Data understanding, cleaning, outlier analysis & validation | Clean, validated dataset |
| **Sprint 2** | Descriptive, univariate, bivariate & multivariate analysis | Visual and business insights |
| **Sprint 3** | Hypothesis testing, confidence intervals & feature engineering | Statistical evidence + 6 new features |

## 📊 Dataset

- **File:** `healthcare-dataset-stroke-data.csv`
- **Size:** 5,110 patient records × 12 columns
- **Target variable:** `stroke` (1 = stroke, 0 = no stroke)
- **Class imbalance:** 4,861 non-stroke (95.13%) vs. 249 stroke (4.87%)

| Feature | Type | Description |
|---|---|---|
| `id` | Integer | Patient record identifier |
| `gender` | Categorical | Recorded gender category |
| `age` | Numeric | Patient age |
| `hypertension` | Binary | Presence of hypertension |
| `heart_disease` | Binary | Presence of heart disease |
| `ever_married` | Categorical | Marital status |
| `work_type` | Categorical | Type of employment |
| `Residence_type` | Categorical | Urban or rural residence |
| `avg_glucose_level` | Numeric | Average glucose level |
| `bmi` | Numeric | Body mass index |
| `smoking_status` | Categorical | Smoking history/status |
| `stroke` | Binary (target) | Recorded stroke outcome |

## 🛠 Tech Stack

- **Language:** Python 3
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, SciPy
- **Environment:** Jupyter Notebook / Google Colab

## 🏃 Sprint Breakdown

### Sprint 1 – Data Understanding, Cleaning & Validation
- Profiled the dataset structure, data types, and descriptive statistics
- Found **201 missing BMI values (3.93%)** and filled them with the **median** (robust to extreme values)
- Confirmed **0 duplicate rows** and no invalid values in binary columns
- Detected outliers using the **IQR method**: **627** in average glucose and **126** in BMI
- Retained the outliers rather than deleting them, since extreme clinical values can be genuine patients
- Ran a final validation check and exported audit reports

### Sprint 2 – Descriptive, Univariate, Bivariate & Multivariate Analysis
- Calculated mean, median, mode, and standard deviation for key variables
- Plotted histograms, box plots, and count plots to study distributions
- Compared stroke rates across gender, work type, smoking status, and health conditions
- Built **pivot tables and crosstabs** and analysed correlations
- Used stroke *rates* (percentages) instead of raw counts because of the class imbalance

### Sprint 3 – Statistical Analysis, Hypothesis Testing & Feature Engineering
- Computed skewness, covariance, and correlation with the target
- Performed an **independent t-test**, **chi-square test**, and **one-way ANOVA**
- Calculated **95% confidence intervals** for key means
- Engineered 6 new features, growing the dataset from **12 to 18 columns**

## 🔍 Key Findings

**Descriptive & group comparison**

| Metric | Non-stroke | Stroke |
|---|---|---|
| Average age | 41.97 | 67.73 |
| Average glucose | 104.80 | 132.54 |
| Average BMI | 28.80 | 30.09 |

**Correlation with stroke:** Age (0.245) > Heart disease (0.135) > Glucose (0.132) > Hypertension (0.128) > BMI (0.036)

**Hypothesis tests (α = 0.05)**

| Test | Question | Result | Decision |
|---|---|---|---|
| Independent t-test | Does mean age differ between stroke / non-stroke? | t = 29.69, p ≈ 2.12 × 10⁻⁹⁵ | Reject H₀ |
| Chi-square | Is hypertension associated with stroke? | χ² = 81.61, p ≈ 1.66 × 10⁻¹⁹ | Reject H₀ |
| ANOVA | Does mean age differ across work types? | F = 1110.09, p ≈ 0 | Reject H₀ |

**95% Confidence Intervals**

| Variable | Mean | 95% CI |
|---|---|---|
| Age | 43.23 | 42.61 – 43.85 |
| Avg. glucose | 106.15 | 104.91 – 107.39 |
| BMI | 28.86 | 28.65 – 29.07 |

**Stroke rate by engineered group**

| Feature | Group | Stroke rate |
|---|---|---|
| Age Group | Young → Adult → Middle_Age → Senior | 0.23% → 0.46% → 3.84% → **13.15%** |
| Disease Status | No Disease → One Condition → Both Conditions | 3.39% → 13.47% → **20.31%** |
| Glucose Category | Very_High | 10.19% |
| BMI Category | Underweight / Normal / Overweight / Obese | 0.29% / 2.94% / **7.14%** / 5.07% |

### 💡 Business Insights
- Older patients show noticeably higher stroke rates.
- Patients with **both hypertension and heart disease** have the highest observed stroke rate.
- Very high glucose levels are associated with higher stroke rates.
- The BMI pattern is mixed (overweight highest, obese lower), showing that engineered features should be evaluated rather than assumed useful.

## 🧩 Engineered Features

| Feature | Purpose |
|---|---|
| Age Group | Young / Adult / Middle_Age / Senior bands |
| BMI Category | Underweight / Normal / Overweight / Obese |
| Glucose Category | Low / Normal / High / Very_High |
| Combined Disease Indicator | Joint presence of hypertension and heart disease |
| Disease Status | No Disease / One Condition / Both Conditions |
| Health Score | Simple 0–2 count of disease indicators |

## 📁 Project Structure

```
├── Sprint_1_based_Ap.ipynb                 # Cleaning, outliers, validation
├── Sprint_2_based_Ap.ipynb                 # EDA: univariate, bivariate, multivariate
├── Sprint_3_based_Ap.ipynb                 # Hypothesis testing & feature engineering
├── Sprint_1_Documentation_Abhinav_Yadav final word.docx
├── Sprint_2_Documentation_Abhinav_Yadav final word.docx
├── Sprint_3_Documentation_Abhinav_Yadav final word.docx
├── healthcare-dataset-stroke-data.csv      # Raw dataset (add to repo)
└── README.md
```

**Generated outputs (by the notebooks):**
- Sprint 1: `stroke_data_cleaned_sprint1.csv`, `missing_value_report.csv`, `duplicate_analysis_report.csv`, `outlier_analysis_report.csv`, `data_validation_summary.csv`
- Sprint 2: pivot tables and crosstabs (gender, work type, smoking), `group_based_analysis.csv`, `stroke_data_sprint2_final.csv`
- Sprint 3: `stroke_data_sprint3_feature_engineered.csv`, `stroke_data_sprint3_final.csv` (5,110 × 18)

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```

3. **Add the dataset** `healthcare-dataset-stroke-data.csv` to the project folder.

4. **Run the notebooks in order** (Sprint 1 → 2 → 3), since each sprint uses the cleaned output of the previous one:
   ```bash
   jupyter notebook
   ```
   > The notebooks were written in Google Colab and read files from `/content/`. Update those paths (e.g. `pd.read_csv("healthcare-dataset-stroke-data.csv")`) when running locally. Sprint 2 and 3 also import `google.colab.files`, which is only needed for downloads in Colab.

## 🚀 Future Scope

- Build a **predictive model** (Logistic Regression, Random Forest, XGBoost) using class-imbalance techniques such as SMOTE or class weights
- Evaluate with **precision, recall, F1, and ROC-AUC** rather than accuracy alone
- Create an interactive **Power BI / Streamlit dashboard** for stakeholders
- Explore interaction effects between age, glucose, and health conditions

## 👤 Author

**Abhinav Yadav**
Aspiring Data Analyst | Hyderabad, India


---

⭐ If you found this project useful, consider giving it a star!
