Markdown
# E-Commerce Sales & Customer Behavior Analysis

An end-to-end Exploratory Data Analysis (EDA) of over 540,000 international transaction records from a UK-based online retail merchant. This project audits and cleans administrative noise, models purchasing distributions, evaluates peak commercial schedules, and derives recommendations around wholesale retention and international fulfillment.

---

## 📌 Executive Summary & Key Metrics

* **Analyzed Scope:** 541,909 raw records cleaned down to 522,710 valid commercial transactions across 38 global markets.
* **Pareto Concentration:** The top **10% of customers generate 61.39% of total revenue**, and the top **20% generate 74.59%**, showing heavy reliance on wholesale B2B accounts.
* **Wholesale Anomaly in the Netherlands:** While Germany and France order at modest quantities per line (median: 10–12 units), Dutch accounts order at a median of **72 units per line item**, driving £283.9k in sales.
* **Q4 Seasonality Apex:** Monthly revenue surges 185% from August (£724k) to its November peak of **£1.453M**, with monthly order count doubling from ~1,250 to over 2,750 orders.
* **Operational Churn Baseline:** An average **cancellation rate of 15.02%** persists across operating months, highlighting regular out-of-stock and cart-adjustment friction.

---

## 📁 Repository Structure

```text
ecommerce_retail_eda/
├── data/
│   ├── raw/                       # Original UCI dataset (Online Retail.xlsx / CSV)
│   └── processed/                 # online_retail_cleaned.csv.gz, sample files
├── notebooks/
│   └── 01_ecommerce_eda.ipynb     # Full data cleaning, profiling & visual EDA
├── reports/
│   ├── figures/                   # High-resolution chart exports (PNG format)
│   ├── eda_report.pdf             # Written business & analytical report
│   └── presentation_deck.pdf      # 5-8 slide executive presentation deck
├── requirements.txt               # Dependencies (pandas, numpy, matplotlib, seaborn)
└── README.md                      # Project documentation & summary
🛠️ Data Audit & Cleaning Pipeline
Deduplication: Identified and removed 5,268 exact duplicate rows (0.97% of raw entries).

Administrative Noise Removal: Filtered over 2,600 service/adjustment codes (POST, DOT, M, D, BANK CHARGES, AMAZONFEE, CRUK, S) and inventory damage notes (damages, thrown away, check).

Cancellations & Inventory Segregation: Separated 10,587 cancellation records (InvoiceNo starting with 'C' or Quantity < 0) into a dedicated churn dataframe to avoid distorting gross retail sales.

Feature Engineering:

Line Spend: TotalPrice = Quantity * UnitPrice

Temporal Dimensions: YearMonth, Month, DayOfWeek, Hour

Customer Profile: Flagged guest checkouts vs. registered buyers (Has_CustomerID).

📊 Key Visualizations & Findings
1. Unit Economics & Distribution Profiles
The catalog features low-cost items: median unit price is £2.08, and median line spend is £9.90.

Order quantities peak at standard packaging units (6, 12, 24, and 36 units), demonstrating wholesale demand patterns.

2. Segment Spreads & Market Comparison
The Netherlands Outlier: Order quantities in the Netherlands dwarf domestic and neighboring European orders (median: 72 units vs. 10–12 across France/Germany).

Weekly Cadence: Spending builds during the week to a peak on Thursday (£10.95 line median); zero Saturday transactions confirm a 6-day dispatch cycle.

Guest Account Margins: Unregistered buyers purchase higher-priced items (median £3.29) than registered trade clients (median £1.95).

3. Commercial Drivers & Operational Rhythms
Top Products: Decorative centerpiece items (REGENCY CAKESTAND 3 TIER at £174.1k; WHITE HANGING HEART T-LIGHT HOLDER at £106.2k) generate the bulk of revenue, while volume leaders are sub-£1 party favors.

Operating Hours: Bimodal surge during business hours: peak transactions land precisely at 12:00 PM (75.7k orders) and 3:00 PM (75.3k orders).

4. Bivariate Elasticity & Multi-Collinearity
Revenue is volume-driven (r = 0.914 between Quantity and TotalPrice), with negligible linear dependence on unit price (r = 0.071).

Price elasticity ceiling: orders over 100 units per line occur almost exclusively for items priced under £5.00.

5. Seasonality, Returns & Customer Pareto Curve
Q4 Holiday Surge: Revenue reaches £1.453M in November 2011, double the monthly summer volume.

Pareto Concentration: The top 20% of buyers generate 74.6% of company revenue.

💼 Business Recommendations
High-Value B2B Retention Programs: Implement dedicated account managers and tiered volume pricing for the top 20% wholesale accounts that generate ~75% of sales.

Benelux Logistics Hub: Partner with a 3PL fulfillment warehouse in the Netherlands/Belgium to service high-volume Dutch and German bulk orders with reduced cross-border transit times.

Q4 Inventory Pre-Stocking: Issue purchase orders for top decorative centerpieces (REGENCY CAKESTAND, T-LIGHT HOLDER) by July/August to prevent stockouts during the autumn and holiday rush.

Checkout & Real-Time Stock Audits: Implement real-time stock validation at checkout to reduce the baseline 15% cancellation rate below 8%.

Staffing Optimization: Schedule warehouse picking and dispatch teams around the 10:00 AM – 3:00 PM order surge.

⚙️ Setup & Reproduction
Bash
# Clone the repository
git clone [https://github.com/](https://github.com/)<your-username>/ecommerce_retail_eda.git
cd ecommerce_retail_eda

# Create and activate virtual environment
python -m venv eda_env
source eda_env/bin/activate  # On Windows: eda_env\Scripts\activate

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Launch the notebook
jupyter notebook notebooks/01_ecommerce_eda.ipynb
📝 Resume Project Bullets
E-Commerce Sales & Customer Behavior Analysis | Python, Pandas, Seaborn

Profiled and cleaned 540K+ international transactions, eliminating 5.2K duplicates, isolating 10.5K cancellations, and filtering administrative inventory charges.

Identified peak seasonality patterns and customer spend concentration, demonstrating that the top 20% of B2B accounts drove 74.6% of company revenue.

Formulated inventory and international logistics strategies (including dedicated Benelux 3PL fulfillment) to cut stockouts during a 185% Q4 seasonal surge.