Customer Shopping Behaviour Analysis
📌 Overview

This project demonstrates an end-to-end Data Analytics workflow using Excel, SQL (PostgreSQL), and Power BI. The objective was to analyze customer shopping behaviour, identify purchasing trends, and generate actionable business insights through data cleaning, SQL analysis, and interactive dashboards.

The project follows the complete analytics process—from raw data preparation to business reporting and presentation.

📊 Dataset

The dataset contains 3,900 customer shopping records with information about:

Customer demographics (Age, Gender, Location)
Product categories and items purchased
Purchase amount
Review ratings
Subscription status
Shipping type
Previous purchases
Discount and promo code usage
Purchase frequency

The data was cleaned and transformed before being used for analysis.

🛠️ Tools & Technologies
Microsoft Excel
PostgreSQL
Power BI
Gamma (Presentation)
GitHub

🚀 Project Workflow

1. Data Loading
Opened the raw dataset in Excel and set up a working copy for cleaning, keeping the original raw data untouched as a backup.
Did an initial pass with column filters and a Ctrl+End check to confirm the full extent of the data (3,900 rows × 18 columns).

2. Data Quality Checks
Reviewed every categorical column via filters to check for inconsistent values (spacing, casing, typos) — none found.
Checked for exact duplicate rows using a TEXTJOIN-based row fingerprint combined with COUNTIF — confirmed 0 duplicate rows.
Used COUNTBLANK across all columns to confirm the dataset's 37 missing values were isolated entirely to the Review Rating column.

3. Data Cleaning
Filled the 37 missing values in the Review Rating column using the median rating for each product category, calculated with an array-based MEDIAN(IF(...)) formula and matched to each row using XLOOKUP.
Renamed all column headers to a consistent lowercase, snake_case format.
Engineered two new features:
  - age_group — created by splitting Age into four equal-sized quartiles (QUARTILE function) and labelling them Young Adult, Adult, Middle-Aged, and Aged.
  - purchase_frequency_days — converted the Frequency of Purchases text values (e.g. Weekly, Monthly) into numerical day counts using an XLOOKUP against a small mapping table.
Verified that promo_code_used duplicated discount_applied in every row (using EXACT + COUNTIF) and removed the redundant column.
Converted all formula columns to static values before exporting, to keep the cleaned dataset stable.

4. Exploratory PivotTable Analysis
Built a PivotTable summarising total and average purchase amount by category.
Found that average order value is fairly consistent across categories (~$57–$60), meaning Clothing's higher total revenue is driven mainly by purchase volume rather than a higher spend per transaction — an insight that fed into the business recommendations.

5. PostgreSQL Analysis
Exported the cleaned dataset as a CSV and loaded it into a PostgreSQL customer table.
Wrote SQL queries to answer business questions, including:
Revenue by gender
Subscriber vs. non-subscriber analysis
Top-rated products
Shipping comparison
Customer segmentation
Revenue by age group
Discount analysis
Product performance

6. Power BI Dashboard

Created an interactive dashboard featuring:

Total Customers
Average Purchase Amount
Average Review Rating
Revenue by Category
Sales by Category
Revenue by Age Group
Sales by Age Group
Subscription Status Distribution
Interactive slicers for Gender, Category, Subscription Status, and Shipping Type

7. Report & Presentation
Prepared a project report summarizing the analysis and business insights.
Created a presentation using Gamma to communicate findings in a clear and visually engaging format.

📈 Dashboard Highlights

The Power BI dashboard enables users to:

Monitor key business KPIs
Analyze customer purchasing behaviour
Compare revenue across product categories
Explore sales by age group
Filter results interactively using multiple slicers
Support business decision-making with visual insights

📌 Key Results
Identified the highest-performing product categories.
Compared purchasing behaviour between subscribers and non-subscribers.
Segmented customers based on purchase history.
Analyzed customer spending by age group and gender.
Evaluated the impact of discounts and shipping methods on customer purchases.
Found that average order value is consistent across categories, meaning revenue growth is more about purchase volume than category-specific pricing.
Built an interactive dashboard to support data-driven business decisions.

▶️ How to Run
Clone this repository.

Open the Excel workbook and review/run through the data cleaning steps (Data Quality Checks → Missing Value Handling → Feature Engineering → Redundancy Check).
Export the cleaned data as a CSV.
Load the cleaned CSV into PostgreSQL (e.g. via pgAdmin's import feature).
Execute the SQL queries to generate business insights.
Open the Power BI (.pbix) file to explore the interactive dashboard.
Review the project report and Gamma presentation for a summary of the findings.

📂 Project Structure
Customer-Shopping-Behaviour-Analysis/
│
├── Dataset/
│   └── customer_shopping_data.csv
│
├── Excel/
│   └── customer_shopping_behavior_cleaning.xlsx
│
├── SQL/
│   └── customer_analysis_queries.sql
│
├── PowerBI/
│   └── Customer_Behaviour_Dashboard.pbix
│
├── Report/
│   └── Customer_Shopping_Behaviour_Report.pdf
│
├── Presentation/
│   └── Customer_Shopping_Behaviour_Presentation.pdf
│
└── README.md

👩‍💻 Author

Shabna Salim

Tools Used: Excel | PostgreSQL | Power BI | SQL | Gamma

