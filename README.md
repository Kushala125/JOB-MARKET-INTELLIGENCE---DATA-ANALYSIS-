# Job Market Intelligence & Hiring Trend Analysis

## Overview

This project delivers a complete end-to-end **Job Market Intelligence Analysis** using **Python, SQL, Excel, and Data Visualization techniques** to uncover hiring trends, skill demand, workforce behavior, and company hiring strategies from real-world job posting data.

The analysis focuses on:

* Hiring trends over time
* Skill demand intelligence
* Senior vs Junior hiring ratios
* Remote vs Hybrid vs Onsite trends
* Hiring volatility and stability
* Company market share analysis
* Skill co-occurrence relationships
* Workforce demand forecasting insights

The project demonstrates strong capabilities in:

* Data Cleaning
* Feature Engineering
* Exploratory Data Analysis (EDA)
* Advanced SQL Analytics
* Python Automation
* Business Intelligence Storytelling
* Data Visualization

---

# Project Architecture

```text
JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-
│
├── excel/
│   └── Dashboard Excel Files
│
├── images/
│   ├── chart1.png
│   ├── chart2.png
│   ├── chart3.png
│   ├── chart4.png
│   ├── chart5.png
│   └── chart6.png
│
├── notebook/
│   └── job analysis.ipynb
│
├── sql/
│   └── Advanced SQL Queries.sql
│
├── README.md
└── Project Report.pdf
```

---

# Business Problem

Modern hiring markets are rapidly evolving.

Companies are shifting toward:

* Skill-first hiring
* Remote work strategies
* Senior-level talent acquisition
* Cloud and AI-focused technical hiring

The challenge is understanding:

* Which skills dominate the market?
* Which companies are aggressively hiring?
* Is the market friendly to junior candidates?
* Which industries prefer remote work?
* Which companies hire consistently versus unpredictably?

This project answers those questions using real-world job posting data.

---

# Dataset Information

### Dataset Size

* Total Records: **6,025 Job Postings**
* Features: **11 Columns**
* Source: LinkedIn-style job posting dataset

### Main Columns

| Column       | Description          |
| ------------ | -------------------- |
| job_title    | Role title           |
| company      | Hiring company       |
| job_location | Job location         |
| first_seen   | Job posting date     |
| job_level    | Seniority level      |
| job_type     | Remote/Hybrid/Onsite |
| job_skills   | Required skills      |
| job_summary  | Job description      |

---

# Technologies Used

| Technology       | Purpose                 |
| ---------------- | ----------------------- |
| Python           | Data cleaning and EDA   |
| Pandas           | Data manipulation       |
| NumPy            | Numerical operations    |
| SQL              | Advanced analytics      |
| SQLite           | Query execution         |
| Matplotlib       | Data visualization      |
| Excel            | Dashboard reporting     |
| Jupyter Notebook | Development environment |
| GitHub           | Version control         |

---

# Python Data Engineering Workflow

## 1. Data Cleaning

### Cleaning Job Levels

```python

def clean_job_level(level):
    if pd.isna(level):
        return 'Unknown'

    level = level.lower()

    if 'junior' in level or 'entry' in level:
        return 'Junior'

    elif 'senior' in level or 'staff' in level or 'lead' in level:
        return 'Senior'

    return 'Mid'

```

### Skill Standardization

```python

def normalize_skill(skill):
    skill = skill.strip().upper()

    if 'SQL' in skill:
        return 'SQL'

    if 'PYTHON' in skill:
        return 'PYTHON'

    if 'POWER BI' in skill:
        return 'POWER BI'

    return skill

```

---

# Advanced SQL Analytics

## Senior vs Junior Hiring Ratio

```sql
WITH job_levels AS (
    SELECT
        substr(first_seen, 1, 7) AS year_month,

        CASE
            WHEN lower("job level") LIKE '%junior%'
              OR lower("job level") LIKE '%entry%'
            THEN 'Junior'

            WHEN lower("job level") LIKE '%senior%'
              OR lower("job level") LIKE '%lead%'
              OR lower("job level") LIKE '%staff%'
            THEN 'Senior'

            ELSE 'Mid'
        END AS job_level

    FROM postings
)

SELECT
    year_month,

    SUM(CASE WHEN job_level = 'Senior' THEN 1 ELSE 0 END)
    AS senior_jobs,

    SUM(CASE WHEN job_level = 'Junior' THEN 1 ELSE 0 END)
    AS junior_jobs,

    ROUND(
        1.0 * SUM(CASE WHEN job_level = 'Senior' THEN 1 ELSE 0 END)
        /
        NULLIF(SUM(CASE WHEN job_level = 'Junior' THEN 1 ELSE 0 END), 0),
        2
    ) AS senior_to_junior_ratio

FROM job_levels
GROUP BY year_month
ORDER BY year_month;
```

