# Global Tech Layoffs Analysis (SQL & Tableau)

An end-to-end data analysis and visual storytelling project investigating global tech workforce reductions from 2020 to 2023.



## 📊 Executive Dashboard Preview

![Global Tech Layoffs Dashboard](world_layoffs_analysis.png)

> **Note:** To interact with the full workbook locally, download `World_Layoffs_Analysis.twbx` from this repository and open it in Tableau Desktop or Tableau Reader.



## ❓ Business Questions Addressed
This project was designed to query the dataset and answer the following strategic questions regarding the tech market contraction:
* **Industry Impact:** Which industries experienced the largest workforce reductions?
* **Temporal Trends:** How did the volume of layoffs evolve month-over-month and year-over-year?
* **Geographic Distribution:** Which countries and regions were most severely affected?
* **Financial Correlation:** Does a company's funding total or investment stage relate to their likelihood or scale of layoffs?



## 💡 Key Quantified Insights
1. **Historical Peak:** Workforce reductions reached their absolute highest point in January 2023, with over **80,000 individual job losses** recorded in a single month.
2. **Sector Vulnerability:** The **Consumer and Retail sectors** absorbed the heaviest losses globally, accounting for over **80,000 combined layoffs**, signalling a massive contraction in consumer tech demand.
3. **Geographic Concentration:** The **United States** bore the overwhelming majority of the impact, representing roughly **65%** of all global tech layoffs recorded in the dataset.
4. **Corporate Giants:** Industry leaders (Amazon, Google, Meta, Microsoft) accounted for the sharpest spikes, collectively shedding roughly **50,000+ jobs** to lead the layoffs chart.
5. **Funding Stage Trend:** **Post-IPO** companies executed the largest volume of layoffs by a wide margin, prioritizing aggressive cost-cutting to satisfy public market pressures over the preservation of growth teams.
6. **Post-Pandemic Correction:** Layoffs surged by over **300%** between late Q3 2022 and Q1 2023, representing a severe correction to the aggressive over-hiring trends of the 2020–2021 period.



## 🛠️ Technical Execution & SQL Methodology

Raw data is inherently messy. To ensure the Tableau dashboard was accurate, a rigorous data cleaning and exploratory data analysis (EDA) pipeline was built in MySQL. 

* **Window Functions (`ROW_NUMBER()`):** Used to partition the data and systematically identify and filter out exact duplicate rows that would have artificially inflated the final layoff totals.
* **Common Table Expressions (CTEs):** Implemented to break down complex, multi-step queries (like calculating rolling totals and year-over-month changes) into readable, modular code blocks without altering the core database.
* **Self-Joins:** Utilized to intelligently populate missing categorical data (e.g., matching a company's known industry from one row to a row where its industry was incorrectly listed as `NULL`).
* **Data Imputation (`COALESCE` & `IS NULL`):** Applied to standardize missing geographic and financial fields, ensuring that Tableau could accurately group and map all 2,000+ records.
* **Date Parsing (`STR_TO_DATE`):** Essential for converting inconsistent string-based date entries into standard relational database formats so the time-series charts would render sequentially.



## 📁 Repository Structure
* `/World Layoffs (Data Cleaning).sql`: Scripts for deduplication, null imputation, and data type normalization.
* `/Exploratory Data Analysis.sql`: Queries for rolling totals, dense ranking, and multi-factor aggregations.
* `/World_Layoffs_Analysis.twbx`: Complete Tableau packaged workbook.
