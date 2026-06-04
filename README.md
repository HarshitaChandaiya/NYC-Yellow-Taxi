# 🚕 NYC Yellow Taxi — Exploratory Data Analysis (2023)

Large-scale exploratory data analysis of New York City Yellow Taxi trips for the full year of **2023** — from **38M+ raw records** down to a clean, validated **3.65M-record** dataset, with temporal, fare, and geospatial insights.

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-data%20cleaning-150458)
![GeoPandas](https://img.shields.io/badge/GeoPandas-zone%20analysis-2C7A4B)
![Jupyter](https://img.shields.io/badge/Jupyter-notebook-orange)
![Status](https://img.shields.io/badge/status-complete-success)

---

## 📌 Overview

This project explores one full year of NYC Yellow Taxi trip data to answer practical questions about *when, where, and how* people use yellow cabs across the city. The emphasis is on **rigorous data validation at scale** — the raw data contains millions of impossible or inconsistent records (zero-distance trips, negative fares, out-of-range timestamps, invalid zones) that must be cleaned carefully before any analysis is trustworthy.

**What the project covers:**
- End-to-end cleaning of 12 monthly Parquet files (Jan–Dec 2023)
- Memory-efficient processing within Google Colab's RAM limits
- Temporal demand analysis (hour of day, day of week, month, seasonality)
- Fare, distance, and payment-type analysis
- Geospatial pickup/drop-off hotspots using NYC TLC taxi zones (GeoPandas)

---

## 📂 Dataset

- **Source:** NYC Taxi & Limousine Commission (TLC) Trip Record Data
- **Period:** January–December 2023 (12 monthly Yellow Taxi Parquet files)
- **Raw volume:** ~38 million trip records
- **After cleaning:** ~3.65 million validated records
- **Supporting file:** TLC Taxi Zone Lookup + Zone shapefile (for geospatial mapping)

> The raw Parquet files are large and are **not** committed to this repo. Download them directly from the [NYC TLC Trip Record Data page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).

---

## 🧹 Data Cleaning & Validation

The bulk of the work — turning 38M noisy rows into 3.65M reliable ones. Records were removed or corrected where they were logically impossible or out of valid range:

- Trips with **zero or negative distance / duration**
- **Negative or zero fares** and totals
- **Out-of-range datetimes** (trips falling outside 2023)
- **Invalid passenger counts** and unknown payment types
- **Invalid or missing taxi zone IDs** (pickup/drop-off)
- Extreme **outliers** in fare and distance (capped using statistical thresholds)

To stay within Colab memory limits, files were processed **month by month**, downcasting numeric dtypes and dropping unused columns before concatenating.

---

## 📊 Key Findings

*(Headline themes from the analysis — see the notebook for exact figures and charts.)*

- **Demand is highly time-dependent:** trip volume peaks in evening commute hours and dips overnight, with clear weekday vs. weekend patterns.
- **Card payments dominate** over cash, which has implications for tipping behaviour (tips are recorded mainly on card trips).
- **Most trips are short:** the majority of rides fall under a few miles, with a long tail of longer airport/inter-borough trips.
- **Geospatial hotspots** cluster in Manhattan, with strong pickup/drop-off concentrations around major hubs and airports.
- **Fare scales with distance** as expected, with surcharges and tolls visible as distinct components of the total.

---

## 🗂️ Repository Structure

```
nyc-yellow-taxi-eda/
├── EDA_Assg_NYC_Taxi_Harshu.ipynb   # Main analysis notebook
├── data/                            # (gitignored) raw + lookup files
│   ├── yellow_tripdata_2023-*.parquet
│   └── taxi_zone_lookup.csv
├── reports/
│   └── NYC_Taxi_EDA_Report.docx     # Formatted written report
├── images/                          # Exported charts & maps
├── requirements.txt
└── README.md
```

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Language | Python 3.10 |
| Data | Pandas, NumPy, PyArrow (Parquet) |
| Geospatial | GeoPandas, Shapely |
| Visualization | Matplotlib, Seaborn |
| Environment | Google Colab, Jupyter Notebook |

---

## ▶️ How to Run

1. **Clone the repo**
   ```bash
   git clone https://github.com/HarshitaChandaiya/nyc-yellow-taxi-eda.git
   cd nyc-yellow-taxi-eda
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download the data** from the [NYC TLC page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) and place the Parquet files + zone lookup in `data/`.

4. **Open the notebook**
   ```bash
   jupyter notebook EDA_Optimising_NYC_Taxis_Harshita_Chandaiya.ipynb
   ```
   Or open it directly in [Google Colab](https://colab.research.google.com/).

---

## 👤 Author

**Harshita Chandaiya** — Data Analyst | Aspiring Data Scientist
MSc in Data Science, IIIT Bangalore & Liverpool John Moores University

[LinkedIn](https://www.linkedin.com/in/harshita-chandaiya-b765b8178) · [GitHub](https://github.com/HarshitaChandaiya)

---

## 📄 License

Released under the [MIT License](LICENSE). Trip data © NYC Taxi & Limousine Commission.
