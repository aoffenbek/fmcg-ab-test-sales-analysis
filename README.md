# FMCG A/B Test Sales Analysis

**Author:** Agnes Offenbek  
**Role:** Business Analyst | Junior Data Scientist  
**Project Type:** Portfolio Project  
**Tools:** Python, Pandas, Matplotlib, Jupyter Notebook  

---

## Project Overview

This project demonstrates an **A/B test analysis** for a fictional FMCG retail scenario.  
The goal is to **compare sales performance between stores with a discount campaign (treatment group) and control stores**.

- Clean, structured data is used from a **simulated sales dataset**.
- End-to-end analysis is performed in **Python (Jupyter Notebook)**.
- Visualizations are created using **Matplotlib**.
- Summary statistics and CSV output are generated for further reporting.

---

## Folder Structure
```
fmcg-ab-test-sales-analysis/
│
├── data/
│ ├── raw/ # Original dataset
│ └── processed/ # Summary tables and processed outputs
│
├── notebooks/
│ └── 01_ab_test_analysis.ipynb # Main analysis notebook
│
├── src/
│ └── data_generation.py # Script to generate example dataset
│
├── README.md
└── requirements.txt # Python dependencies
```
---

## How to Run

**1. Clone the repository**

```bash
git clone https://github.com/aoffenbek/fmcg-ab-test-sales-analysis.git
cd fmcg-ab-test-sales-analysis
```

**2. Create a virtual environment (optional but recommended)**

python -m venv venv
source venv/Scripts/activate  # Windows

**3. Install dependencies**

pip install -r requirements.txt

**4. Run the notebook**

Open Jupyter Notebook:
Navigate to notebooks/01_ab_test_analysis.ipynb and run all cells.

---

## Project Steps

1. **Data Generation / Loading** – generate or load raw sales data.
2. **Grouping Stores** – assign stores to discount or control group.
3. **Exploratory Data Analysis** – calculate daily sales, averages, and visualize.
4. **Summary Statistics** – compute mean, standard deviation, and export results.
5. **Visualization** – bar charts comparing discount vs control groups.
6. **Output** – save summary tables for further business analysis.

---

## Example code snippets

Load data

import pandas as pd

# Load raw sales data
sales_df = pd.read_csv('data/raw/sales_data.csv')

Assign Groups for A/B Test
# Assign stores to discount or control group
sales_df['group'] = sales_df['store'].apply(lambda x: 'discount' if int(x.split('_')[1]) <= 10 else 'control')


Calculate Summary Statistics
# Average daily sales per group
summary = sales_df.groupby('group')['daily_sales'].agg(['mean','std']).reset_index()
summary.to_csv('data/processed/ab_test_summary.csv', index=False)

Simple Visualization
import matplotlib.pyplot as plt

plt.bar(summary['group'], summary['mean'], yerr=summary['std'], color=['skyblue','orange'])
plt.title('Average Daily Sales: Discount vs Control')
plt.ylabel('Average Sales')
plt.show()

---

## Skills Demonstrated

- **Data Analysis & Cleaning:** Pandas, SQL basics
- **Visualization:** Matplotlib charts for A/B comparison
- **Statistical Thinking:** Basic summary statistics for A/B testing
- **Portfolio-Ready Workflow:** Folder structure, modular code, reproducibility
- **Documentation & Reporting:** Clear README and notebook explanation

---

## Requirements

All Python dependencies are listed in requirements.txt. Install them with:

pip install -r requirements.txt


Minimum packages:

pandas>=1.5.0
matplotlib>=3.7.0
numpy>=1.25.0
jupyter>=1.0.0


Optional (for SQL queries):

sqlalchemy>=2.0

---

## Next Steps / Extensions

- Apply **hypothesis testing (t-tests)** to confirm statistical significance.
- Integrate **time-series analysis** for trends over weeks/months.
- Simulate **realistic FMCG datasets** with multiple product categories.
- Explore **Python visualization libraries** (Seaborn, Plotly) for interactive dashboards.
