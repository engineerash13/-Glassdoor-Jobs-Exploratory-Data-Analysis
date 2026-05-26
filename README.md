# Glassdoor Jobs EDA — Salary Trends & Workplace Analytics

An Exploratory Data Analysis of Glassdoor job postings (956 records) to uncover salary patterns, geographic job distribution, company rating dynamics, and in-demand technical skills. The project includes advanced feature engineering — salary parsing, skill extraction from job descriptions, company age calculation, and competitor analysis — to deliver actionable insights for job seekers, employers, and recruiters.

**Author:** Ashwin Suryawanshi | **Type:** Individual Project

---

## Files in This Repository

| File | Description |
|------|-------------|
| `Glassdoor_EDA_By_Ashwin_Suryawanshi.ipynb` | Full EDA notebook — 9-step feature engineering, 20+ Seaborn/Plotly charts across UBM framework |

---

## Tools & Technologies

- **Python** — Pandas, NumPy
- **Visualization** — Matplotlib, Seaborn, Plotly Express
- **Jupyter Notebook** — Google Colab

---

## Dataset

**Source:** `glassdoor_jobs.csv`
**Size:** 956 rows × 15 columns | 0 duplicates | 0 missing values

| Column | Description |
|--------|-------------|
| `Job Title` | Title of the job position |
| `Company Name` | Name of the company (with embedded rating removed in wrangling) |
| `Location` | City and state of the job |
| `Headquarters` | Company's headquarter location |
| `Salary Estimate` | Estimated salary range (e.g., "$80K-$120K") |
| `Job Description` | Full text of job responsibilities and qualifications |
| `Rating` | Company rating on Glassdoor (1.0–5.0 scale) |
| `Company Size` | Employee headcount range (e.g., 51–200, 1000–5000) |
| `Company Type` | Public, Private, Government, or Other |
| `Industry` | Business sector (Tech, Finance, Healthcare, etc.) |
| `Sector` | Broader sector classification |
| `Revenue` | Company estimated revenue range |
| `Founded` | Year company was founded |
| `Competitors` | Comma-separated list of competing companies |

---

## Feature Engineering (9 steps)

| Feature | Logic | Insight |
|---------|-------|---------|
| `min_salary` | Parsed from Salary Estimate string — extracted lower bound | Enables numerical salary analysis |
| `max_salary` | Parsed from Salary Estimate string — extracted upper bound | Enables salary range comparison |
| `avg_salary` | `(min_salary + max_salary) / 2` | Primary salary metric for all comparisons |
| `company_txt` | Stripped embedded rating from Company Name string | Clean grouping by company |
| `job_state` | Extracted state abbreviation from Location | State-level job distribution analysis |
| `same_state` | Binary — 1 if Location == Headquarters | Identifies remote vs HQ-based roles |
| `age` | `2023 - Founded` (for valid years) | Company stability proxy |
| `python_yn` / `R_yn` / `spark` / `aws` / `excel` | Binary flags — keyword presence in Job Description | In-demand skill frequency mapping |
| `desc_len` | `len(Job Description)` | Proxy for role complexity |
| `num_comp` | Count of comma-separated competitors | Market competition intensity |

---

## Charts (20+ — UBM Framework)

### Univariate Analysis
| Chart | Type | Key Insight |
|-------|------|-------------|
| Distribution of Company Ratings | Histogram + KDE | Slightly right-skewed; most companies cluster between 3.0–4.0; peak at ~3.5 |
| Number of Jobs by State | Countplot | California dominates significantly; MA, NY, VA are secondary hubs |
| Salary Estimate Distribution | Histogram | Average salaries cluster in $80K–$120K range for data roles |
| Company Size Distribution | Bar Chart | Mid-size companies (201–500, 1001–5000) post most data job listings |
| Industry Distribution | Bar Chart | IT and Business Services sectors post the most roles |

### Bivariate Analysis
| Chart | Type | Key Insight |
|-------|------|-------------|
| Average Salary by State | Horizontal Box Plot | California and New York show highest median salaries with significant outliers |
| Average Salary vs Company Rating | Scatter Plot | Weak positive correlation — higher salary does not guarantee higher rating |
| Average Salary vs Job Description Length | Regression Plot | Weak positive correlation — longer descriptions suggest more complex, higher-paid roles |
| Salary by Company Size | Box Plot | Larger companies (5000+ employees) offer wider salary ranges and higher ceilings |
| Salary by Company Type | Box Plot | Public companies show higher median salaries than private firms |
| Skills Frequency | Bar Chart | Python is most in-demand (highest frequency in JDs), followed by Excel and AWS |

### Multivariate Analysis
| Chart | Type | Key Insight |
|-------|------|-------------|
| Correlation Heatmap (avg_salary, Rating, desc_len, num_comp) | Heatmap | All correlations are weak — no single feature strongly predicts salary |
| Salary vs Rating by Industry | Scatter (colored by industry) | Finance and Tech industries cluster at higher salary + higher rating quadrant |
| Salary vs Company Age | Scatter Plot | Newer companies show more salary variance; mature companies more stable pay bands |
| State vs Skill Demand | Grouped Bar | California shows highest Python and AWS demand; NY leans toward Excel and R |

---

## Key Insights

- **California** has the most job postings — significantly more than any other state
- **Python is the #1 in-demand skill** appearing most frequently in job descriptions, followed by Excel and AWS
- **No strong correlation between salary and company rating** — compensation alone doesn't drive employee satisfaction
- **Company size positively correlates with salary ceiling** — larger companies offer higher maximum pay
- **Public companies pay more** than private firms across comparable roles
- **Job description length weakly predicts salary** — more complex roles tend to have longer, more detailed descriptions
- **Newer companies show more salary variance** — startups offer both very high and very low salaries relative to their size

---

## Business Recommendations

**For Job Seekers:**
- Target California, New York, and Massachusetts for the highest salary and job density
- Prioritise Python and AWS skills — appear most frequently in job descriptions
- Don't rely solely on salary when evaluating companies — rating correlates with culture, not just pay

**For Employers:**
- Benchmark salaries against California and NY rates to remain competitive for remote talent
- Improve company rating through culture and growth opportunities, not just compensation
- Use detailed job descriptions — they signal role complexity and attract qualified candidates

**For Recruiters:**
- High competitor count in an industry signals competitive talent market — adjust salary offers accordingly
- Mid-size companies (201–1000 employees) represent the highest volume of active hiring

---

## Topics

`eda` `python` `seaborn` `matplotlib` `glassdoor` `salary-analysis` `data-analysis` `pandas` `job-market` `feature-engineering`
