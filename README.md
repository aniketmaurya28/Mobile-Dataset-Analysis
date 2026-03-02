# 📱 Mobile Phones Market Analysis Using Python

> Exploratory data analysis of a mobile phones dataset — uncovering pricing patterns, brand dynamics, discount strategies, and consumer preferences through structured Python workflows.

---

## 📂 Dataset Overview

The dataset (`Mobiles_Dataset.xlsx`) contains listings of mobile phones with the following attributes:

| Column | Description |
|---|---|
| `Product Name` | Full name of the mobile device |
| `MRP` | Maximum Retail Price (original price) |
| `Selling_Price` | Discounted / actual selling price |
| `Stars` | Average star rating |
| `Rating` | Number of customer ratings |
| `Reviews` | Number of written reviews |
| `RAM (GB)` | RAM configuration |
| `Storage (GB)` | Internal storage capacity |
| `Camera` | Camera specifications |

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?logo=numpy)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

---

## 🔍 What This Project Covers

### 🧹 Part 1–2 · Data Loading & Cleaning
- Loaded Excel data using `pandas`
- Cleaned currency symbols (`₹`) and commas from price columns using string operations and `astype()` for type conversion
- Handled missing values — filled camera specs with `'Not specified'`, dropped null star ratings
- Removed duplicate records to ensure data integrity
- Renamed columns for better readability (`Actual price` → `MRP`, `Discount price` → `Selling_Price`)

### 🔎 Part 3 · Filtering & Selection
- Used `loc` and `iloc` for precise row/column selection
- Applied boolean indexing to find high-rated, budget-friendly phones (Stars > 4.5 & Price < ₹50,000)
- Used `.query()` for readable multi-condition filtering (e.g., Samsung phones above ₹70,000)
- Used `.where()` to conditionally mask price values

### ⚙️ Part 4 · Feature Engineering
- Extracted `Brand` from product names using string splitting
- Created a `Price_Category` column (`Budget` / `Mid-Range` / `Premium`) using `np.select()` based on star ratings
- Calculated `Discount_Percentage` = `((MRP - Selling_Price) / MRP) × 100`
- Computed mean and standard deviation of selling prices to understand price spread

### 📊 Part 5 · Grouping & Aggregation
- Grouped by `Brand` to compute mean, sum, and standard deviation of selling prices
- Used `.transform()` to add `Average_Brand_Price` as a new column without collapsing the DataFrame
- Built a **pivot table** — Stars by Brand × RAM — to spot which RAM configurations drive better ratings per brand
- Created a **crosstab** of Brand vs. Storage to understand product distribution

### 🔄 Part 6 · Reshaping & Combining
- Melted the DataFrame to compare MRP vs. Selling_Price in long format
- Split and re-concatenated the dataset to demonstrate `pd.concat()`
- Merged with a custom `country_df` to map brands to their countries of origin (Apple → USA, Samsung → South Korea, OnePlus → China)
- Used `.shift()` to create a `Previous_Price` column for row-by-row price comparison

### 📅 Part 7 · Time Series & NumPy
- Simulated launch dates using `pd.date_range()` and extracted `Year`, `Month_Name`, `Day_of_Week`
- Converted dates to periods (`'M'`) for monthly time-series grouping
- Converted price series to NumPy arrays and computed the **75th percentile** price point

### 💾 Part 8 · Export
- Exported the cleaned, feature-rich dataset to both `.csv` and `.xlsx` formats for downstream use

---

## 💡 Key Insights

- **Brand extraction** from raw product names enables brand-level benchmarking without a separate reference table.
- **Discount percentage engineering** reveals that high-MRP phones don't always offer the deepest discounts — mid-range phones often show aggressive pricing.
- **Pivot tables (Stars × RAM)** show that higher RAM configurations tend to correlate with better star ratings across most brands.
- **The 75th percentile price** (~computed via NumPy) provides a practical threshold for classifying "premium" vs. accessible segments.
- Phones with `Stars > 4.5` and `Selling_Price < ₹50,000` form a distinct "value-for-money" cluster worth tracking for consumer recommendations.

---

## 📁 Project Structure

```
📦 Mobiles-Analysis
 ┣ 📓 Mobiles_Analysis_Using_Python.ipynb   ← Main analysis notebook
 ┣ 📊 Mobiles_Dataset.xlsx                  ← Raw input data
 ┣ 📄 mobiles_cleaned_final.csv             ← Cleaned output (CSV)
 ┣ 📊 mobiles_cleaned_final.xlsx            ← Cleaned output (Excel)
 ┗ 📄 README.md
```

---

## ▶️ How to Run

```bash
# Clone the repository
git clone https://github.com/aniketmaurya28/mobiles-analysis.git
cd mobiles-analysis

# Install dependencies
pip install pandas numpy openpyxl

# Launch the notebook
jupyter notebook Mobiles_Analysis_Using_Python.ipynb
```

---

## 🧠 Skills Demonstrated

### 🐍 Python & Libraries
- **Pandas** — DataFrame manipulation, filtering, grouping, merging, reshaping, and aggregation
- **NumPy** — Array operations, percentile calculation, conditional column creation with `np.select()`
- **Jupyter Notebook** — Structured, reproducible analysis workflow across 8 logical parts

### 🧹 Data Wrangling
- Cleaning raw, inconsistently formatted data (currency symbols, commas, text-in-numeric fields)
- Type conversion (`astype()`) and regex-based string cleaning
- Handling missing values with context-aware strategies (fill vs. drop)
- Deduplication and data integrity checks

### 🔧 Feature Engineering
- Derived new columns: `Brand`, `Price_Category`, `Discount_Percentage`, `Average_Brand_Price`
- Segmented products into meaningful tiers (Budget / Mid-Range / Premium) using business logic
- Simulated time-series data and extracted date components (year, month, day of week)

### 📊 Data Analysis & Aggregation
- Multi-condition boolean filtering to identify value-for-money products
- GroupBy aggregations (mean, sum, std) for brand-level comparisons
- Pivot tables and crosstabs for multi-dimensional analysis (Brand × RAM × Stars)
- Used `.transform()` to enrich data without losing granularity

### 🔗 Data Combining & Reshaping
- `pd.concat()` for stacking DataFrames
- `df.merge()` for enriching data with external reference tables
- `df.melt()` for converting wide data to long format for comparison

### 💾 Data Export & Reproducibility
- Exported clean, analysis-ready datasets to both `.csv` and `.xlsx`
- Maintained clean, well-commented, section-based notebook structure

---

## 👤 Author

**Aniket Maurya**  
[![GitHub](https://img.shields.io/badge/GitHub-aniketmaurya28-181717?logo=github)](https://github.com/your-username)

---

*Feel free to ⭐ the repo if you found this useful!*
