# 🎓 Student Performance Prediction & Analysis

Predicting and analyzing student academic performance using Exploratory Data Analysis (EDA) and Machine Learning (Linear Regression & Random Forest).

---

## 📌 Project Overview
This project analyzes a dataset containing student demographics, social details, school attributes, and past grades to understand the key factors influencing academic success and build predictive models for final student grades (`G3`).

It is structured into two main Jupyter Notebooks:
1. **[student-performance-dataset.ipynb](file:///Users/admin/Desktop/ml model/student performance/student-performance-dataset.ipynb)**: Dedicated to data cleaning, duplicate handling, absences data aggregation, and univariate analysis (pie charts, bar plots).
2. **[Untitled.ipynb](file:///Users/admin/Desktop/ml model/student performance/Untitled.ipynb)**: Focused on feature preprocessing (Label Encoding), correlation heatmap analysis, regression model training, feature importance extraction, and model evaluation.

---

## 📊 Dataset Description
The dataset contains **395 rows** and **33 columns**, tracking various factors from student demographics to academic habits.

### Data Dictionary

| Column Name | Type | Description |
| :--- | :--- | :--- |
| `school` | Binary | Student's school (`GP` - Gabriel Pereira, `MS` - Mousinho da Silveira) |
| `sex` | Binary | Student's sex (`F` - female, `M` - male) |
| `age` | Numeric | Student's age (15 to 22) |
| `address` | Binary | Home address type (`U` - urban, `R` - rural) |
| `famsize` | Binary | Family size (`LE3` - less/equal to 3, `GT3` - greater than 3) |
| `Pstatus` | Binary | Parent's cohabitation status (`T` - living together, `A` - apart) |
| `Medu` | Numeric | Mother's education (0 - none, 1 - primary, 2 - 5th-9th grade, 3 - secondary, 4 - higher education) |
| `Fedu` | Numeric | Father's education (0 - none, 1 - primary, 2 - 5th-9th grade, 3 - secondary, 4 - higher education) |
| `Mjob` | Nominal | Mother's job (`teacher`, `health` care, civil `services`, `at_home`, or `other`) |
| `Fjob` | Nominal | Father's job (`teacher`, `health` care, civil `services`, `at_home`, or `other`) |
| `reason` | Nominal | Reason to choose this school (close to `home`, `reputation`, `course` preference, or `other`) |
| `guardian` | Nominal | Student's guardian (`mother`, `father`, or `other`) |
| `traveltime` | Numeric | Home to school travel time (1: <15 min, 2: 15-30 min, 3: 30-60 min, 4: >60 min) |
| `studytime` | Numeric | Weekly study time (1: <2 hrs, 2: 2-5 hrs, 3: 5-10 hrs, 4: >10 hrs) |
| `failures` | Numeric | Number of past class failures (n if 1 <= n < 3, else 4) |
| `schoolsup` | Binary | Extra educational support (yes or no) |
| `famsup` | Binary | Family educational support (yes or no) |
| `paid` | Binary | Extra paid classes within the course subject (yes or no) |
| `activities`| Binary | Extra-curricular activities (yes or no) |
| `nursery` | Binary | Attended nursery school (yes or no) |
| `higher` | Binary | Wants to take higher education (yes or no) |
| `internet` | Binary | Internet access at home (yes or no) |
| `romantic` | Binary | In a romantic relationship (yes or no) |
| `famrel` | Numeric | Quality of family relationships (from 1 - very bad to 5 - excellent) |
| `freetime` | Numeric | Free time after school (from 1 - very low to 5 - very high) |
| `goout` | Numeric | Going out with friends (from 1 - very low to 5 - very high) |
| `Dalc` | Numeric | Workday alcohol consumption (from 1 - very low to 5 - very high) |
| `Walc` | Numeric | Weekend alcohol consumption (from 1 - very low to 5 - very high) |
| `health` | Numeric | Current health status (from 1 - very bad to 5 - very good) |
| `absences` | Numeric | Number of school absences (0 to 75) |
| `G1` | Numeric | First period grade (0 to 20) |
| `G2` | Numeric | Second period grade (0 to 20) |
| `G3` | Numeric | **Final grade** (0 to 20, Target Variable) |

---

## 📈 Exploratory Data Analysis (EDA) Highlights
Some of the core visual distributions explored:
* **Mjob/Fjob Distribution**: Insights into parent professions, showing a high concentration of parents employed in `other` and civil `services`, while healthcare and teaching occupations are less common.
* **School Representation**: Significant imbalance with Gabriel Pereira (`GP`) constituting the vast majority of student entries compared to Mousinho da Silveira (`MS`).
* **Absences Analysis**: Identified categories of absences, showing most students have low levels of absences (under 10), with a few outliers having highly frequent absences (up to 75).
* **Final Grades (`G3`) Distribution**: Displays a semi-normal distribution centered around 10-11, with a noticeable spike at 0 (representing students who failed or did not take the final exam).

---

## 🤖 Machine Learning Modeling & Results
The modeling pipeline consists of:
1. **Preprocessing**: Converting categorical variables using Scikit-Learn's `LabelEncoder`.
2. **Train-Test Split**: Splitting features (`X`) and target final grade (`y = G3`) into training and testing sets.
3. **Model Selection**: Implementing Linear Regression and Random Forest Regressor.

### Evaluation Metrics Comparison

| Model | $R^2$ Score | Mean Absolute Error (MAE) |
| :--- | :---: | :---: |
| **Linear Regression** | `0.7546` | `1.4955` |
| **Random Forest Regressor** | **`0.8300`** | **`1.1051`** |

*Random Forest Regressor achieved superior performance, explaining approximately 83% of the variance in final grades with an average error of only ~1.1 points on a 20-point scale.*

### 🔑 Key Feature Importances (Random Forest)
The Random Forest model identified the top factors driving student grades:

1. **`G2` (Second Period Grade)**: **79.25%** (By far the strongest predictor)
2. **`absences` (School Absences)**: **11.03%**
3. **`age` (Student Age)**: **1.52%**
4. **`reason` (Reason for choosing school)**: **1.03%**
5. **`G1` (First Period Grade)**: **0.76%**
6. **`famrel` (Family relationship quality)**: **0.64%**
7. **`Mjob` (Mother's job)**: **0.61%**
8. **`romantic` (Romantic relationship status)**: **0.57%**

*This indicates that short-term previous academic performance (`G2`) combined with student attendance (`absences`) dominate the predictive signal for final success.*

---

## 🚀 How to Run the Project
1. **Clone the repository**:
   ```bash
   git clone <repository_url>
   cd "student performance"
   ```
2. **Install requirements**:
   Ensure you have python installed along with key libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
3. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```
4. Open and run:
   * `student-performance-dataset.ipynb` for EDA.
   * `Untitled.ipynb` for ML modeling.
