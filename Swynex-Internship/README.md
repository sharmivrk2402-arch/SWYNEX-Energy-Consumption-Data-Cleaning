# Energy Consumption — Exploratory Data Analysis

This repository contains Task 2 EDA performed on the cleaned dataset from Task 1.

## Files
- `cleaned_dataset.csv` — cleaned input dataset used for this analysis
- `eda_analysis.ipynb` — reproducible Python notebook
- `EDA_Report.md` — findings, statistics, charts and limitations
- `charts/` — exported charts used in the report

## Tools
Python, Pandas, NumPy, Matplotlib, Jupyter Notebook.

## How to run
Open `eda_analysis.ipynb` in Jupyter Notebook or Google Colab. The notebook expects `cleaned_dataset.csv` in the same folder. Run the cells from top to bottom.

## Main findings
- Temperature has the strongest positive numerical correlation with energy consumption (Pearson r ≈ 0.696).
- Average consumption is higher in records where HVAC is On than Off.
- The highest occupancy quartile has the highest average consumption.
- Saturday has the highest weekday average in this sample.
- One low energy-consumption observation is flagged by the 1.5×IQR rule and should be reviewed, not automatically deleted.

See `EDA_Report.md` for exact statistics, charts, interpretation and limitations.
