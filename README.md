# layoffss
# 📉 Layoffs Data Analysis — SQL Case Study

## 📌 Project Overview

This project is a **SQL-based analysis of global company layoffs**, designed to explore patterns in workforce reductions across companies, industries, countries, company stages, and time periods.

The objective of this project was not simply to practice SQL syntax, but to approach the dataset from a **Data Analyst perspective** by turning business questions into measurable metrics, analyzing the results, and extracting meaningful insights.

The analysis follows a structured approach:

> **Business Question → Metric → SQL Analysis → Result → Insight**

---

# 🎯 Business Objective

Large-scale layoffs can reflect changes in company strategy, industry conditions, funding availability, market demand, or broader economic pressure.

This project aims to answer questions such as:

* How many employees were laid off in total?
* Which companies experienced the largest layoffs?
* Which industries were affected the most?
* Which countries recorded the highest number of layoffs?
* How did layoffs change over time?
* Which company stages experienced the greatest impact?
* Which companies had the highest percentage of their workforce laid off?
* Is there a relationship between company funding and layoffs?
* How do **absolute layoffs** differ from **relative workforce impact**?
* How complete and reliable is the dataset?

---

# 📊 Dataset

The dataset contains information about company layoffs and includes the following columns:

| Column                  | Description                                    |
| ----------------------- | ---------------------------------------------- |
| `company`               | Company name                                   |
| `location`              | Company location/city                          |
| `industry`              | Industry in which the company operates         |
| `total_laid_off`        | Total number of employees laid off             |
| `percentage_laid_off`   | Percentage of the company's workforce laid off |
| `date`                  | Date of the layoff event                       |
| `stage`                 | Company funding/business stage                 |
| `country`               | Country                                        |
| `funds_raised_millions` | Total funding raised, in millions              |

---

# 🔍 Data Exploration & Quality

Before performing the main analysis, the dataset was explored to understand:

* Number of companies
* Available industries
* Countries represented
* Company stages
* Date range
* Missing values
* Distribution of layoffs
* Availability of funding information

Missing-data analysis was particularly important because several analytical metrics depend on fields such as:

* `total_laid_off`
* `percentage_laid_off`
* `industry`
* `stage`
* `funds_raised_millions`

Understanding missing data helps prevent misleading conclusions.

---

# 📈 1. Overall Layoff Impact

## Business Question

> **How many employees were laid off in total across the dataset?**

### Metric

`SUM(total_laid_off)`

This provides the overall scale of layoffs represented in the dataset.

### Result

**Total employees laid off:** `[RESULT]`

### Insight

This establishes the baseline for the entire analysis and allows later comparisons across years, industries, countries, and companies.

---

# 🏢 2. Layoffs by Company

## Business Question

> **Which companies recorded the largest number of layoffs?**

The analysis ranked companies according to their total number of laid-off employees.

### Metric

```sql
SUM(total_laid_off)
```

### Analysis

Companies were grouped and ordered by total layoffs to identify organizations with the largest absolute workforce reductions.

### Key Result

The companies with the highest total layoffs included:

| Company     | Total Laid Off |
| ----------- | -------------: |
| `[Company]` |     `[Result]` |
| `[Company]` |     `[Result]` |
| `[Company]` |     `[Result]` |
| `[Company]` |     `[Result]` |
| `[Company]` |     `[Result]` |

📸 **Result:** See the corresponding screenshot in the repository.

---

# 📅 3. Layoffs Over Time

## Business Question

> **How did layoffs change from year to year?**

The `date` column was used to extract the year and analyze total layoffs over time.

### Metric

**Total layoffs by year**

### Analysis

```text
Layoffs
   ↓
Extract Year
   ↓
GROUP BY Year
   ↓
SUM(total_laid_off)
   ↓
Compare Years
```

### Result

|     Year | Total Laid Off |
| -------: | -------------: |
| `[Year]` |     `[Result]` |
| `[Year]` |     `[Result]` |
| `[Year]` |     `[Result]` |

### Insight

The yearly analysis shows how the scale of layoffs changed throughout the period covered by the dataset.

This provides a temporal view of workforce reductions and helps identify periods with particularly high layoff activity.

---

# 🏭 4. Layoffs by Industry

## Business Question

> **Which industries experienced the largest number of layoffs?**

Companies were grouped by `industry` and total layoffs were calculated.

### Metric

```sql
SUM(total_laid_off)
```

### Result

| Industry     | Total Laid Off |
| ------------ | -------------: |
| `[Industry]` |     `[Result]` |
| `[Industry]` |     `[Result]` |
| `[Industry]` |     `[Result]` |
| `[Industry]` |     `[Result]` |
| `[Industry]` |     `[Result]` |

### Insight

The analysis highlights which industries experienced the greatest absolute workforce reductions within the dataset.

However, total layoffs alone do not necessarily mean that an industry was proportionally more affected, because industries differ greatly in company and workforce size.

---

