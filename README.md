# superstore-sales
 # 🛒 Superstore Sales Data Analysis

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

A complete end-to-end business data analysis project on a global superstore's sales transactions (2011–2014). The project includes a theoretical research report, exploratory data analysis (EDA) with statistical hypothesis testing, an interactive Power BI dashboard, and full documentation — all organized in this repository.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset Description](#-dataset-description)
- [Repository Structure](#-repository-structure)
- [Key Findings](#-key-findings)
- [Getting Started](#-getting-started)
- [Requirements](#-requirements)
- [How to Run](#-how-to-run)
- [Visualizations](#-visualizations)
- [Hypothesis Testing Results](#-hypothesis-testing-results)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Technologies Used](#-technologies-used)
- [Author](#-author)

---

## 📖 Project Overview

This project analyzes sales data from a fictional global superstore to extract meaningful business insights. The core objectives are:

- Understand **sales trends** across product categories, regions, and customer segments
- Identify **top-performing** and **loss-making** products and geographies
- Detect **seasonal patterns** and year-over-year growth
- Validate business hypotheses using **formal statistical tests**
- Present findings through an interactive **Power BI dashboard**

> **Note:** Component 4 (ML Predictive Modelling) has been excluded from this project.

---

## 📂 Dataset Description

| Attribute | Details |
|---|---|
| **File Name** | `SuperStore_Orders.csv` |
| **Source** | [Kaggle – Superstore Dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) |
| **Rows** | 51,290 (51,281 after deduplication) |
| **Columns** | 21 |
| **Time Period** | January 2011 – December 2014 |
| **Markets** | 7 (APAC, EU, US, LATAM, EMEA, Africa, Canada) |
| **Regions** | 13 global regions |

### Column Reference

| Column | Type | Description |
|---|---|---|
| `order_id` | String | Unique order identifier |
| `order_date` | Date | Date the order was placed |
| `ship_date` | Date | Date the order was shipped |
| `ship_mode` | String | Shipping method (Standard, First Class, etc.) |
| `customer_name` | String | Customer full name |
| `segment` | String | Customer segment (Consumer / Corporate / Home Office) |
| `region` | String | Geographic region |
| `market` | String | Global market |
| `category` | String | Product category (Furniture / Office Supplies / Technology) |
| `sub_category` | String | Product sub-category (17 types) |
| `sales` | Integer | Order sales value ($) |
| `quantity` | Integer | Units ordered |
| `discount` | Float | Discount applied (0.0 – 0.85) |
| `profit` | Float | Profit or loss on the order ($) |
| `shipping_cost` | Float | Cost of shipping ($) |
| `order_priority` | String | Priority level (Low / Medium / High / Critical) |
| `year` | Integer | Order year |

> ⚠️ **Data Notes:**
> - The `sales` column uses comma-separated thousands in some rows (e.g., `1,234`) — handled in preprocessing.
> - The `order_date` column contains two mixed formats: `M/D/YYYY` and `DD-MM-YYYY` — both parsed correctly.
> - 9 true duplicate rows (same order + product + values) were removed during cleaning.

---

## 🗂️ Repository Structure

```
superstore-sales-analysis/
│
├── data/
│   └── SuperStore_Orders.csv          # Raw dataset
│
├── notebooks/
│   └── SuperStore_EDA.ipynb           # Full EDA + Hypothesis Testing notebook
│
├── reports/
│   ├── Research_Report_Data_Analytics.docx   # Component 1 – Research Report
│   └── Action_Plan_Superstore.docx           # Component 2 – Action Plan
│
├── dashboard/
│   ├── SuperStore_Dashboard.pbix      # Power BI dashboard file
│   └── screenshots/                   # Dashboard screenshot images
│
├── figures/                           # All 14 EDA chart PNGs
│   ├── fig_distributions.png
│   ├── fig_category.png
│   ├── fig_subcategory.png
│   ├── fig_region.png
│   ├── fig_market.png
│   ├── fig_segment.png
│   ├── fig_heatmap_seg_cat.png
│   ├── fig_yearly_trend.png
│   ├── fig_monthly_trend.png
│   ├── fig_yearly_lines.png
│   ├── fig_quarterly.png
│   ├── fig_h1.png
│   ├── fig_h2.png
│   └── fig_h3.png
│
├── README.md                          # This file
└── requirements.txt                   # Python dependencies
```



## 💡 Key Findings

1. **Technology dominates profitability** — Technology is the highest-revenue and highest-profit category, with a significantly better profit margin than Furniture or Office Supplies.

2. **Tables and Bookcases are loss-makers** — Despite reasonable sales volumes, these two Furniture sub-categories generate negative total profit across all years, suggesting a pricing or discount problem.

3. **Q4 seasonality is consistent** — Sales peak every October–December across all four years, with Q4 accounting for the largest share of annual revenue. Inventory planning should align with this pattern.

4. **High discounts destroy profit** — Orders with a discount rate above 30% consistently generate negative average profit. Discount policy needs an immediate review; the Pearson correlation between discount and profit is r = −0.316 (p < 0.001).

5. **Steady year-over-year growth** — Total sales grew from ~$2.3M (2011) to ~$4.3M (2014), a near 87% increase over four years, with profit growing proportionally.

6. **Consumer segment leads in volume** — The Consumer segment accounts for ~51% of total sales, though Home Office shows the strongest average profit margin per order.

7. **Central region leads in sales** — Across the 13 global regions, Central and East are the top two in total sales; EMEA and Southeast Asia show the weakest profit margins.

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10 or higher
- Jupyter Notebook or JupyterLab
- Power BI Desktop (for Component 5 only — free from Microsoft)

### Clone the Repository

```bash
git clone https://github.com/<your-username>/superstore-sales-analysis.git
cd superstore-sales-analysis
```

---

## 📦 Requirements

Install all Python dependencies with:

```bash
pip install -r requirements.txt
```

**`requirements.txt`**
```
pandas>=1.5.0
numpy>=1.23.0
matplotlib>=3.6.0
seaborn>=0.12.0
scipy>=1.9.0
jupyter>=1.0.0
```

---

## ▶️ How to Run

### EDA Notebook

1. Place `SuperStore_Orders.csv` in the `data/` folder (or the same directory as the notebook).
2. Open the notebook:

```bash
jupyter notebook notebooks/SuperStore_EDA.ipynb
```

3. Run all cells from top to bottom with **Kernel → Restart & Run All**.

> The notebook handles all data cleaning automatically — no manual preprocessing needed.

### Power BI Dashboard

1. Open Power BI Desktop.
2. Go to **File → Open** and select `dashboard/SuperStore_Dashboard.pbix`.
3. If prompted, update the data source path to point to your local `SuperStore_Orders.csv`.
4. Click **Refresh** to reload the data.

---

## 📊 Visualizations

The EDA produces 14 charts, saved as PNG files in the `figures/` folder:

| Figure | Description |
|---|---|
| `fig_distributions.png` | Histogram of Sales and Profit distributions |
| `fig_category.png` | Bar + pie charts: Sales & Profit by Category |
| `fig_subcategory.png` | Horizontal bar charts: Sales & Profit by Sub-Category |
| `fig_region.png` | Bar charts: Sales & Profit across 13 regions |
| `fig_market.png` | Bar charts: Sales & Profit across 7 global markets |
| `fig_segment.png` | Bar + pie charts: Sales & Profit by Customer Segment |
| `fig_heatmap_seg_cat.png` | Heatmap: Profit by Segment × Category |
| `fig_yearly_trend.png` | Line chart: Annual Sales & Profit (2011–2014) |
| `fig_monthly_trend.png` | Dual-axis line: Average Monthly Sales & Profit |
| `fig_yearly_lines.png` | Multi-line: Monthly Sales by Year |
| `fig_quarterly.png` | Grouped bar: Quarterly Sales by Year |
| `fig_h1.png` | H1 test — Technology vs Office Supplies profit |
| `fig_h2.png` | H2 test — Consumer vs Corporate sales |
| `fig_h3.png` | H3 test — Discount vs Profit scatter + bucket chart |

---

## 🧪 Hypothesis Testing Results

All tests performed at **α = 0.05** significance level.

| Test | Hypothesis | Statistic | p-value | Result |
|---|---|---|---|---|
| **H1** | Technology profit per order > Office Supplies profit per order | t = 17.68 | < 0.0001 | ✅ Reject H₀ |
| **H2** | Consumer average sales ≠ Corporate average sales | t = −0.51 | 0.6128 | ❌ Fail to Reject H₀ |
| **H3** | Discount is negatively correlated with profit | r = −0.316 | < 0.0001 | ✅ Reject H₀ |

**Interpretation:**
- **H1:** Technology generates statistically significantly higher profit per order than Office Supplies. Prioritizing Technology in marketing and inventory is data-supported.
- **H2:** There is no statistically significant difference in average order value between Consumer and Corporate segments — both segments are comparable in per-order revenue.
- **H3:** Higher discount rates significantly reduce profitability. This is a critical business insight — discounts above 30% are confirmed loss-drivers.

---

## 📈 Power BI Dashboard

The dashboard (`dashboard/SuperStore_Dashboard.pbix`) provides an interactive view of all major EDA findings with the following features:

**Visuals included:**
- 📦 KPI Cards — Total Sales, Total Profit, Profit Margin %, Total Orders
- 📊 Bar Charts — Sales & Profit by Category, Sub-Category, Region, Segment
- 📈 Line Chart — Monthly and Annual Sales Trends
- 🥧 Pie / Donut Chart — Sales Share by Category and Segment

**Interactive filters:**
- 🔽 Region slicer
- 🔽 Product Category slicer
- 🔽 Year / Date range slicer

Screenshots are available in `dashboard/screenshots/`.

---

## 🛠️ Technologies Used

| Tool | Purpose |
|---|---|
| **Python 3.10** | Core programming language |
| **Pandas** | Data loading, cleaning, and aggregation |
| **NumPy** | Numerical computation |
| **Matplotlib** | Chart creation and customization |
| **Seaborn** | Statistical visualizations and heatmaps |
| **SciPy** | Hypothesis testing (t-tests, Pearson correlation) |
| **Jupyter Notebook** | Interactive analysis environment |
| **Power BI Desktop** | Interactive business intelligence dashboard |
| **GitHub** | Version control and project hosting |
| **python-docx** | Report and action plan document generation |


## 👤 Author  @satyamgupta8351 

**Superstore Sales Data Analysis Project**  
Academic Data Analytics Project — 2026

---

