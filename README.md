# 🐍 Exploratory Data Analysis in Python — DataCamp

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)
![DataCamp](https://img.shields.io/badge/DataCamp-Course-03EF62?style=for-the-badge&logo=datacamp&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> **Course:** [Exploratory Data Analysis in Python](https://app.datacamp.com/learn/courses/exploratory-data-analysis-in-python) — DataCamp  
> **Instructor:** George Boorman | **Duration:** 4 Hours | **Level:** Intermediate  
> **Libraries:** pandas, seaborn, matplotlib, numpy

---

## 📖 About This Course

This course covers the full EDA workflow — from first look at a raw dataset all the way to generating hypotheses and feeding findings into a data science pipeline. Across 4 real-world projects, I practiced validating and summarising data, handling missing values, cleaning data types, engineering new features, and creating Seaborn visualisations to communicate insights clearly.

---

## 📁 Projects Overview

| # | Project | Dataset | Focus |
|---|---|---|---|
| 1 | 💍 Divorce Analysis | `divorce.csv` | Relationships between marriage, kids & income |
| 2 | ✈️ Plane Ticket Prices | `planes.csv` | Data cleaning, outlier removal & feature engineering |
| 3 | 💼 Data Science Salaries | `ds_salaries_clean.csv` | Salary distribution by role, company size & location |
| 4 | 📉 Global Unemployment | `clean_unemployment.csv` | Unemployment trends by continent (2019–2021) |

---

## 💍 Project 1 — Divorce Analysis

**File:** `portfolio_divorce.py`  
**Dataset:** `divorce.csv`

Explored a dataset of married and divorced couples, analysing the relationships between marriage duration, number of children, income, and education level.

### What I did:
- Parsed date columns (`divorce_date`, `dob_man`, `dob_woman`, `marriage_date`) on import using `parse_dates`
- Engineered a new `marriage_year` feature from `marriage_date`
- Built a **line plot** of average number of kids by marriage year
- Built a **scatterplot** of marriage duration vs number of kids
- Created a **pairplot** to explore relationships between `income_woman` and `marriage_duration`
- Visualised how `woman_age_marriage` relates to `income_woman`, coloured by education level
- Built **KDE plots** of marriage duration grouped by number of kids — with boundary clamping (`cut=0`) and a **cumulative distribution function** variant

### Visualisations:
| Chart | Purpose |
|---|---|
| Line plot | Avg kids by marriage year |
| Scatterplot | Marriage duration vs kids |
| Pairplot | Income vs marriage duration |
| Scatterplot (hue) | Age at marriage vs income by education |
| KDE plot (3 variants) | Duration distribution by number of kids |

> 📸 *Add screenshot here:* `![Divorce Analysis](screenshots/divorce.png)`

---

## ✈️ Project 2 — Plane Ticket Prices

**File:** `portfolio_planes.py`  
**Dataset:** `planes.csv`

Cleaned a messy airline pricing dataset, handling missing values, engineering categorical and numerical features, and removing outliers before analysis.

### What I did:
- Audited missing values with `isna().sum()` across all columns
- Applied a **5% threshold rule** — dropped rows only for columns with few nulls
- Imputed missing `Price` values using **median price per airline** (via `groupby` + `map`)
- Categorised flight duration into `Short-haul`, `Medium`, `Long-haul`, and `Extreme duration` using `np.select` with regex conditions
- Cleaned the `Duration` column by stripping the `"h"` string and converting to `float`
- Engineered **3 group-level features** using `groupby` + `transform`:
  - `airline_price_st_dev` — price volatility per airline
  - `airline_median_duration` — typical flight length per airline
  - `price_destination_mean` — average price per destination
- Removed outliers using the **IQR method** (1.5× IQR above/below Q1/Q3)

### Visualisations:
| Chart | Purpose |
|---|---|
| Box plot | Price distribution per airline |
| Count plot | Flights per duration category |
| Histogram | Distribution of flight duration |
| Histogram | Distribution of ticket prices (pre & post outlier removal) |

> 📸 *Add screenshot here:* `![Planes Analysis](screenshots/planes.png)`

---

## 💼 Project 3 — Data Science Salaries

**File:** `portfolio_salaries.py`  
**Dataset:** `ds_salaries_clean.csv`

Analysed data science salary data across job categories, company sizes, experience levels, and locations.

### What I did:
- Explored job category distribution using **relative frequency** (`value_counts(normalize=True)`)
- Used `pd.crosstab` to cross-tabulate `Company_Size` vs `Experience`, and `Job_Category` vs `Company_Size` with mean salary as values
- Extracted `month` and `weekday` from `date_of_response` for time-based analysis
- Built a **correlation heatmap** across all numeric features
- Used `pd.cut` with IQR-based bins to create a `salary_level` column (`entry`, `mid`, `senior`, `exec`)
- Compared US vs GB salaries with a **bar plot**
- Visualised salary by company size and employment status with a grouped **bar plot**

### Visualisations:
| Chart | Purpose |
|---|---|
| Heatmap | Correlation between numeric features |
| Count plot | Salary levels by company size |
| Bar plot | Average salary — US vs GB |
| Bar plot (grouped) | Salary by company size & employment status |

> 📸 *Add screenshot here:* `![Salaries Analysis](screenshots/salaries.png)`

---

## 📉 Project 4 — Global Unemployment

**File:** `portfolio_unemployment.py`  
**Dataset:** `clean_unemployment.csv`

Explored global unemployment rates across continents from 2019 to 2021, with a focus on summary statistics and distribution analysis.

### What I did:
- Previewed the dataset and counted records per continent with `value_counts`
- Fixed data type — converted `2019` column from object to `float`
- Computed min, max, mean, and standard deviation of unemployment rates for 2019–2021
- Used `groupby().agg()` to build a continent-level summary with mean & std for 2021
- Built a **histogram** of 2021 unemployment rates (1% bin width)
- Built a **box plot** of 2021 rates broken down by continent
- Built a **bar plot** of average unemployment by continent

### Visualisations:
| Chart | Purpose |
|---|---|
| Histogram | Distribution of 2021 unemployment rates |
| Box plot | 2021 rates by continent |
| Bar plot | Average unemployment per continent |

> 📸 *Add screenshot here:* `![Unemployment Analysis](screenshots/unemployment.png)`

---

## 🧠 Skills Demonstrated

| Skill | Used In |
|---|---|
| `parse_dates`, `dt.year`, `dt.month`, `dt.weekday` | Divorce, Salaries |
| Feature engineering | Divorce (marriage_year), Planes (duration category, group stats) |
| Missing value handling (`isna`, `fillna`, `dropna`) | Planes |
| Median imputation with `groupby` + `map` | Planes |
| `np.select` with regex conditions | Planes (flight categories) |
| IQR outlier removal | Planes, Salaries |
| `pd.cut` for binning | Salaries (salary levels) |
| `pd.crosstab` | Salaries |
| `groupby().agg()` | Unemployment, Salaries |
| `groupby().transform()` | Planes (group-level features) |
| Seaborn: line, scatter, KDE, pairplot, heatmap, boxplot, countplot, histplot, barplot | All projects |

---

## 📁 Repository Structure

```
📦 eda-python-datacamp
 ┣ 📂 screenshots/                  # Chart screenshots
 ┣ 📄 portfolio_divorce.py
 ┣ 📄 portfolio_planes.py
 ┣ 📄 portfolio_salaries.py
 ┣ 📄 portfolio_unemployment.py
 ┗ 📄 README.md
```

---

## 🏆 Certificate

> 📜 *Add your DataCamp Statement of Accomplishment link here*  
> [View Certificate](https://your-certificate-link-here)

---

## 📬 Connect With Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://linkedin.com/in/your-profile)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/your-username)