---

## Hiring Stability Score

```sql
WITH monthly_jobs AS (

    SELECT
        company,
        substr(first_seen, 1, 7) AS year_month,
        COUNT(*) AS jobs

    FROM postings
    GROUP BY company, year_month
),

stats AS (

    SELECT
        company,
        AVG(jobs) AS avg_jobs,
        AVG(jobs * jobs) AS avg_jobs_sq

    FROM monthly_jobs
    GROUP BY company
)

SELECT
    company,

    ROUND(avg_jobs, 2) AS avg_monthly_jobs,

    ROUND(
        sqrt(avg_jobs_sq - avg_jobs * avg_jobs),
        2
    ) AS hiring_volatility,

    ROUND(
        avg_jobs /
        NULLIF(sqrt(avg_jobs_sq - avg_jobs * avg_jobs), 0),
        2
    ) AS stability_score

FROM stats
ORDER BY stability_score DESC;
```

---

# Key Insights

## Hiring Market Trends

* The market strongly favors **Mid-level and Senior-level professionals**.
* Junior hiring remains relatively limited.
* Technology and Data Engineering roles dominate hiring activity.
* Remote work adoption continues to grow.
* Hybrid work models remain highly popular.

---

## Top In-Demand Skills

| Rank | Skill              |
| ---- | ------------------ |
| 1    | SQL                |
| 2    | Python             |
| 3    | Azure              |
| 4    | AWS                |
| 5    | Data Engineering   |
| 6    | ETL                |
| 7    | Power BI           |
| 8    | Data Modeling      |
| 9    | Tableau            |
| 10   | Data Visualization |

---

# Skill Intelligence Analysis

The project discovered a strong **long-tail skill distribution**:

* Core skills dominate the majority of postings.
* Specialized cloud and orchestration skills appear primarily in senior roles.
* Python and SQL form the foundational technical stack for most data-focused careers.

### Most Common Skill Pairings

| Skill Pair     | Co-Occurrence |
| -------------- | ------------- |
| Python + SQL   | Highest       |
| AWS + SQL      | Very High     |
| Azure + SQL    | High          |
| Power BI + SQL | High          |
| SQL + Tableau  | High          |

---

# Remote Work Intelligence

### Work Mode Distribution

| Work Mode | Share |
| --------- | ----- |
| Onsite    | 46.4% |
| Hybrid    | 33.9% |
| Remote    | 19.6% |

### Insight

Companies are increasingly supporting flexible work arrangements, but onsite and hybrid roles still dominate overall hiring.

---

# Business Intelligence Storytelling

## The Skill-First Economy

The modern hiring market is no longer driven solely by job titles.

Instead, organizations evaluate candidates based on:

* Technical skill combinations
* Cloud ecosystem experience
* Data engineering capabilities
* AI and automation readiness

### Two Market Layers

## 1. Utility Skills Layer

These are baseline skills expected in nearly all roles:

* SQL
* Python
* Excel
* Data Visualization

These skills are no longer differentiators.

They are minimum entry requirements.

---

## 2. Strategic Skills Layer

These advanced skills appear primarily in senior and leadership roles:

* Snowflake
* Airflow
* Kubernetes
* Cloud Architecture
* Machine Learning Infrastructure

These skills differentiate high-value professionals.

---

# JavaScript Dashboard & Visualization Code

The project can also be extended into a modern JavaScript analytics dashboard using Chart.js.

## Example: Hiring Trend Line Chart (JavaScript)

```html
<canvas id="hiringTrend"></canvas>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>
const ctx = document.getElementById('hiringTrend');

new Chart(ctx, {
    type: 'line',
    data: {
        labels: ['2023-08', '2023-09', '2023-10', '2023-11', '2023-12'],
        datasets: [{
            label: 'Jobs Posted',
            data: [420, 510, 630, 720, 865],
            borderWidth: 3
        }]
    },
    options: {
        responsive: true,
        plugins: {
            title: {
                display: true,
                text: 'Hiring Trend Over Time'
            }
        }
    }
});
</script>
```

