# 📊 Sprint 5 Project — Megaline Telecom Revenue Statistical Analysis  

---

🧠 **Project Overview**  
In this sprint, I worked as a data analyst for **Megaline**, a telecom operator that offers two prepaid plans — **Surf** and **Ultimate**.  
The business department wanted to identify which plan generates higher average monthly revenue in order to adjust the company’s advertising budget more effectively.  

Using real customer usage data (calls, messages, and internet traffic), I performed a **statistical analysis** to evaluate client behavior and determine whether there is a significant revenue difference between the two plans and across customer regions.  

---

## 🎯 Project Objectives  
- Import, inspect, and clean multiple datasets.  
- Convert data types, detect and fix errors, and handle missing values.  
- Aggregate each customer’s monthly usage (calls / minutes, SMS, MB used).  
- Compute monthly revenue per user according to plan rules.  
- Compare Surf vs Ultimate performance through descriptive statistics.  
- Test hypotheses on plan revenue and regional differences using statistical tests.  

---

## 📁 Datasets  
The project uses five inter-related tables located in the `/datasets/` folder:

| File | Description |
|-------|--------------|
| `megaline_users.csv` | User profile information (ID, name, age, city, plan) |
| `megaline_calls.csv` | Call records with date and duration |
| `megaline_messages.csv` | SMS records with date |
| `megaline_internet.csv` | Internet sessions with data usage (MB) |
| `megaline_plans.csv` | Plan pricing and allowance details |

---

## 🧾 Data Dictionary  

**users**  
- `user_id` – unique user identifier  
- `first_name`, `last_name` – user name  
- `age` – age in years  
- `reg_date` – subscription date  
- `churn_date` – service termination date (if empty, still active)  
- `city` – user’s city  
- `plan` – plan name  

**calls**  
- `id` – unique call ID  
- `call_date` – call date  
- `duration` – call duration (minutes, rounded up per call)  
- `user_id` – user who made the call  

**messages**  
- `id` – unique message ID  
- `message_date` – message date  
- `user_id` – sender ID  

**internet**  
- `id` – unique session ID  
- `mb_used` – megabytes used per session  
- `session_date` – session date  
- `user_id` – user who browsed data  

**plans**  
- `plan_name` – plan name  
- `usd_monthly_fee` – monthly fee in USD  
- `minutes_included` – included minutes per month  
- `messages_included` – included SMS per month  
- `mb_per_month_included` – included data (MB)  
- `usd_per_minute` – price per extra minute  
- `usd_per_message` – price per extra SMS  
- `usd_per_gb` – price per extra GB (1 GB = 1024 MB)  

---

## 📶 Plan Details  

| Plan | Monthly Fee | Included Allowances | Over-Limit Charges |
|------|--------------|--------------------|--------------------|
| **Surf** | \$20 | 500 min, 50 SMS, 15 GB | \$0.03 / min, \$0.03 / SMS, \$10 / GB |
| **Ultimate** | \$70 | 3000 min, 1000 SMS, 30 GB | \$0.01 / min, \$0.01 / SMS, \$7 / GB |

---

## 🧩 Project Steps  

### Step 1 – Load and Inspect Data  
- Read all CSV files using `pandas.read_csv()`.  
- Check column types, missing values, and basic statistics with `info()` and `describe()`.  
- Validate data consistency across tables using `user_id` keys.  

### Step 2 – Data Preparation  
- Convert columns to proper types (`datetime`, `int`, etc.).  
- Detect and remove duplicates and erroneous entries.  
- Aggregate usage per user per month (calls, SMS, data usage).  
- Compute each user’s monthly revenue:  
    `total revenue = base fee + extra minutes/SMS/GB charges`.  

### Step 3 – Exploratory Analysis  
- Describe average monthly minutes, SMS, and data per plan.  
- Compute mean, variance, and standard deviation.  
- Visualize distributions with histograms and boxplots (`matplotlib`, `seaborn`).  

### Step 4 – Hypothesis Testing  
1. **H₀:** The average monthly revenue for Surf and Ultimate users is equal.  
   **H₁:** The average revenue differs between plans.  
2. **H₀:** Average revenue for NY–NJ users equals that of other regions.  
   **H₁:** Average revenues differ by region.  
- Set α = 0.05.  
- Used independent two-sample t-tests (`scipy.stats.ttest_ind`).  
- Interpreted p-values and confidence intervals to draw conclusions.  

### Step 5 – Conclusions  
- Summarized which plan generates higher average revenue.  
- Discussed customer usage patterns and regional differences.  
- Outlined marketing and budget recommendations for Megaline.  

---

## 💼 Skills Developed  
- Data Cleaning and Transformation (`pandas`, `datetime`)  
- Exploratory Data Analysis (EDA)  
- Descriptive Statistics & Distributions  
- Hypothesis Testing (`scipy.stats`)  
- Data Visualization (`matplotlib`, `seaborn`)  
- Business Insight Interpretation from Statistical Evidence  

---

## 🧰 Tools & Technologies  
`Python` | `Pandas` | `NumPy` | `Matplotlib` | `Seaborn` | `SciPy` | `Jupyter Notebook`

---

## 👤 Author  
*Project completed by [Jonathan Peña] as part of Sprint 5 — Statistical Data Analysis Track.*
