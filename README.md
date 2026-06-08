# 🌞 NREL Limited Access 2030 Moderate PV Supply Curve — California Analysis

**Course:** CISD 43 – Big Data Analytics | Mt. San Antonio College  
**Dataset:** [NREL Limited Access 2030 Moderate PV Supply Curve](https://data.openei.org/submissions/6001)

---

## Overview

This project analyzes utility-scale solar energy development potential across California counties using NREL's **Limited Access 2030 Moderate PV Supply Curve** dataset. The dataset is produced by NREL's reV (Renewable Energy Potential) model and contains site-level lat/long coordinates across the U.S., each assessed for solar resource quality and development viability.

The analysis focuses on key supply curve metrics including **LCOE (Levelized Cost of Energy)** — the break-even price per MWh a project must sell electricity to cover all costs over its lifetime — alongside capacity factors, transmission costs, and installed capacity.

---

## Dataset

| Attribute | Detail |
|---|---|
| Source | NREL reV (Renewable Energy Potential) Model |
| Scenario | Limited Access, 2030 Moderate (NREL ATB) |
| Format | CSV — site-level supply curve points |
| Geography | U.S. nationwide; filtered to **California counties** |
| Key Columns | `mean_cf`, `mean_lcoe`, `lcot`, `capacity_mw`, `dist_km`, `reinforcement_cost_per_mw_ac`, `sc_point_gid` |

**"Limited Access"** indicates that sites on protected land, steep slopes, wetlands, and urban areas have been excluded. **"2030 Moderate"** refers to mid-range technology cost projections from NREL's Annual Technology Baseline.

---

## Project Components

### 1. Exploratory Data Analysis (EDA)
- Statistical profiling of LCOE distributions across California counties
- Seaborn visualizations: histograms, boxplots, scatter plots, heatmaps
- Outlier detection and missing value handling

### 2. Machine Learning

**Linear Regression**  
Predicts `mean_lcoe` as a continuous variable based on site-level features such as capacity factor, distance to transmission, and reinforcement cost per MW AC.

**K-Nearest Neighbors (KNN)**  
Classifies solar sites into development viability tiers (Low / Medium / High) based on LCOE and supply curve attributes. Features normalized using `StandardScaler` prior to training.

### 3. MongoDB
NoSQL document storage used to ingest and query the NREL supply curve dataset. Queries explore LCOE ranges, county-level aggregations, and site filtering by capacity factor thresholds.

### 4. RapidMiner
Visual ML workflow environment used to replicate and validate the Linear Regression and KNN models built in Python.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy, Seaborn, Sklearn) | EDA & machine learning |
| Jupyter Notebook | Analysis environment |
| MongoDB | NoSQL data storage & querying |
| RapidMiner | Visual ML workflows |
| AWS | Cloud infrastructure |

---

## Repository Structure

```
├── data/
│   └── (NREL dataset not included — see link above)
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Linear_Regression.ipynb
│   └── 03_KNN.ipynb
├── mongodb/
│   └── queries.js
├── rapidminer/
│   └── workflow.rmp
└── README.md
```

---

## Data Source & Attribution

National Renewable Energy Laboratory (NREL). *Limited Access 2030 Moderate PV Supply Curve.* Open Energy Data Initiative. https://data.openei.org/submissions/6001

---

## Author

**Tina** | GIS Analyst & Aspiring Data Engineer | Mt. SAC CISD 43