# 🌍 5. Layoffs by Country

## Business Question

> **Which countries recorded the highest number of layoffs?**

Companies were grouped by `country` and ranked according to total layoffs.

### Metric

**Total employees laid off by country**

### Result

| Country     | Total Laid Off |
| ----------- | -------------: |
| `[Country]` |     `[Result]` |
| `[Country]` |     `[Result]` |
| `[Country]` |     `[Result]` |
| `[Country]` |     `[Result]` |
| `[Country]` |     `[Result]` |

### Insight

This provides a geographic view of the layoffs represented in the dataset.

The results should be interpreted in the context of the dataset's company coverage and the concentration of large companies in certain countries.

---

# 🏗️ 6. Layoffs by Company Stage

## Business Question

> **Which company stages experienced the greatest number of layoffs?**

The analysis examined layoffs across different company stages.

Examples of stages represented in the dataset include:

* Seed
* Series A
* Series B
* Series C
* Series D
* Series E
* Series F
* IPO
* Private Equity
* Acquired

### Metric

**Total layoffs by company stage**

### Result

| Company Stage | Total Laid Off |
| ------------- | -------------: |
| `[Stage]`     |     `[Result]` |
| `[Stage]`     |     `[Result]` |
| `[Stage]`     |     `[Result]` |
| `[Stage]`     |     `[Result]` |

### Insight

Comparing stages provides another perspective on where layoffs occurred within the company lifecycle.

---

# 📊 7. Share of Total Layoffs by Company Stage

## Business Question

> **What percentage of all recorded layoffs came from each company stage?**

Instead of only looking at absolute numbers, the analysis calculated each stage's contribution to the total layoffs.

### Metric

```text
Stage Layoffs / Total Layoffs × 100
```

This analysis used aggregation together with a subquery to compare each stage against the overall total.

### Result

| Company Stage | Total Layoffs |  % of Total |
| ------------- | ------------: | ----------: |
| `[Stage]`     |    `[Result]` | `[Result]%` |
| `[Stage]`     |    `[Result]` | `[Result]%` |
| `[Stage]`     |    `[Result]` | `[Result]%` |

### Insight

This provides a more meaningful comparison between stages because it expresses each stage's contribution relative to the entire dataset.

---

# 💰 8. Funding vs. Layoffs

## Business Question

> **Does the amount of funding raised provide any useful context for layoffs?**

The dataset contains:

`funds_raised_millions`

This allows companies to be grouped into funding ranges and compared with their layoff activity.

### Analytical Approach

Funding levels can be categorized using `CASE WHEN`, for example:

```text
Funding
   ↓
CASE WHEN
   ↓
Funding Categories
   ↓
Compare Layoffs
```

The analysis explores whether companies with different funding levels show different patterns in workforce reductions.

### Important Limitation

This analysis does **not** establish that funding causes layoffs.

It only examines patterns within the available dataset.

Other factors such as:

* Company size
* Industry
* Market conditions
* Revenue
* Profitability
* Growth strategy
* Economic environment

may also influence layoffs.

---

# ⚖️ 9. Absolute Layoffs vs. Relative Workforce Impact

One of the most important analytical distinctions in this project is the difference between:

### Absolute Impact

```text
total_laid_off
```

and

### Relative Impact

```text
percentage_laid_off
```

These two metrics answer different questions.

---

## Absolute Impact

> **How many employees did the company lay off?**

A large company could lay off thousands of employees while only affecting a relatively small percentage of its workforce.

---

## Relative Impact

> **What percentage of the company's workforce was laid off?**

A smaller company could lay off fewer employees numerically but lose a very large percentage of its workforce.

### Example

```text
Company A
10,000 employees
2,000 layoffs
= 20%

Company B
100 employees
80 layoffs
= 80%
```

Company A has the larger **absolute** number of layoffs.

Company B has the larger **relative workforce impact**.

This distinction is essential when interpreting layoff data.

---

# 🏆 10. Companies with the Highest Layoff Percentage

## Business Question

> **Which companies experienced the largest percentage reduction in their workforce?**

The analysis used:

```sql
percentage_laid_off
```

to identify companies with the highest relative workforce impact.

### Result

| Company     | Layoff Percentage |
| ----------- | ----------------: |
| `[Company]` |       `[Result]%` |
| `[Company]` |       `[Result]%` |
| `[Company]` |       `[Result]%` |

### Insight

This analysis reveals companies where layoffs represented a particularly large proportion of their workforce.

This is fundamentally different from ranking companies by the total number of employees laid off.

---

# 🔢 11. Comparing Layoff Size and Layoff Percentage

The project also compared:

* `SUM(total_laid_off)`
* `AVG(percentage_laid_off)`

This distinction helps answer two different analytical questions:

### Question 1

> **Where were the largest numbers of employees laid off?**

Measured using:

`SUM(total_laid_off)`

### Question 2

> **Where was the average workforce impact proportionally larger?**

