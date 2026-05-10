<div align="center">

<br/>

# 📊 Job Market Intelligence & Hiring Trend Analysis

### *A complete, end-to-end data analytics project that transforms 6,025 raw LinkedIn-style job postings into real, actionable workforce intelligence*

<br/>

[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![SQL](https://img.shields.io/badge/SQL-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://sqlite.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge&logo=python&logoColor=white)](https://matplotlib.org)
[![Excel](https://img.shields.io/badge/Excel-Dashboard-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)](https://microsoft.com/excel)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)

[![GitHub stars](https://img.shields.io/github/stars/Kushala125/JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-?style=for-the-badge&color=FFD700)](https://github.com/Kushala125/JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-)
[![Last Commit](https://img.shields.io/github/last-commit/Kushala125/JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-?style=for-the-badge&color=00D4AA)](https://github.com/Kushala125/JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-)

<br/>

---

</div>

<br/>

## 📌 Table of Contents

- [What Is This Project?](#-what-is-this-project)
- [The Problem It Solves](#-the-problem-it-solves)
- [Dataset Overview](#-dataset-overview)
- [Project Architecture](#-project-architecture)
- [Phase 1 — Data Cleaning](#-phase-1--data-cleaning-with-python)
- [Phase 2 — Feature Engineering](#-phase-2--feature-engineering)
- [Phase 3 — Advanced SQL Analytics](#-phase-3--advanced-sql-analytics)
- [Phase 4 — Visualizations](#-phase-4--visualizations)
- [Key Findings & Insights](#-key-findings--insights)
- [Technologies Used](#-technologies-used)
- [Who This Helps](#-who-this-helps)
- [Future Roadmap](#-future-roadmap)

<br/>

---

<br/>

## 🧭 What Is This Project?

Most people approach the job market the same way — they scroll through postings, apply broadly, and hope for the best. This project takes a completely different approach.

> **Instead of reading the job market, this project measures it.**

Using **6,025 real job postings** scraped from a LinkedIn-style source, the project applies a full data analytics pipeline — Python, SQL, and Excel — to systematically answer the questions that matter most to job seekers, recruiters, and hiring teams.

Think of it as building your own private workforce intelligence tool, similar to what HR analytics teams at large companies use internally — but built from scratch with open tools and documented transparently.

The project covers every stage of a real analytics workflow:

```
Raw messy data  →  Python cleaning  →  Feature engineering
      →  Advanced SQL queries  →  Python visualizations  →  Excel dashboard
```

Each stage has a clear purpose, and every decision is explained below.

<br/>

---

<br/>

## 🎯 The Problem It Solves

Without data, people answering career questions rely on guesswork and anecdotes:

> *"Should I learn Azure or AWS first?"*
> *"Is remote work actually common, or just tech Twitter hype?"*
> *"Do companies actually hire junior people, or is 'entry level' a myth now?"*
> *"Which companies are genuinely growing vs. just posting a lot?"*

This project replaces those guesses with **hard numbers from real postings**. Every insight comes directly from the data — not from opinion, trends blogs, or personal bias.

It answers five strategic questions:

| # | Question | Why It Matters |
|---|---|---|
| 1 | Which skills appear most in job postings? | Tells you exactly where to focus your learning time |
| 2 | Which skills are always paired together? | Shows which combinations make you truly competitive |
| 3 | Is the market tilted toward senior or junior talent? | Tells junior candidates how hard entry actually is |
| 4 | Which companies hire consistently vs. erratically? | Helps job seekers target stable, growing employers |
| 5 | What is the true split of remote vs. onsite vs. hybrid? | Cuts through hype with actual numbers |

<br/>

---

<br/>

## 📁 Dataset Overview

### What the raw data looked like

The dataset contains **6,025 job postings** across 11 columns. Here is the full raw schema:

| Column | What It Contains | Example Value |
|---|---|---|
| `job_title` | The exact role title as posted | `"Senior Data Engineer"` |
| `company` | Hiring company name | `"Cook Medical"` |
| `job_location` | City and state combined in one field | `"Bloomington, IN"` |
| `job_link` | URL to the original posting | `"https://linkedin.com/jobs/..."` |
| `first_seen` | Date the posting was first scraped | `"2023-12-17"` *(stored as text)* |
| `search_city` | City used when the scraper ran | `"Bloomington"` |
| `search_country` | Country of the search | `"United States"` |
| `job level` | Seniority classification | `"Mid senior"` *(wildly inconsistent)* |
| `job_type` | Work arrangement | `"Onsite"` |
| `job_summary` | Full job description text | *Long paragraph...* |
| `job_skills` | All required skills, comma-separated | `"Azure, SQL, NoSQL, MongoDB..."` |

### Why the raw data was challenging

Three structural problems made the raw data impossible to analyze without cleaning first:

1. **Job levels were inconsistent** — "Mid senior", "Staff", "Lead", "Entry Level" all mean different things and have no standard format across companies
2. **Skills were packed into a single cell** — You cannot accurately count how many jobs require Python if 10 different skills are crammed into one text field per row
3. **Date and location were raw strings** — `"2023-12-17"` is not a date Python can calculate with; `"Bloomington, IN"` is one field when you need two

All three problems were solved systematically before any analysis began.

<br/>

---

<br/>

## 🗂️ Project Architecture

```
JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-/
│
├── 📁 excel/
│   └── dashboard excel.xlsx          ← Final business intelligence dashboard
│                                        Built in Excel with pivot tables and charts
│                                        Designed for executive-level reporting
│
├── 📁 images/
│   ├── chart1.png                    ← Hiring Momentum Heatmap
│   ├── chart2.png                    ← Skill Dominance Curve
│   ├── chart3.png                    ← Remote vs Hybrid vs Onsite Trend
│   ├── chart4.png                    ← Hiring Concentration Pie Chart
│   ├── chart 5.png                   ← Skill Demand Bubble Chart by Seniority
│   └── chart6.png                    ← Full Dashboard Screenshot
│
├── 📁 notebook/
│   └── job analysis.ipynb            ← All Python code: cleaning, EDA, charts
│                                        Run this notebook to reproduce every result
│
├── 📁 sql/
│   └── Advanced SQL Queries.sql      ← 15+ analytical SQL queries
│                                        Uses CTEs, window functions, aggregations
│
├── 📄 README.md                      ← This file
└── 📄 Job Market Intelligence Project – Full Summary.pdf  ← Written report
```

<br/>

---

<br/>

## 🧹 Phase 1 — Data Cleaning with Python

> **Goal:** Turn messy, inconsistent raw data into a reliable foundation for analysis.
> **Tool:** Python + Pandas | **File:** `notebook/job analysis.ipynb`

Before any insight can be generated, the data must be trustworthy. This phase fixes four separate problems in the raw dataset:

---

### Problem 1: Inconsistent Job Level Labels

**The issue:** The `job level` column had dozens of formats. "Mid senior", "Staff Engineer", "Lead Analyst", "Entry Level" — all written differently by different companies, with no standard.

**Why it matters:** You cannot count how many "Senior" roles exist if they're labeled in 50 different ways. Grouping and analysis requires a shared vocabulary.

**The fix:** A Python function reads each raw label, checks it for recognizable keywords, and maps it to one of three clean output categories.

```python
def clean_job_level(level):
    """
    Maps raw job level text → Junior / Senior / Mid.

    Why keyword matching instead of exact string matching?
    Because raw data has hundreds of variations: "Mid senior",
    "Senior Staff", "Lead Engineer" all mean Senior. Checking
    for the keyword catches all of them regardless of phrasing.
    """
    if pd.isna(level):
        return 'Unknown'          # Handle missing values safely first

    level = level.lower()         # Lowercase so "SENIOR" and "senior" both match

    if 'junior' in level or 'entry' in level:
        return 'Junior'

    elif 'senior' in level or 'staff' in level or 'lead' in level:
        return 'Senior'

    return 'Mid'                  # Default: anything that doesn't match the rules above

df['job_level_clean'] = df['job_level'].apply(clean_job_level)
```

**Result:** Every row now has exactly one of three clean labels: `Junior`, `Mid`, or `Senior`.

---

### Problem 2: All Skills Packed Into One Column

**The issue:** A single job posting listed all its required skills in one comma-separated text cell: `"Python, SQL, Azure, Snowflake, Airflow"`. That's one row with five skills — but treated as a single indivisible value by the database.

**Why it matters:** If you try to count how many jobs require Python without separating the skills first, your count will be wrong. You need one row per skill to count correctly.

**The fix:** Two steps — first split the string into a Python list, then *explode* the list so each skill gets its own row.

```python
# Step 1: Convert the comma-separated string into a Python list
# "PYTHON, SQL, AZURE" becomes ['PYTHON', 'SQL', 'AZURE']
df['skill_list'] = df['job_skills_clean'].apply(
    lambda x: [s.strip() for s in x.split(',') if s.strip()]
)

# Step 2: Explode — each item in the list becomes its own row.
# A job with 5 skills goes from 1 row to 5 rows, one per skill.
# This is what makes accurate skill counting possible.
skills_df = df[['job_title', 'company', 'skill_list']].explode('skill_list')
skills_df = skills_df.rename(columns={'skill_list': 'skill'})
```

**Before explode (1 row):**

| job_title | skill_list |
|---|---|
| Data Engineer | `['PYTHON', 'SQL', 'AZURE']` |

**After explode (3 rows):**

| job_title | skill |
|---|---|
| Data Engineer | PYTHON |
| Data Engineer | SQL |
| Data Engineer | AZURE |

**Result:** 6,025 job postings → **14,532+ individual skill records** that can be counted with full accuracy.

---

### Problem 3: Skill Name Variations

**The issue:** "SQL", "NoSQL", "SQL Server", and "Oracle" look similar but are different technologies. Meanwhile, "Power BI" and "PowerBI" are identical technologies written two different ways.

**Why it matters:** If "POWER BI" and "POWERBI" are counted separately, each gets half the true count. The skill demand numbers will be wrong.

**The fix:** A normalization function applies business logic to collapse variant spellings into one canonical name per skill.

```python
def normalize_skill(skill):
    """
    Maps skill name variants to a single canonical form.

    Why this matters: "POWER BI" and "POWERBI" are the same skill.
    Without this function, they'd be counted as two different skills,
    splitting their true demand count in half.
    """
    if not isinstance(skill, str):
        return 'UNKNOWN'

    skill = skill.strip().upper()

    if 'SQL' in skill:                              return 'SQL'
    if 'PYTHON' in skill:                           return 'PYTHON'
    if 'POWER BI' in skill or 'POWERBI' in skill:  return 'POWER BI'
    if 'AZURE' in skill:                            return 'AZURE'
    if 'AWS' in skill:                              return 'AWS'
    if 'SNOWFLAKE' in skill:                        return 'SNOWFLAKE'
    if 'AIRFLOW' in skill:                          return 'AIRFLOW'

    return skill    # Return unchanged if no normalization rule applies
```

---

### Problem 4: Duplicate Postings

**The issue:** Some postings appeared multiple times — likely because the same job was still open when the scraper ran on different days.

**Why it matters:** Duplicates inflate every count. If "Recruiting from Scratch" posted 100 unique jobs but each appeared twice, the analysis would incorrectly show 200.

**The fix:** Drop any row that shares the same combination of job title + company + location as an existing row.

```python
# A posting is a duplicate if it matches another on all three fields.
# keep='first' means we retain the original and drop the repeat.
df = df.drop_duplicates(subset=['job_title', 'company', 'job_location'])
```

<br/>

---

<br/>

## ⚙️ Phase 2 — Feature Engineering

> **Goal:** Build new, useful columns from the data that already exists.
> **Why:** Raw data rarely contains the exact features an analysis needs — you derive them.

Feature engineering is the process of creating new columns by transforming or combining existing ones. Three important feature groups were built:

---

### Time Features

The `first_seen` column was stored as a plain text string like `"2023-12-17"`. Python cannot do date arithmetic or month-based grouping on a string — it first needs to be converted to a proper datetime object, then broken into components.

```python
# Convert raw string → real datetime (errors='coerce' turns bad values into NaT)
df['first_seen'] = pd.to_datetime(df['first_seen'], errors='coerce')

# Extract the time components we need for grouping
df['year']       = df['first_seen'].dt.year           # → 2023
df['month']      = df['first_seen'].dt.month          # → 12
df['year_month'] = df['first_seen'].dt.to_period('M').astype(str)  # → "2023-12"
```

The `year_month` column is the most important — it lets us group all jobs posted in December 2023 together so we can draw hiring trend charts over time.

---

### Location Features

`"Bloomington, IN"` is one string field. For any state-level analysis or filtering by geography, we need city and state as separate, independent columns.

```python
# Split on the comma to get city and state separately
location_split  = df['job_location'].str.split(',', expand=True)
df['city']  = location_split[0].str.strip()    # → "Bloomington"
df['state'] = location_split[1].str.strip()    # → "IN"
df['state'] = df['state'].fillna('Unknown')    # Handle postings with no state listed
```

---

### Experience Buckets

This translates the cleaned job level category into a human-readable experience range. It makes dashboard labels more intuitive for non-technical stakeholders.

```python
def experience_bucket(level):
    """Converts job level label into a plain-English experience range."""
    if level == 'Junior':   return '0–2 years'
    elif level == 'Mid':    return '3–5 years'
    elif level == 'Senior': return '6+ years'
    else:                   return 'Unknown'

df['experience_bucket'] = df['job_level_clean'].apply(experience_bucket)
```

---

### Job Role Normalization

Job titles in real data are extremely varied. "Staff Data Engineer", "Senior Data Engineer (Public Company)", "Data Engineer 2", and "Sr. DE" all describe the same role family. A normalization function maps hundreds of title variations into five clean role categories so we can count them.

```python
def normalize_job_title(title):
    """
    Groups hundreds of unique job titles into 5 clean role families.
    Without this, "Data Engineer" and "Senior Data Engineer" would be
    counted as completely separate roles.
    """
    title = title.lower()
    if 'data analyst' in title:       return 'Data Analyst'
    elif 'data engineer' in title:    return 'Data Engineer'
    elif 'business analyst' in title: return 'Business Analyst'
    elif 'analytics' in title:        return 'Analytics Role'
    else:                             return 'Other'

df['job_role'] = df['job_title'].apply(normalize_job_title)
```

<br/>

---

<br/>

## 🗄️ Phase 3 — Advanced SQL Analytics

> **Goal:** Answer complex business questions requiring aggregation, ranking, and statistical calculation.
> **Tool:** SQLite + SQL | **File:** `sql/Advanced SQL Queries.sql`

After the Python cleaning phase, the clean data was loaded into SQLite. SQL was then used to run 15+ analytical queries. Three of the most strategically important are explained here in full detail:

---

### Query 1: The Hiring Stability Score

**Business question:** *Which companies hire consistently every month, and which ones just had a one-time surge?*

**Why this matters:** Total job count is a misleading metric. A company that posted 60 jobs in January and then nothing for 5 months looks the same as a company posting 10 jobs every month — both show 60 total. But they represent very different realities. The stability score reveals the difference.

**How the math works:** The query computes each company's standard deviation of monthly job postings. Standard deviation measures how much numbers vary from their average.

- Low standard deviation = company hires approximately the same amount every month = **stable**
- High standard deviation = company had one huge hiring month and many quiet months = **volatile**

The Stability Score divides Average Monthly Jobs by Standard Deviation. Higher = more stable.

> Note: SQLite does not have a built-in `STDDEV()` function. The standard deviation is computed manually using the mathematical identity: `STDDEV = SQRT(AVG(x²) - AVG(x)²)`

```sql
WITH monthly_jobs AS (

    -- Step 1: Count how many jobs each company posted each month
    SELECT
        company,
        substr(first_seen, 1, 7) AS year_month,   -- Extracts "2023-12" from the date
        COUNT(*)                 AS jobs
    FROM postings
    GROUP BY company, year_month

),

stats AS (

    -- Step 2: For each company, compute the inputs needed for standard deviation.
    -- We need AVG(jobs) and AVG(jobs²) to apply the variance formula.
    SELECT
        company,
        AVG(jobs)         AS avg_jobs,
        AVG(jobs * jobs)  AS avg_jobs_sq
    FROM monthly_jobs
    GROUP BY company

)

SELECT
    company,
    ROUND(avg_jobs, 2)  AS avg_monthly_jobs,

    -- Standard deviation manually: SQRT(AVG(x²) - AVG(x)²)
    ROUND(SQRT(avg_jobs_sq - avg_jobs * avg_jobs), 2)  AS hiring_volatility,

    -- Stability Score: high avg ÷ low volatility = predictable, consistent hiring
    -- NULLIF prevents division-by-zero for companies with only one month of data
    ROUND(avg_jobs / NULLIF(SQRT(avg_jobs_sq - avg_jobs * avg_jobs), 0), 2)
                                                       AS stability_score

FROM stats
ORDER BY stability_score DESC;
```

---

### Query 2: Senior vs Junior Ratio Over Time

**Business question:** *Is the job market accessible to junior candidates, or dominated by senior roles?*

**Why this matters:** This answers one of the most discussed questions in data careers — is the entry-level market actually shrinking? — with evidence instead of opinion.

```sql
WITH job_levels AS (

    -- Step 1: Classify every posting as Junior, Senior, or Mid
    -- using the same keyword logic as the Python cleaning phase
    SELECT
        substr(first_seen, 1, 7) AS year_month,
        CASE
            WHEN lower("job level") LIKE '%junior%'
              OR lower("job level") LIKE '%entry%'  THEN 'Junior'
            WHEN lower("job level") LIKE '%senior%'
              OR lower("job level") LIKE '%lead%'
              OR lower("job level") LIKE '%staff%'  THEN 'Senior'
            ELSE 'Mid'
        END AS job_level
    FROM postings

)

SELECT
    year_month,

    -- Count Senior and Junior in the same row using conditional aggregation.
    -- CASE WHEN inside SUM() is how SQL pivots categories into columns.
    SUM(CASE WHEN job_level = 'Senior' THEN 1 ELSE 0 END)  AS senior_jobs,
    SUM(CASE WHEN job_level = 'Junior' THEN 1 ELSE 0 END)  AS junior_jobs,

    -- For every 1 junior role, how many senior roles exist?
    -- A ratio of 5 means 5 senior postings for every 1 junior posting.
    -- NULLIF prevents division-by-zero when no junior roles exist in a month.
    ROUND(
        1.0 * SUM(CASE WHEN job_level = 'Senior' THEN 1 ELSE 0 END)
            / NULLIF(SUM(CASE WHEN job_level = 'Junior' THEN 1 ELSE 0 END), 0),
        2
    ) AS senior_to_junior_ratio

FROM job_levels
GROUP BY year_month
ORDER BY year_month;
```

---

### Query 3: Company Market Share (Window Functions)

**Business question:** *What percentage of total hiring does each company control?*

**Why this matters:** It reveals whether the market is competitive and distributed, or whether a small number of players dominate. This has direct implications for job seekers evaluating which channels to prioritize.

```sql
WITH monthly_totals AS (
    -- The total number of jobs across the entire market each month
    SELECT
        substr(first_seen, 1, 7) AS year_month,
        COUNT(*) AS total_jobs
    FROM postings
    GROUP BY year_month
),

company_monthly AS (
    -- Each individual company's job count per month
    SELECT
        company,
        substr(first_seen, 1, 7) AS year_month,
        COUNT(*) AS company_jobs
    FROM postings
    GROUP BY company, year_month
)

SELECT
    c.company,
    c.year_month,
    -- Market share = this company's jobs / all jobs in that month × 100
    ROUND(100.0 * c.company_jobs / t.total_jobs, 2)  AS market_share_percent
FROM company_monthly c
JOIN monthly_totals t ON c.year_month = t.year_month
ORDER BY market_share_percent DESC;
```

<br/>

---

<br/>

## 📈 Phase 4 — Visualizations

> **Goal:** Translate numbers into charts that tell a clear story at a glance.
> **Tool:** Matplotlib (Python) + Excel | **Files:** `images/` + `excel/`

Six visualizations were built, each designed to answer one specific question visually:

---

### Chart 1 — Hiring Momentum Heatmap

```python
pivot = df.groupby(['year_month', 'job_level_clean']).size().unstack(fill_value=0)

plt.imshow(pivot.T, aspect='auto')
plt.colorbar(label='Job Count')
plt.title('Hiring Momentum by Job Level Over Time')
```

**What it shows:** A color grid where rows are job levels and columns are time periods. Darker color = more jobs posted. The heatmap lets you instantly see which level dominated hiring and whether activity was rising or falling — something a table of numbers would not show clearly.

---

### Chart 2 — Skill Dominance Curve (Long Tail)

```python
skill_counts = skills_df['skill_clean'].value_counts()

plt.plot(skill_counts.values)
plt.title('Skill Dominance Curve (Long Tail)')
plt.ylabel('Job Mentions')
plt.xlabel('Skill Rank')
```

**What it shows:** The classic long-tail distribution of skill demand. SQL and Python tower above everything else on the left. The curve then drops steeply and flattens into a long tail of thousands of niche skills that each appear in only a handful of postings. This shape is extremely informative — it proves the market concentrates heavily on a small set of core skills.

---

### Chart 3 — Remote vs Hybrid vs Onsite Trend

```python
pivot_mode = df.groupby(['year_month', 'job_type_clean']).size().unstack(fill_value=0)

pivot_mode.plot(kind='area', stacked=True, figsize=(10,4),
    title='Remote vs Hybrid vs Onsite Trend Over Time')
```

**What it shows:** A stacked area chart where each work mode occupies its own colored band. The relative size of each band shows the proportion of that mode in the overall market. This chart cuts through remote-work hype by showing actual numbers — not claims.

---

### Chart 4 — Hiring Concentration Pie

```python
company_counts = df['company'].value_counts()
top_10  = company_counts.head(10).sum()
others  = company_counts.iloc[10:].sum()

plt.pie([top_10, others], labels=['Top 10 Companies', 'All Others'], autopct='%1.1f%%')
plt.title('Hiring Concentration')
```

**What it shows:** The proportion of all job postings controlled by just the top 10 companies versus every other company combined. A highly skewed pie means the market is dominated by a few players — which shapes every other strategic decision a job seeker or recruiter makes.

---

### Chart 5 — Skill Demand Bubble Chart (by Seniority)

```python
plt.scatter(
    plot_data['job_skills'],
    plot_data['job_level'],
    s=plot_data['count'] * 5,    # Bubble SIZE represents job count
    alpha=0.6
)
plt.title('Skill Demand by Job Seniority (Bubble Chart)')
```

**What it shows:** Each bubble sits at the intersection of a skill (x-axis) and a seniority level (y-axis). The larger the bubble, the more postings require that skill at that seniority level. This reveals which skills are universal across all levels and which appear almost exclusively in senior roles — directly informing career progression decisions.

<br/>

---

<br/>

## 💡 Key Findings & Insights

### Finding 1: SQL Is Non-Negotiable

With **4,894 job mentions**, SQL is the single most demanded skill in the entire dataset — more than double Python and more than twice Azure. If your resume doesn't show SQL proficiency, you are screened out before a human reads your application in the majority of data roles.

```
Skill              Mentions    Demand Index (SQL = 100%)
─────────────────────────────────────────────────────────
SQL                  4,894     ████████████████████ 100%
Python               2,759     ████████████          56%
Azure                2,177     █████████             45%
AWS                  1,814     ████████              37%
Data Engineering     1,182     █████                 24%
Data Analysis        1,099     ████                  22%
ETL                    973     ████                  20%
Power BI               961     ████                  20%
Data Modeling          924     ████                  19%
Data Visualization     898     ████                  18%
```

---

### Finding 2: Skill Pairs Matter More Than Individual Skills

The co-occurrence analysis measured which skills companies expect to see *together* in the same candidate. Python and SQL co-occur in **1,707 postings** — the strongest pairing in the entire dataset by a wide margin. Companies have learned to expect this combination as a baseline package.

```
Strongest Skill Pairs        Co-occurrences   Index
──────────────────────────────────────────────────────
Python  ×  SQL                   1,707         100%
AWS     ×  SQL                     843          49%
AWS     ×  Python                  826          48%
Azure   ×  SQL                     779          46%
Data Engineering × SQL             730          43%
Data Analysis    × SQL             698          41%
Data Engineering × Python          671          39%
Power BI × SQL                     661          39%
Data Modeling    × SQL             649          38%
SQL     × Tableau                  630          37%
```

**What this means for your career:** Python + SQL + one cloud platform (Azure or AWS) simultaneously covers the three strongest skill pairings in the market. Learning these three together is more efficient than learning five unrelated skills.

---

### Finding 3: The Market Has Two Distinct Layers

The bubble chart and seniority breakdown revealed a structure that is invisible from casual job browsing — the market effectively operates as two separate markets at the same time:

**Layer 1 — Utility Skills (universal, table stakes)**

These appear across Junior, Mid, and Senior roles equally. Every company expects them. They are minimum requirements, not differentiators. Having them does not make you stand out; lacking them removes you from consideration.

> `SQL` · `Python` · `Excel` · `Data Visualization`

**Layer 2 — Strategic Skills (senior-exclusive, premium value)**

These appear almost exclusively in Senior and Lead roles. They separate a $70K data analyst from a $140K senior data engineer. They are what companies mean when they say they want "strategic" talent.

> `Snowflake` · `Airflow` · `Kubernetes` · `Cloud Architecture` · `ML Infrastructure`

**The practical implication:** If you have only Layer 1 skills, you are competing in a crowded, price-sensitive entry zone. Adding even one Layer 2 skill repositions you into a fundamentally different tier of the market with less competition and higher pay.

---

### Finding 4: Remote Work Is the Minority

Despite widespread discussion about remote-first work cultures, the actual data tells a different story:

```
Work Mode     Share      Job Count
───────────────────────────────────
Onsite        46.4%        2,628
Hybrid        33.9%        1,920
Remote        19.6%        1,110
```

Nearly half of all postings require full-time, in-person work. Only 1 in 5 roles is fully remote. The discourse around remote work significantly overstates its actual prevalence in data and analytics roles.

---

### Finding 5: Staffing Firms Dominate the Numbers

The top companies by job count are almost entirely **recruiting and staffing firms**, not end employers:

```
#1   Recruiting from Scratch     214 jobs
#2   Steneral Consulting         100 jobs
#3   Nigel Frank International    74 jobs
#4   Railroad19                   58 jobs
#5   Motion Recruitment           56 jobs
```

**What this means:** A large portion of visible job postings are intermediated by third-party recruiters — not direct hiring by companies. This is a critical nuance for job seekers: applying through a staffing firm is a fundamentally different process with different timelines, incentives, and evaluation criteria than applying directly to an employer.

<br/>

---

<br/>

## 🛠️ Technologies Used

| Technology | Role in This Project |
|---|---|
| **Python 3.11** | Main programming language for the entire data pipeline |
| **Pandas** | Data loading, cleaning, transformation, and aggregation |
| **NumPy** | Numerical operations supporting statistical calculations |
| **SQLite** | Lightweight database engine for running analytical SQL queries |
| **SQL** | CTEs, window functions, conditional aggregations, and the stability score formula |
| **Matplotlib** | All six analytical charts and visualizations |
| **Excel** | Final business intelligence dashboard for non-technical stakeholders |
| **Jupyter Notebook** | Development environment — all code is documented inline with explanations |
| **GitHub** | Version control and public portfolio hosting |

<br/>

---

<br/>

## 👥 Who This Helps

### For Job Seekers
- Know which skills to prioritize — based on actual market demand, not YouTube advice
- Identify companies with stable, consistent hiring patterns (high stability score)
- Understand the true difficulty of breaking into the market as a junior candidate, with numbers

### For Recruiters & HR Teams
- Benchmark your company's skill requirements and hiring pace against market norms
- Identify skill trends before they become industry-wide consensus
- Understand which roles attract the most competition and plan accordingly

### For Companies & Workforce Planners
- Understand what the talent pool expects in terms of work mode
- Identify your own hiring volatility and whether it's affecting candidate trust
- Use market share data to benchmark your hiring footprint

### For Data Analysts & Students
- End-to-end project from raw messy data to clean insights — not a tutorial with pre-cleaned data
- Demonstrates Python, SQL, visualization, feature engineering, and business storytelling together
- Every decision is documented with an explanation of *why*, making it a learning resource not just a portfolio piece

<br/>

---

<br/>

## 🚀 Future Roadmap

- [ ] 🤖 **ML Salary Prediction** — Regression model to predict salary from skills, level, and location
- [ ] 🧬 **NLP Skill Extraction** — Use spaCy or BERT to pull skills from raw job description text automatically, eliminating reliance on the pre-tagged skills column
- [ ] 🔴 **Live Scraping Pipeline** — Automated weekly scraper to refresh the dataset with new postings
- [ ] 📊 **Power BI Dashboard** — Rebuild the Excel dashboard as a fully interactive Power BI report
- [ ] 📅 **Trend Forecasting** — Apply time-series models to predict which skills will rise or decline over the next 6 months
- [ ] 🎯 **Job Matching System** — Input your current skill set and receive a ranked list of the roles you match most strongly

<br/>

---

<br/>

## 📄 License & Usage

This project is intended for **educational, portfolio, and research purposes.**
All data originates from publicly available job postings.
No proprietary or confidential information is included.

<br/>

---

<br/>

<div align="center">

### Built by Kushala Chikkappanna Reddy

*Python · SQL · Data Analytics · Power BI · Excel · Business Intelligence*

[![GitHub](https://img.shields.io/badge/View_Full_Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kushala125/JOB-MARKET-INTELLIGENCE---DATA-ANALYSIS-)

<br/>

---

*"The job market is not random. It is a signal. This project reads it."*

</div>
