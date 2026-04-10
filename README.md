# 🥃 Liquor Sales Dashboard — Dan Murphy's Sales Analysis

> **End-to-end data analytics project** combining Tableau visualisation with deep statistical analysis in R on Databricks — built to uncover revenue drivers, margin patterns, and sales trends across spirit categories, vendors, and counties.

---

## 📌 Project Overview

This project analyses **2,000 real liquor sales transactions** from a retail dataset to answer key business questions:

- Which spirit categories and vendors drive the most revenue?
- Do premium products significantly outperform standard ones?
- Are there seasonal sales patterns worth targeting?
- What factors statistically predict a high-value transaction?

The project delivers answers through **interactive dashboards** (Tableau) and **rigorous statistical testing** (R on Databricks).

---

## 🗂️ Repository Structure

```
Liquor-Sales-Dashboard/
│
├── Intro to Databricks - liquor sales 2000 rows.csv   # Raw dataset
├── DanMurphys_Liquor_Sales_R_Analysis.r               # Full R analysis script
├── Liquor Sales Data Analysis.Rmd                     # R Markdown report
├── Liquor Sales Data Analysis.ipynb                   # Jupyter/Databricks notebook
└── README.md                                          # This file
```

---

## 📊 Dataset

| Field | Detail |
|-------|--------|
| **Source** | Iowa Liquor Sales (Databricks Intro Dataset) |
| **Rows** | 2,000 transactions |
| **Columns** | 17 (date, store, county, category, vendor, item, price, quantity, total…) |
| **Date Range** | February 2014 – January 2015 |
| **Key Metrics** | Bottle price, quantity, total revenue, gross margin |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **R** | Statistical analysis, EDA, hypothesis testing |
| **Databricks** | Cloud notebook execution & scalable compute |
| **tidyverse** | Data wrangling and ggplot2 visualisations |
| **car / dunn.test** | ANOVA, Levene's test, post-hoc analysis |
| **corrplot / ggridges** | Correlation matrix, ridge density plots |
| **Tableau Public** | Interactive sales dashboard |
| **GitHub** | Version control & project showcase |

---

## 📈 Tableau Dashboard

The Tableau dashboard provides interactive views of:

- 📉 **Sales Over Time** — weekly revenue trend line with labels
- 🍾 **Total Bottles Sold** — by spirit category (bar chart)
- 🏭 **Total Vendor Revenue** — ranked vendor comparison
- 💰 **Total Sales $** — category-level revenue breakdown
- 🗺️ **County × Category Heatmap** — geographic sales distribution
- 🔗 **Vendor × Category Matrix** — cross-dimensional performance

🔗 **[View Live Dashboard on Tableau Public →]https://public.tableau.com/views/LiquorSalesDashboard_17755814981430/LiquorDashboard?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link**


---

## 🔬 R Analysis on Databricks

The R notebook (`DanMurphys_Liquor_Sales_R_Analysis.r`) is structured across **26 cells** covering:

### 1. Data Preparation
- Date parsing, type fixing, outlier removal
- Feature engineering: `margin_pct`, `spirit_type`, `is_premium`, `size_category`
- Missing value audit

### 2. Exploratory Data Analysis (EDA)
- Distribution of sale values (histogram, log-density, skewness/kurtosis)
- Revenue by spirit category
- Monthly and quarterly revenue trends
- Top 10 counties by revenue
- Gross margin analysis (boxplots + ridge plots)
- Vendor bubble chart
- Correlation matrix

### 3. Hypothesis Testing

| # | Test | Variables | Finding |
|---|------|-----------|---------|
| 1 | **Welch t-test** | Premium vs Standard → sale value | ✅ Premium significantly higher (p < 0.05) |
| 2 | **Welch ANOVA** | Spirit type → sale value | ✅ Significant difference across spirits |
| 3 | **Tukey HSD** | Pairwise spirit comparisons | Whiskey vs Vodka most distinct |
| 4 | **Two-Way ANOVA** | Spirit type × Premium tier | Significant interaction effect |
| 5 | **Chi-Square** | Spirit type ↔ bottle size | ✅ Strong association (Cramér's V > 0.3) |
| 6 | **Kruskal-Wallis + Dunn** | Margin % by bottle size | ✅ Significant margin differences |
| 7 | **Pearson Correlation** | Price ↔ quantity | Weak negative, significant |

### 4. Multiple Linear Regression
- **DV:** `log(total sale value)`
- **IVs:** bottle price, quantity, liter size, spirit type, premium status
- Reports R², adjusted R², F-statistic, AIC, and variable importance plot

---

## 💡 Key Business Insights

| Insight | Implication |
|---------|-------------|
| **Vodka** is #1 by volume | Maintain broad SKU range & competitive pricing |
| **Whiskey** drives highest revenue | Invest in premiumisation & curated ranges |
| **Polk County** accounts for ~38% of revenue | Priority geography for promotions |
| **Q4 seasonal peak** confirmed | Run targeted campaigns Oct–Dec |
| **Liqueurs command highest margins** | Upsell opportunity at checkout |
| **Premium products** have significantly higher sale values | Expand premium tier listings |
| **Diageo Americas** is the top vendor | Strong partnership; audit margin terms |

---

## ▶️ How to Run

### Option 1 — Databricks (Recommended)
1. Upload `liquor_sales_2000_rows.csv` to your DBFS: `dbfs:/FileStore/tables/`
2. Create a new **R notebook** in Databricks
3. Paste each cell from `DanMurphys_Liquor_Sales_R_Analysis.r`
4. Update the `read.csv` path in Cell 2 to `/dbfs/FileStore/tables/liquor_sales_2000_rows.csv`
5. Click **Run All**

### Option 2 — Local R / RStudio
```r
# Set working directory to repo root
setwd("path/to/Liquor-Sales-Dashboard")

# Install dependencies
install.packages(c("tidyverse","lubridate","scales","ggthemes","car",
                   "dunn.test","corrplot","knitr","broom","gridExtra",
                   "RColorBrewer","ggridges","moments"))

# Run the script
source("DanMurphys_Liquor_Sales_R_Analysis.r")
```

### Option 3 — R Markdown
Open `Liquor Sales Data Analysis.Rmd` in RStudio and click **Knit** to produce a full HTML report.

---

## 📸 Project Screenshots

| Tableau Dashboard | Databricks R Notebook |
|<img width="1472" height="713" alt="Screenshot 2026-04-11 044240" src="https://github.com/user-attachments/assets/f879a365-d51c-49cc-8b99-8258b3b3eff3" />
|:---------------------:|


---

## 👤 Author

**Neel Mehul Shah**
- 🌐 Portfolio: https://datascienceportfol.io/shahneel364
- 💼 LinkedIn: https://www.linkedin.com/in/neel-shah-654a1b27b/
- 🐙 GitHub: [@neel2444](https://github.com/neel2444)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

*Built with ❤️ using R, Databricks & Tableau*
