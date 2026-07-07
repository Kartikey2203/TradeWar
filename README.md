# 🌐 TradeWar — US–China Trade & Tariff Analytics Dashboard

> **A multi-page Power BI dashboard analyzing the economic impact of the US–China trade war on global trade flows, tariff rates, and sector-wise commodity performance (2017–2025).**

---

## 📌 Project Overview

The **TradeWar Dashboard** is a data analytics project that tracks and visualizes the evolving US–China trade relationship through quantitative analysis of bilateral trade flows, tariff escalations, and sector-level economic impact. It leverages UN Comtrade data to produce actionable business intelligence across three interconnected Power BI dashboard pages.

The project aims to answer key questions:
- How have total trade volumes between the US and China shifted across 2017–2025?
- Which sectors suffered the most from tariff escalation?
- What is the tariff revenue generated, and how does it break down by sector and year?
- Which commodity categories dominate trade flows and face the highest average tariff burdens?

---

## 📊 Dashboard Pages

### Page 1 — Trade Overview & Tariff Trends

> *The entry point — a macro-level view of overall trade health and tariff evolution.*

| KPI | Value |
|-----|-------|
| Total Trade Value | **$1.71 Trillion** |
| Total Imports | **$1.29 Trillion** |
| Total Exports | **$421.30 Billion** |
| Average Tariff Rate | **21.30%** |
| Tariff Revenue Generated | **$359.27 Billion** |

**Visuals included:**
- 📈 **Total Trade by Year** (Line Chart) — Shows the sharp trade decline post-2022, bottoming out near $100bn in 2024 before a modest recovery.
- 📈 **Average Tariff Rate by Year** (Line Chart) — Illustrates the surge in tariffs from near 0% (pre-2018) to ~30% by 2025, reflecting escalating trade war phases.
- 🍩 **Total Imports by Year** (Donut Chart) — Yearly breakdown of import share, with 2018 ($164.90bn, 12.79%) and 2025 ($138.07bn, 10.71%) as notable points.
- 🍩 **Total Exports by Year** (Donut Chart) — 2025 ($62.65bn, 14.87%) leads exports, alongside 2020 ($56.39bn, 13.39%).
- 🍩 **Tariff Revenue by Year** (Donut Chart) — 2025 ($51.76bn, 14.41%) and 2024 ($50.94bn, 14.18%) represent the peak tariff revenue years.

---

### Page 2 — Sector-Wise Trade Impact Analysis

> *A deep dive into how individual sectors were hit by the trade war.*

| KPI | Value |
|-----|-------|
| Highest Revenue Sector | **Technology** |
| Max Tariff Rate | **25.00%** |
| Least Affected Sector | **Technology** |
| Most Affected Sector | **Agriculture** |

**Visuals included:**
- 📊 **Total Trade by Sector** (Bar Chart) — Technology dominates at ~$1.0T, followed by Automobile (~$0.2T) and Agriculture. Healthcare is the smallest sector.
- 📊 **Tariff Revenue by Sector** (Bar Chart) — Technology generates the highest tariff revenue (~$0.2T), while Chemicals and Critical Minerals generate the least.
- 📊 **Average Tariff Rate by Sector** (Bar Chart) — **Semiconductors** face the highest average tariff rate (~25%), followed by Automobile and Chemicals.
- 📊 **Trade Before Tariff by Sector** (Bar Chart) — Technology was the largest pre-tariff sector (>100bn).
- 📊 **Trade After Tariff by Sector** (Bar Chart) — Technology retains dominance post-tariff, though volume declines.
- 🔢 **Impact % by Sector** (Diverging Bar Chart) — Critical Minerals show the highest positive impact (~+1%), while Technology shows slight negative impact. Healthcare and Consumer Electronics show moderate negative impact.

---

### Page 3 — Category & Commodity Analysis

> *Granular view of HS Code-level commodity performance and cross-year category trends.*

| KPI | Value |
|-----|-------|
| Count of HS Codes | **20** |
| First Commodity (Export) | **Wheat and Meslin** |
| First Commodity (Import) | **Motor Cars** |

**Visuals included:**
- 🟦 **Total Trade by Sector** (Treemap) — Technology leads at **$950bn**, followed by Automobile ($181.37bn), Agriculture ($131.9bn), Semiconductors ($111.0bn), Energy ($73.3bn), and Electronics ($81.14bn).
- 📊 **Total Trade by Category** (Horizontal Bar Chart) — **Telecommunication Equipment** is the top category, followed by Computers & Data Processing and Vehicle Parts & Accessories. Soybeans rank 4th as a major agricultural commodity.
- 📊 **Average Tariff Rate by Sector** (Horizontal Bar Chart) — Semiconductors face the highest average tariff (~30%), followed by Automobile and Chemicals (~20–25%).
- 📈 **Trade Value by Year and Sector** (Stacked Bar Chart) — Shows year-on-year sector contribution from 2018–2025; Technology (blue) consistently dominates.
- 🔘 **Year Filter Slicer** — Allows filtering all visuals by individual years: 2017–2025.
- 🔀 **Trade Flow Filter** — Toggle between Export and Import flows.