Measured using:

`AVG(percentage_laid_off)`

These metrics should not be treated as interchangeable.

A company or group can rank highly in absolute layoffs while having a lower relative workforce impact.

---

# 🏅 12. Ranking Companies Using Window Functions

To make the analysis more advanced, **Window Functions** were used to rank companies according to layoff metrics.

For example:

```sql
RANK() OVER (
    ORDER BY SUM(total_laid_off) DESC
)
```

This allows companies to be ranked without collapsing the analytical logic into a simple `LIMIT`.

### SQL Concepts Demonstrated

* `RANK()`
* `OVER()`
* Aggregation
* Ordering within a window
* Analytical ranking

This was one of the advanced SQL techniques used in the project.

---

# 🧹 13. Missing Data Analysis

## Business Question

> **How complete is the dataset?**

Missing values were investigated across important columns.

Particular attention was given to:

* `total_laid_off`
* `percentage_laid_off`
* `industry`
* `stage`
* `funds_raised_millions`

### Why this matters

Missing data can directly affect analytical results.

For example:

* Missing `total_laid_off` affects total layoff calculations.
* Missing `percentage_laid_off` affects relative-impact analysis.
* Missing `funds_raised_millions` limits funding analysis.
* Missing `industry` or `stage` affects segmentation.

Therefore, data quality was treated as part of the analysis rather than ignored.

---

# 🧠 Key Analytical Insights

The project demonstrates several important analytical ideas.

## 1. Total layoffs and percentage layoffs tell different stories

A company can have a very high number of layoffs without eliminating most of its workforce.

At the same time, a smaller company can lose a very large percentage of its employees while having a much smaller absolute number of layoffs.

---

## 2. Time is an important dimension

Analyzing layoffs by year makes it possible to identify periods of higher and lower layoff activity.

---

## 3. Industry and geography matter

Layoffs are not evenly distributed across industries or countries.

Grouping the data by these dimensions reveals where the largest concentrations of layoffs occurred within the dataset.

---

## 4. Company stage provides additional context

The number of layoffs can vary significantly across different stages of company development.

---

## 5. Data quality affects business conclusions

Missing values are not simply a technical problem.

They can directly affect the accuracy and interpretation of analytical results.

---

# 🛠️ SQL Skills Demonstrated

This project applies a broad range of SQL concepts.

### Data Exploration

* `SELECT`
* `DISTINCT`
* `WHERE`
* `IS NULL`
* `IS NOT NULL`

### Aggregation

* `COUNT()`
* `COUNT(DISTINCT)`
* `SUM()`
* `AVG()`
* `MAX()`

### Grouping & Filtering

* `GROUP BY`
* `HAVING`
* `ORDER BY`
* `LIMIT`

### Date Analysis

* `YEAR()`
* Date-based grouping

### Conditional Logic

* `CASE WHEN`

### Advanced SQL

* Subqueries
* Common Table Expressions (CTEs)
* Window Functions
* `RANK()`

### Analytical Techniques

* Percentage calculations
* Conditional aggregation
* Absolute vs. relative metrics
* Ranking
* Data-quality analysis
* Metric comparison

---

# 📂 Project Structure

```text
layoffs-sql-analysis/
│
├── README.md
│
├── sql/
│   └── layoffs_analysis.sql
│
└── screenshots/
    ├── layoffs_by_company.png
    ├── layoffs_by_year.png
    ├── layoffs_by_industry.png
    ├── layoffs_by_country.png
    ├── layoffs_by_stage.png
    ├── funding_analysis.png
    └── ranking_analysis.png
```

---

# 🧰 Tools

* **MySQL**
* **SQL**
* **GitHub**
* **Layoffs Dataset**

---

# 🎓 What I Learned

This project helped me move beyond writing SQL queries and start thinking more like a **Data Analyst**.

The main learning outcomes were:

* Translating business questions into SQL metrics
* Working with real-world imperfect data
* Understanding data quality and missing values
* Using aggregation to identify patterns
* Comparing absolute and relative metrics
* Analyzing trends over time
* Segmenting data by industry, country, and company stage
* Using subqueries and CTEs for multi-step analysis
* Applying window functions for analytical ranking
* Interpreting SQL results from a business perspective

---

# 🚀 Future Improvements

This SQL case study can be extended in future versions by adding:

* Power BI visualizations
* Interactive dashboards
* More detailed time-series analysis
* Industry-level trend analysis
* Geographic analysis
* Company-level deep dives
* Funding and company-size analysis
* Python-based exploratory data analysis

---

# 📌 Final Takeaway

The main lesson from this project is that effective data analysis is not about writing the most complicated SQL query.

It is about understanding:

> **What question are we trying to answer?**

Then:

> **What metric actually answers that question?**

And finally:

> **What does the result mean from a business perspective?**

This project represents an early step in my journey toward becoming a **Data Analyst**, combining SQL technical skills with business-oriented analytical thinking.

