# Employee Attrition & Workforce Analytics

## 1. Project Overview
This project is an Exploratory Data Analysis (EDA) on employee attrition using the **IBM HR Analytics Employee Attrition & Performance** dataset. The goal of this project is to understand why employees leave the organization, identify key patterns in employee turnover, and suggest practical recommendations for human resources management.

This analysis was completed as part of the EDA Project Assignment.

---

## 2. Problem Statement
Employee turnover creates hiring expenses, training costs, and loss of productivity. By analyzing workforce data, this project answers:
- What is the overall attrition rate in the company?
- How do salary, experience, and age relate to employees leaving?
- Does working overtime increase the chance of leaving?
- Which departments and job roles face the highest turnover?
- How do work-life balance and commute distance affect employee decisions?

---

## 3. Dataset Summary
- **Source:** IBM HR Analytics Employee Attrition & Performance Dataset
- **Total Records:** 1,470 employees
- **Total Columns:** 35 features initially (reduced to 32 after cleaning)
- **Target Variable:** `Attrition` (`Yes` = Left company, `No` = Stayed)
- **Baseline Attrition Rate:** 16.12% (237 employees left, 1,233 stayed)

---

## 4. Tools & Libraries Used
- **Language:** Python
- **Data Manipulation:** Pandas, NumPy
- **Data Visualization:** Matplotlib, Seaborn
- **Environment:** Google Colab / Jupyter Notebook

---

## 5. Repository Structure
```text
├── data/
│   ├── raw/                 # Original dataset (WA_Fn-UseC_-HR-Employee-Attrition.csv)
│   └── processed/           # Cleaned dataset (hr_cleaned.csv)
├── notebooks/
│   └── employee_attrition_eda.ipynb  # Main analysis notebook with all charts and code
├── reports/
│   └── figures/             # Exported visualizations (.png)
├── hr_attrition_report.pdf  # Final executive summary report (PDF)
├── hr_workforce_analytics.pdf # Presentation slide deck (PDF)
└── README.md                # Project documentation
```

---

## 6. Data Cleaning Steps
1. **Missing Values Check:** Checked all 35 columns; zero missing values were present.
2. **Duplicate Check:** Verified that all rows and employee IDs (`EmployeeNumber`) are unique.
3. **Removed Constant Columns:** Dropped `EmployeeCount`, `Over18`, and `StandardHours` because they hold identical values for every employee and provide no useful information.
4. **Logical Consistency Check:** Confirmed that career experience values are valid (`TotalWorkingYears >= YearsAtCompany` and implied career start age $\ge 16$).
5. **Target Encoding:** Created a binary flag `Attrition_Flag` (1 for `Yes`, 0 for `No`) to calculate turnover percentages and correlations easily.

---

## 7. Key Findings

1. **Overtime is the Largest Driver:**
   - Employees who work overtime have an attrition rate of **30.53%**, compared to only **10.44%** for those who do not work overtime. Working extra hours nearly triples the risk of leaving.

2. **Lower Salary Increases Resignations:**
   - Employees who left had a median monthly income of **$3,202**, compared to **$5,204** for those who stayed (a $2,000 difference per month).
   - Most departures happen in **Job Level 1 and Level 2** roles earning under $5,000 per month.

3. **High Attrition in Entry-Level Roles:**
   - **Sales Representatives** have the highest turnover rate across the company at **39.76%**.
   - **Laboratory Technicians (23.94%)** and **Human Resources roles (23.08%)** also experience higher-than-average attrition.
   - Senior roles like **Research Directors (2.50%)** and **Managers (4.90%)** have very low attrition.

4. **Early Career Vulnerability:**
   - Turnover is concentrated among employees with **0 to 3 years** of tenure at the company and within the **28 to 33 age range**.

5. **Work-Life Balance and Commute Distance:**
   - Employees rating their work-life balance as **1 (Bad)** have an attrition rate of **31.25%**, compared to 14%–17% for better ratings.
   - Employees who left traveled an average of **10.63 miles** compared to **8.92 miles** for those who stayed.

---

## 8. Business Recommendations

| Problem Identified | Recommended Action | Expected Business Result |
| :--- | :--- | :--- |
| **High Overtime Burnout** | Set a weekly limit on overtime and offer compensatory leave for extra hours worked. | Lowers burnout-related resignations, especially in technical and sales teams. |
| **Low Starting Salaries** | Review and benchmark entry salaries for Sales Representatives and Lab Technicians. Add small milestone bonuses at 1 and 2 years. | Helps retain early-career employees during the vulnerable 0–3 year window. |
| **Long Daily Commutes** | Offer 2 to 3 days of hybrid/remote work for employees living more than 10 miles away. | Reduces daily travel stress and improves work-life balance satisfaction. |
| **Role Stagnation** | Establish regular 1-on-1 career check-ins between managers and junior staff. | Improves morale and internal growth opportunities. |

---

## 9. Project Limitations
- The dataset represents a snapshot in time and does not include exit interview text or longitudinal tracking over several years.
- External factors such as local economic conditions, inflation, and competitor hiring offers are not recorded in the data.

---

## 10. How to Run the Notebook
1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/employee-attrition-workforce-analytics.git
   cd employee-attrition-workforce-analytics
   ```
2. Install required packages:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Open and run the notebook:
   ```bash
   jupyter notebook notebooks/employee_attrition_eda.ipynb
   ```