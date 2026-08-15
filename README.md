# 📊 Customer Churn Analysis & Retention Analytics

An end-to-end **Customer Churn Analysis and Retention Analytics** project using **SQL and Python** to identify customer churn patterns, analyze subscription behavior, evaluate support interactions, quantify revenue risk, and generate actionable business recommendations.

The project integrates customer, subscription, and support data from a relational SQLite database and applies data cleaning, feature engineering, exploratory data analysis, visualization, and customer risk segmentation.

---

## 🎯 Business Problem

Customer churn directly affects recurring revenue and customer lifetime value.

The objective of this project is to answer three key business questions:

* **Who** is churning or at high risk of churn?
* **Why** are customers churning?
* **When** does churn become a significant business risk?

The analysis focuses on customer demographics, subscription plans, contract types, churn scores, cancellation behavior, revenue, CLTV, complaints, escalations, and CSAT.

---

## 🗄️ Database Structure

The project uses a SQLite database containing three relational tables:

### `db_customer`

Contains customer-level information:

* Customer ID
* Customer Name
* Country
* State
* Gender
* Date of Birth
* Interests
* Pincode

### `db_subscription`

Contains subscription and revenue information:

* Customer ID
* Subscription Start Date
* Subscription Type
* Renewal Date
* Plan Type
* Contract Type
* Cancellation Date
* Cancellation Reason
* Monthly Charges
* CLTV
* Churn Score

### `db_support`

Contains customer support information:

* Customer ID
* Complaint Date
* Escalations
* CSAT Score
* Comments

The three tables are connected using `customerid`.

---

## 🛠️ Tech Stack

| Technology           | Purpose                                      |
| -------------------- | -------------------------------------------- |
| **Python**           | Data analysis and processing                 |
| **SQL**              | Relational data querying                     |
| **SQLite**           | Database management                          |
| **Pandas**           | Data manipulation and analysis               |
| **NumPy**            | Numerical operations and feature engineering |
| **Matplotlib**       | Data visualization                           |
| **Seaborn**          | Statistical visualization                    |
| **Jupyter Notebook** | Interactive analysis                         |

---

## 🔄 Project Workflow

```text
SQLite Database
       ↓
SQL Queries
       ↓
Python + SQLite3
       ↓
Data Extraction
       ↓
Data Cleaning & Quality Checks
       ↓
Feature Engineering
       ↓
EDA & KPI Analysis
       ↓
Customer Risk Segmentation
       ↓
Data Visualization
       ↓
Business Insights
       ↓
Retention Recommendations
```

The project follows the SQL → Python → cleaning → feature engineering → EDA → visualization → insights workflow outlined in the project roadmap.

---

## 🧹 Data Cleaning

The analysis includes several data-cleaning steps:

* Renaming columns for clarity
* Removing unnecessary columns
* Converting date columns to appropriate datetime types
* Standardizing categorical values
* Handling missing country values using state-country mapping
* Removing irrelevant support columns
* Performing data quality checks
* Preparing multiple tables for analysis

For example, gender values such as `Men` and `Women` were standardized to `Male` and `Female`.

---

## ⚙️ Feature Engineering

New analytical features were created to support churn analysis.

### Churn Flag

Customers were classified based on cancellation information to identify churned customers.

### Customer Tenure

Customer tenure was calculated using:

```text
Cancellation Date - Subscription Start Date
```

For active customers, the current date was used as the reference date.

### Churn Risk

Customers were segmented based on their churn score:

| Churn Score | Risk Level |
| ----------: | ---------- |
|      `< 50` | Low        |
|     `50–69` | Medium     |
|     `>= 70` | High       |

This creates a simple risk-segmentation framework for prioritizing retention efforts.

---

## 📈 Key KPIs

The project analyzes several business KPIs, including:

* Churn Rate
* Retention Rate
* Churn by Plan Type
* Churn by Contract Type
* Churn by State
* ARPU
* Average Customer Tenure
* Revenue at Risk
* CLTV Lost
* Escalation Rate
* Average Complaints per Customer
* Escalation vs Churn Relationship

These metrics are designed to connect customer behavior with revenue and retention outcomes.

---

# 🔍 Key Findings

## 1. Overall Churn

The overall customer churn rate was:

### **28.6%**

with a corresponding retention rate of:

### **71.4%**

---

## 2. Contract Type Is a Major Churn Differentiator

One of the strongest findings was the difference between monthly and annual contract customers.

| Contract Type | Churn Rate |
| ------------- | ---------: |
| Monthly       |  **55.6%** |
| Annual        |   **8.3%** |

Monthly-contract customers showed approximately **6.7× higher churn** than annual-contract customers.

This indicates an opportunity to investigate contract migration and retention strategies for suitable monthly subscribers.

---

## 3. Revenue at Risk

The analysis identified approximately:

### **₹73.94**

in monthly revenue associated with churned/high-risk customers in the analyzed dataset.

The project also identified:

### **₹2,047 CLTV Lost**

due to churn.

---

## 4. ARPU

The calculated Average Revenue Per User was approximately:

### **₹18.85**

---

## 5. Support Escalation & Churn

The analysis explored the relationship between support escalations and customer churn.

The calculated correlation between escalation and churn was:

### **0.77**

This suggests a strong relationship within this dataset and highlights customer support interactions as a potentially useful signal for churn-risk monitoring.

> **Note:** Correlation indicates an association in this dataset; it does not by itself establish causation.

---

## 6. Geographic & Time-Based Patterns

The analysis identified:

* **Karnataka** as the most affected state in the analyzed churn data.
* **September 2024** as the month with the highest observed churn.

These patterns can be used as starting points for investigating pricing changes, service issues, customer complaints, or other regional/time-specific factors.

---

# 📊 Visualizations

The project includes visual analysis of:

* Monthly Churn Trend
* Churn by Plan Type
* Churn by Contract Type
* Churn by State
* Customer Risk Segmentation
* Churn-related behavioral patterns

Example analytical workflow:

```python
churn_plan = df_visual.groupby('plan_type')['churn_flag'].mean()
```

This was used to compare churn rates across subscription plans.

---

# 💡 Business Recommendations

Based on the analysis, the following actions can be considered:

### 1. Focus on Monthly Subscribers

Investigate why monthly-contract customers have substantially higher churn and evaluate suitable incentives for longer-term contracts.

### 2. Prioritize High-Risk Customers

Use churn-risk segmentation together with customer value/CLTV to create a prioritized retention list.

### 3. Investigate Support Escalations

Customers with escalated support interactions can be monitored as potential churn-risk signals.

### 4. Investigate Karnataka

Analyze whether pricing, technical problems, service quality, or customer complaints contributed to the higher churn observed in Karnataka.

### 5. Investigate September 2024

Review changes in pricing, product/service experience, customer support, or competitor activity around the September 2024 churn spike.

These recommendations align with the project's business-focused action items.

---

# 🚀 How to Run the Project

## 1. Clone the Repository

```bash
git clone 'my_github_repo_url'
```

## 2. Navigate to the Project

```bash
cd customer-churn-analysis
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

## 5. Open the Analysis Notebook

Open:

```text
notebooks/customer_churn_analysis.ipynb
```

Run the notebook cells sequentially.

---

# 📦 Requirements

```text
numpy
pandas
matplotlib
seaborn
jupyter
```

SQLite is used through Python's built-in `sqlite3` module.

---

# 📌 Project Outcomes

This project demonstrates the ability to:

* Work with relational databases
* Query data using SQL
* Integrate SQL databases with Python
* Clean and transform real-world style datasets
* Perform exploratory data analysis
* Engineer analytical features
* Build customer-risk segments
* Analyze churn and revenue impact
* Create meaningful visualizations
* Translate analytical results into business recommendations

The overall objective is to move from **raw customer data → analytical insight → actionable retention strategy**.

---

# 🔮 Future Improvements

Potential next steps for this project include:

* Building a machine-learning churn prediction model
* Comparing multiple classification algorithms
* Performing model evaluation using precision, recall and F1-score
* Building an interactive dashboard using Power BI or Streamlit
* Creating automated churn-risk reports
* Developing customer-level retention recommendations
* Adding larger and more diverse datasets for improved generalization

---

## 👨‍💻 Author

**Rohan Sawant**

Aspiring **Data Analyst | Data Engineer | Data Scientist**

Interested in building data-driven solutions using **Python, SQL, Data Analytics and Machine Learning**.

---

⭐ If you found this project useful, consider giving the repository a star!