---

## Example: Remote vs Hybrid vs Onsite Chart

```html
<canvas id="workModeChart"></canvas>

<script>
const workCtx = document.getElementById('workModeChart');

new Chart(workCtx, {
    type: 'bar',
    data: {
        labels: ['Onsite', 'Hybrid', 'Remote'],
        datasets: [{
            label: 'Job Count',
            data: [2628, 1920, 1110],
            borderWidth: 2
        }]
    },
    options: {
        responsive: true
    }
});
</script>
```

---

## Example: Skill Demand Pie Chart

```html
<canvas id="skillsChart"></canvas>

<script>
const skillCtx = document.getElementById('skillsChart');

new Chart(skillCtx, {
    type: 'pie',
    data: {
        labels: ['SQL', 'Python', 'Azure', 'AWS', 'Power BI'],
        datasets: [{
            data: [4894, 2759, 2177, 1814, 961]
        }]
    }
});
</script>
```

---

# Project Images & Dashboard Screenshots

## Hiring Momentum Heatmap

![Hiring Momentum](images/chart1.png)

---

## Skill Dominance Curve

![Skill Dominance](images/chart2.png)

---

## Remote vs Hybrid vs Onsite Trend

![Remote Work Trend](images/chart3.png)

---

## Hiring Concentration Analysis

![Hiring Concentration](images/chart4.png)

---

## Skill Demand by Seniority

![Skill Demand](images/chart 5.png)

---

## Business Intelligence Dashboard

![Dashboard](images/chart6.png)

---

# Visualizations Included

The project includes multiple professional visualizations:

* Hiring Trend Over Time
* Skill Dominance Curve
* Remote vs Hybrid vs Onsite Trends
* Hiring Concentration Pie Chart
* Skill Demand Bubble Chart
* Hiring Momentum Heatmap

---

# Example Python Visualization

```python
pivot_mode.plot(
    kind='area',
    stacked=True,
    figsize=(10,4),
    title='Remote vs Hybrid vs Onsite Trend Over Time'
)

plt.ylabel('Job Count')
plt.xlabel('Month')
plt.xticks(rotation=45)
plt.show()
```

---

# Business Value

This project can help:

### Job Seekers

* Understand high-demand skills
* Identify fast-growing companies
* Learn which technologies improve employability

### Recruiters

* Benchmark hiring strategies
* Analyze competitor hiring behavior
* Track market demand shifts

### Companies

* Optimize workforce planning
* Understand remote work adoption trends
* Improve hiring intelligence

### Data Analysts

* Practice advanced SQL and Python analytics
* Learn real-world feature engineering
* Build portfolio-ready business intelligence projects

---

# Challenges Solved

## Unstructured Skill Processing

The original dataset stored multiple skills in a single text column.

### Solution

Used Python `.explode()` transformations to convert skills into row-level records for accurate analysis.

---

## Inconsistent Job Levels

Raw job levels contained inconsistent formats:

* Entry
* Junior
* Mid-Senior
* Staff
* Lead

### Solution

Built SQL and Python standardization logic using CASE statements and mapping functions.

---

## Hiring Stability Analysis

Simple job counts were insufficient for measuring workforce consistency.

### Solution

Developed a Stability Score using:

* Average hiring
* Hiring volatility
* Statistical variance

---

# Final Conclusion

This project demonstrates how data analytics can transform raw job postings into actionable workforce intelligence.

The analysis reveals that:

* The market is highly skill-driven.
* Senior talent demand dominates hiring.
* SQL and Python remain foundational technologies.
* Cloud and orchestration tools define premium talent.
* Hiring behavior varies significantly between companies.
* Remote work adoption continues to evolve.

The project combines:

* Advanced SQL
* Python feature engineering
* Data storytelling
* Visualization techniques
* Business intelligence strategy

into a complete real-world analytics solution.

---

# Author

## Kushala Chikkappanna Reddy

### Skills

* Python
* SQL
* Data Analytics
* Power BI
* Excel
* Data Visualization
* Business Intelligence
* Cloud Technologies

---

# Future Improvements

Planned future enhancements include:

* Machine Learning salary prediction
* NLP-based skill extraction
* Real-time job scraping pipelines
* Interactive Power BI dashboard
* Predictive hiring trend forecasting
* AI-driven job recommendation system

---

# Repository

GitHub Repository:

`Kushala125/JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-`

---

# License

This project is intended for educational, portfolio, and research purposes.