---

## 🗂️ Project Structure

```
TradeWar/
│
├── 📁 data/
│   ├── 📁 raw/                          # Original source data
│   │   ├── merge-csv.com__6a45176537aa7.csv   # Merged raw Comtrade export
│   │   └── eda_new.ipynb                      # Raw data exploration notebook
│   │
│   └── 📁 clean/                        # Processed & analysis-ready data
│       └── trade_total_clean.csv             # Final cleaned dataset used in dashboard
│
├── 📁 notebook/
│   └── eda.ipynb                        # Main EDA Jupyter Notebook
│
├── 📁 dashboard/
│   ├── Trade_war.pbix                   # Power BI dashboard file
│   ├── Screenshot 2026-07-07 215639.png # Page 1: Trade Overview & Tariff Trends
│   ├── Screenshot 2026-07-07 215715.png # Page 2: Sector-Wise Trade Impact Analysis
│   └── Screenshot 2026-07-07 215815.png # Page 3: Category & Commodity Analysis
│
└── README.md
```

---

## 🔬 Data Source

| Field | Details |
|-------|---------|
| **Source** | [UN Comtrade Plus — Trade Flow Data](https://comtradeplus.un.org/TradeFlow) |
| **Reporter Countries** | United States, China |
| **Trade Flow** | Export & Import |
| **Time Range** | 2017 – 2025 |
| **Classification** | HS (Harmonized System) Commodity Codes |
| **Format** | CSV |
| **Key Fields** | `Trade_Value_USD`, `Tariff_Rate (%)`, `HS_Code`, `Sector`, `Category`, `Trade_Flow`, `Year` |

> The raw data was downloaded from the UN Comtrade Plus platform and merged using [merge-csv.com](https://merge-csv.com). It was subsequently cleaned and enriched with sector/category labels and tariff rates using Python (Pandas) in the Jupyter notebooks.

---

## 🧹 Data Processing Pipeline

```
UN Comtrade API / Export
         │
         ▼
  Raw CSV files (data/raw/)
         │
         ▼
  Data Merging & Cleaning
  (Python / Pandas — eda_new.ipynb)
    • Handle missing values
    • Standardize HS code descriptions
    • Assign Sector & Category labels
    • Calculate Tariff Revenue = Trade_Value × Tariff_Rate
    • Filter for US–China bilateral flows only
         │
         ▼
  Cleaned Dataset (data/clean/trade_total_clean.csv)
         │
         ▼
  Power BI Dashboard (dashboard/Trade_war.pbix)
    • DAX measures for KPIs
    • Custom theme (dark mode)
    • Multi-page navigation
    • Interactive slicers (Year, Trade Flow)
```

---

## 🧠 Key Insights & Findings

### 📉 Trade Volume Decline
- Total US–China trade peaked around **2021–2022** and then sharply declined to ~**$100bn** by **2024**, reflecting the full impact of sustained tariff escalations.
- Trade began a modest recovery in **2025**, suggesting potential policy shifts or trade rerouting effects.

### 📈 Tariff Escalation
- Average tariff rates surged from near **0% (pre-2018)** to approximately **30% by 2025**, directly correlating with the phased imposition of Section 301 tariffs.
- **Semiconductors** face the highest average tariff burden (~25–30%), reflecting strategic technology decoupling efforts.

### 💰 Revenue Generation
- Despite reduced trade volume, tariff revenue **peaked in 2024–2025** ($50–52bn/year), suggesting high tariffs are yielding more revenue even on lower trade volumes.
- **Technology** generates the lion's share of tariff revenue (~$0.2T) due to the massive trade volume even after reductions.

### 🌾 Sector Impact Asymmetry
- **Agriculture** is the **most affected sector** — US agricultural exports (particularly soybeans) to China fell dramatically.
- **Technology** is paradoxically the **least affected** in terms of proportional impact, as it retains dominance despite tariffs.
- **Critical Minerals** show a **positive impact** (~+1%), likely due to strategic stockpiling or supply chain diversification.

### 📦 Top Commodities
- **Telecommunication Equipment** and **Computers & Data Processing** are the largest trade categories, underscoring the technology-centric nature of US–China trade.
- **Soybeans** remain a top agricultural commodity, reflecting China's food security dependency on US agricultural imports.
- **Motor Cars** are the top import commodity, with **Wheat and Meslin** leading exports.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Power BI Desktop** | Dashboard design, DAX measures, interactive visuals |
| **Python (Pandas, NumPy)** | Data cleaning, merging, transformation |
| **Jupyter Notebook** | Exploratory Data Analysis (EDA) |
| **UN Comtrade Plus** | Primary data source |
| **merge-csv.com** | CSV file merging utility |
| **Git** | Version control |

---

## 🚀 Getting Started

### Prerequisites
- **Power BI Desktop** (latest version recommended) — [Download here](https://powerbi.microsoft.com/desktop/)
- **Python 3.8+** with `pandas`, `numpy`, `matplotlib`, `seaborn`
- **Jupyter Notebook** or **JupyterLab**

### 1. Clone the Repository
```bash
git clone https://github.com/Kartikey2203/TradeWar.git
cd TradeWar
```

### 2. Install Python Dependencies
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Explore the Data (Optional)
```bash
cd notebook
jupyter notebook eda.ipynb
```

### 4. Open the Dashboard
1. Launch **Power BI Desktop**
2. Open `dashboard/Trade_war.pbix`
3. The dashboard will load with all three pages and pre-connected data

### 5. Refresh Data (Optional)
To update with fresh Comtrade data:
1. Download new export from [UN Comtrade Plus](https://comtradeplus.un.org/TradeFlow)
2. Run the cleaning notebook (`data/raw/eda_new.ipynb`)
3. Replace `data/clean/trade_total_clean.csv`
4. Refresh the Power BI data source

---

## 📸 Dashboard Screenshots

### Page 1 — Trade Overview & Tariff Trends
![Trade Overview & Tariff Trends](dashboard/Screenshot%202026-07-07%20215639.png)

### Page 2 — Sector-Wise Trade Impact Analysis
![Sector-Wise Trade Impact Analysis](dashboard/Screenshot%202026-07-07%20215715.png)

### Page 3 — Category & Commodity Analysis
![Category & Commodity Analysis](dashboard/Screenshot%202026-07-07%20215815.png)

---

## 📋 Dataset Schema

The cleaned dataset (`trade_total_clean.csv`) contains the following key columns:

| Column | Type | Description |
|--------|------|-------------|
| `Year` | Integer | Trade year (2017–2025) |
| `Trade_Flow` | String | `Export` or `Import` |
| `HS_Code` | String | Harmonized System commodity code |
| `Category` | String | Human-readable commodity category |
| `Sector` | String | Broad economic sector |
| `Trade_Value_USD` | Float | Trade value in US Dollars |
| `Tariff_Rate (%)` | Float | Applied tariff rate percentage |
| `Tariff_Revenue` | Float | Calculated: `Trade_Value_USD × Tariff_Rate / 100` |

---

## ⚠️ Limitations & Caveats

- **Tariff Rate Approximation**: Tariff rates used are simplified averages by HS code category; actual applied rates may vary due to exclusions, retaliatory tariffs, and trade agreements.
- **Data Coverage**: UN Comtrade data may have reporting lags or gaps for certain commodity categories or years.
- **Bilateral Focus**: This analysis focuses exclusively on **US–China** bilateral trade. Third-country trade diversion effects are not captured.
- **Constant USD**: Trade values are not inflation-adjusted; comparisons across years do not account for purchasing power changes.
- **HS Code Scope**: Only 20 HS codes are included in the current analysis. Expanding the scope would give a more complete picture.

---

## 🔮 Future Enhancements

- [ ] Expand HS code coverage beyond 20 codes
- [ ] Add trade diversion analysis (Vietnam, Mexico, India as alternative suppliers)
- [ ] Include GDP impact estimation per sector
- [ ] Integrate real-time Comtrade API connection to Power BI
- [ ] Add country-level import/export partner breakdown
- [ ] Deploy as an interactive web dashboard (Power BI Service or Streamlit)
- [ ] Inflation-adjust trade values to constant 2020 USD

---

## 👤 Author

**Kartikey**
- GitHub: [@Kartikey2203](https://github.com/Kartikey2203)
- Project: [TradeWar](https://github.com/Kartikey2203/TradeWar)

---

## 📄 License

This project is for **educational and research purposes**. Data sourced from [UN Comtrade](https://comtradeplus.un.org/) is subject to their [Terms of Use](https://comtrade.un.org/db/help/licenseagreement.aspx).

---

## 🙏 Acknowledgements

- [UN Comtrade Plus](https://comtradeplus.un.org/TradeFlow) for providing open access to global trade statistics
- [Microsoft Power BI](https://powerbi.microsoft.com/) for the visualization platform
- Academic research on US–China trade war economics for domain context

---

*Last Updated: July 2026*
