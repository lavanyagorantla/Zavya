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
