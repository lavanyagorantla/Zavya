# Zavya
Business analytics case study for Zavya, a D2C Indian fine-jewellery brand.  we perform data cleaning, exploratory analysis, KPI development, and dashboard creation in Looker Studio.The goal: demonstrate end-to-end analytics workflow from raw data to actionable insights across Growth, Product, Operations, and Marketing.
. Objectives
Growth: Identify channels and campaigns driving highest revenue.

Product: Find best-selling categories and price-performance.

Operations: Track returns, discount effectiveness, order volumes.

Marketing: Attribute revenue to campaigns & measure conversion funnels.

3. Tech Stack
Python: pandas, numpy, matplotlib, seaborn

SQL: BigQuery (parameterised queries)

Looker Studio: KPI & executive dashboards

Amplitude: Event-level behavioral analytics

Google Sheets/Excel: ad-hoc exploration & data cleaning

4. Data Sources
zavya_dataset_clean.csv: cleaned synthetic transactional dataset.

data_dictionary.csv: field definitions & types.

tracking_plan.xlsx: analytics tracking events & properties.

5. Steps in Analysis
Data Cleaning (remove nulls, parse dates, create derived metrics like Revenue_After_Discount).

Exploratory Data Analysis (top products, channels, regions, campaigns).

Feature Engineering (RFM, LTV, discount bins, repeat purchase flag).

KPI Development (Revenue, AOV, Return %, Channel Share).

SQL Queries for BigQuery analytics.

Looker Studio Dashboard (KPIs, trends, distribution charts).

Amplitude Event Setup (customer actions, funnel tracking).

Recommendations (growth, product, ops, marketing).

6. Folder Contents
notebooks/: Jupyter notebooks with data cleaning, analysis, and feature engineering.

sql/: Parameterised queries for BigQuery.

dashboards/: Screenshots + links to interactive dashboards.

slides/: 1-page summaries for executives & LinkedIn portfolio.

data_dictionary.csv: Column names, descriptions, and example values.

tracking_plan.xlsx: Event/property mapping for Amplitude/GA4.

validation_checks.md: QA checklist and data validation results.

How to Run Locally
bash
Copy
Edit
# Clone the repository
git clone https://github.com/<your-username>/zavya-business-analytics.git
cd zavya-business-analytics

# Install dependencies
pip install -r requirements.txt

# Open notebooks
jupyter notebook
Key Insights
Website channel drives the majority of revenue (high ROI potential).

Silver Jewellery dominates product sales (~60% revenue share).

Discount % shows minimal variation — opportunity for A/B testing.

Return rate is ~7.7% — higher in certain product categories.
Dashboard Previews
Looker Studio:
https://lookerstudio.google.com/u/0/reporting/c91360b0-d44b-41aa-80f5-76c5bb73e24f/page/kN4TF/edit

tracking_plan (key columns)
Event Name	Description	Properties	Owner	Priority
Product Viewed	User views product page	Product_ID, Category	Marketing	High
Add to Cart	User adds product to cart	Product_ID, Price	Marketing	High
Purchase Completed	Successful order placed	Order_ID, Revenue	Ops	High
Return Initiated	User initiates return	Order_ID, Reason	Ops	Medium
Campaign Clicked	User clicks campaign ad link	Campaign_ID	Marketing	Medium

Upload zavya_dataset_clean to Google Drive → open with Google Sheets.

Ensure header row is clean, Order_Date is parsed as a Date, numeric columns (Unit_Price, Revenue_After_Discount, Units_Sold, Discount_%) are numbers.

In Looker Studio: Create → Data Source → Google Sheets → select sheet → Add to report.

In the data source editor, set Order_Date type → Date; set currency fields to Number (Currency formatting applied in charts).
Data modeling — fields to create in the Looker Studio data source
Create these calculated fields in the data source (or precompute in BigQuery if you prefer).

Metrics (calculated fields)

Orders = COUNT_DISTINCT(Order_ID)

Total_Revenue = SUM(Revenue_After_Discount) (or use existing column)

AOV = SUM(Revenue_After_Discount) / COUNT_DISTINCT(Order_ID)

Units_per_Order = SUM(Units_Sold) / COUNT_DISTINCT(Order_ID)

Return_Rate = SUM(Return_Flag) / COUNT_DISTINCT(Order_ID)

Avg_Discount_Pct = AVG(Discount_%)

Active_Customers = COUNT_DISTINCT(Customer_ID)

Looker Studio steps (copy-paste friendly)
Add a chart → Configure:

Scorecard (Total Revenue)

Metric: Total_Revenue (type: Currency)

Comparison date range: Previous period → toggle on.

Style: big, bold, center.

Time Series (Revenue)

Chart: Time series

Dimension: Order_Date

Metric: Total_Revenue

Break down dimension (optional): Channel (series) — pick max 4 channels.

Date range default: Auto (report-level control).

Add smoothing: use rolling average option if available.

Bar Chart (Revenue by Channel)

Chart: Bar chart

Dimension: Channel

Metric: Total_Revenue (and add Orders as second metric)

Sort by: Total_Revenue descending

Table (Top SKUs)

Dimensions: SKU, Product_Category

Metrics: Orders, Total_Revenue, Return_Rate, Avg_Discount_Pct

Add conditional formatting for Return_Rate > 10% highlight red.

Top insights:

Website accounts for 62% revenue; Instagram drives higher AOV but fewer orders.

Discounting increases conversion but reduces AOV; 11–20% bucket has highest conversion rates.

Top 10% customers (by LTV) deliver 40% of revenue — prioritize retention.
Recommended actions (3):

Run targeted retention program for top LTV cohort (email + SMS).

Test non-discounted bundles to preserve AOV.

Improve product page UX on Instagram-linked landing pages.
Expected impact: 5–8% incremental revenue in 3 months if top customers’ repeat rate increases by 10%.
Artifacts: Link to dashboard + SQL + notebook.
Steps in Analysis
Data Cleaning (remove nulls, parse dates, create derived metrics like Revenue_After_Discount).

Exploratory Data Analysis (top products, channels, regions, campaigns).

Feature Engineering (RFM, LTV, discount bins, repeat purchase flag).

KPI Development (Revenue, AOV, Return %, Channel Share).

SQL Queries for BigQuery analytics.

Looker Studio Dashboard (KPIs, trends, distribution charts).

Amplitude Event Setup (customer actions, funnel tracking).

Recommendations (growth, product, ops, marketing).
