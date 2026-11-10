# Shop Easy Marketing Analytics: Fixing the Conversion Slump

## The Challenge
Our marketing team noticed a worrying drop in conversions during late 2024. Despite steady traffic, visitors weren't buying. We had a massive collection of raw data—customer journey logs, product specs, and thousands of unstructured customer reviews—but no clear answers on why people were dropping off or how to fix it.

This project builds a complete analytics pipeline to clean that raw data, process customer feedback, and build an executive dashboard to pinpoint exactly where the funnel is broken.

---

## What I Built (The Architecture)
Instead of jumping straight into charts, I built this project sequentially across the entire data lifecycle:
1. **Data Infrastructure (SQL):** Cleaned, filtered, and structured messy transactional logs into production-ready dimension and fact tables.
2. **Sentiment Engine (Python):** Wrote a script to analyze text reviews, turning unstructured feedback into clear, numeric satisfaction scores.
3. **BI & Visualization (Power BI):** Designed an interactive dashboard for stakeholders to track conversion metrics, customer sentiment, and marketing ROI.

---

## Technical Deep Dive

### 1. SQL Transformations & Data Cleaning
The raw data was filled with duplicates, missing values, and unformatted dates. I used SQL Server to build a clean relational schema.
* **Key Steps:**
  * Created a unified `Product Dimension` table with cleaned pricing tiers.
  * Formatted and joined web traffic data into a `Customer Journey Fact` table.
  * Extracted and structured a dedicated `Customer Reviews` table for text analytics.
  * Used window functions and `COALESCE` to handle missing interaction lengths and drop-offs.

*📂 Check out the scripts in the `/SQL_Scripts/` folder.*

### 2. Sentiment Analysis with Python
Customer reviews held the "why" behind the conversion drop, but reading thousands of comments manually was impossible. 
* **Key Steps:**
  * Loaded the SQL review table into Python using `pandas`.
  * Used the `NLTK VADER` sentiment analyzer to score reviews as Positive, Neutral, or Negative.
  * Grouped the results by product categories to identify exactly which items were driving customer frustration.
  * Exported the enriched data back into a clean structure for dashboard ingestion.

*📂 View the Python scripts in the `/Python_Notebooks/` folder.*

### 3. Power BI Dashboard & Storytelling
The final step was transforming our clean tables into data stakeholders could actually use. I built an interactive dashboard centered around our core business goals.
* **Key Features:**
  * **Overview Page:** Tracked high-level KPIs like total traffic, conversion rates, and revenue trend lines.
  * **Funnel Analysis:** Mapped the user journey step-by-step to show exactly where users abandon their carts.
  * **Sentiment Tracker:** Correlated product review scores directly with sales drops, proving that a specific quality-control issue in Q3 directly caused the October conversion dip.

*📂 Grab the dashboard file in the `/PowerBI_Dashboards/` folder.*

---

## Key Business Takeaways
* **The Culprit:** The conversion rate dipped from **8.4% down to 5.1%** in October. By combining web traffic with python sentiment analysis, we found this matched a spike in negative reviews regarding product sizing issues in our top clothing category.
* **The Action:** Spotlighting this issue allowed the inventory team to update sizing charts, while the marketing team shifted budget toward higher-rated product lines.
* **The Impact:** Conversions began stabilizing by late November, rebounding back toward **7.8%** by mid-December.

---

## How to Explore this Project
1. **Database:** Look at the `.sql` files to see how the tables were designed and cleaned.
2. **Text Processing:** Run the Jupyter Notebook in the Python directory to see the VADER analyzer in action.
3. **Insights:** Open the `.pbix` file in Power BI Desktop to interact with the final executive reports.
