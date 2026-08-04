# U.S. Business Formation Statistics: What Do New Business Applications Tell Us About the American Economy?

This project is part of the Udacity Data Scientist Nanodegree. It analyzes the U.S. Census Bureau's **Business Formation
Statistics (BFS)** — weekly counts of new business applications filed with the IRS, broken out by state — to answer five
business questions about entrepreneurial activity in the United States between 2006 and 2026.

📖 **Blog post (non-technical write-up):** [America is Starting Businesses Like Never Before](https://medium.com/@fahad.reda/america-is-starting-businesses-like-never-before-heres-what-20-years-of-data-reveals-e6c9d5eaf035?postPublishedType=initial)

✨ ## Motivation

New business applications are one of the earliest available signals of economic activity — available weekly, and well ahead
of GDP, payrolls, or other lagging economic indicators. This project explores what over two decades of application data can
tell us about long-run growth, the impact of COVID-19, regional differences across states, seasonality, and the changing
"quality" of new business filings, and builds a simple model to predict weekly application volume.

❇️ ## Business Questions

1. How have national business applications trended between 2006 and 2026, and how did COVID-19 affect them?
2. Which U.S. states lead in business formation — in absolute volume and in growth over the last decade?
3. Is there a seasonal pattern to when people file new business applications during the year?
4. What share of new applications are "high-propensity" (likely to become real employer businesses), and how has that share
   changed over time?
5. Can we predict weekly, state-level business applications from year, week-of-year, and state — and which factor matters
   most?

💎## Summary of Results

- Business applications grew slowly from 2006-2019, then jumped **~54% from 2019 to 2021** following the onset of COVID-19,
  and have stayed roughly double their pre-pandemic level ever since.
- **Florida, California, and Texas** lead in total application volume, but smaller states like **Wyoming, Delaware, and New
  Mexico** grew the fastest (2015-2025).
- Applications are seasonal: they **peak in January/March** and are **lowest in November/December**.
- The share of applications classified as "high-propensity" (likely to become a real, wage-paying business) has **fallen from
  ~59% (2006) to ~30% (2025)**, even as the pandemic-era boom pushed up the raw number of applications.
- A Random Forest model predicts weekly, state-level applications with **R² ≈ 0.91**. `State` (baseline economic scale)
  explains roughly 80% of the model's predictive power, `Year` (growth trend) about 16%, and seasonality (`Week`/`Month`)
  under 4% combined.

Full methodology, code, charts, and discussion are in the notebook.

📂## Repository Contents

| File | Description |
|---|---|
| `Pr1-US_Business_Formation_Analysis.HTML` | Same Jupyter file below, but this one is in HTML format for easy preview. |
| `Pr1-US_Business_Formation_Analysis.ipynb` | Main Jupyter notebook containing the full analysis: data loading, cleaning, exploration, visualizations, and the predictive model, following the CRISP-DM process. |
| `data/bfs_state_apps_weekly_nsa.csv` | Raw weekly business-application counts by U.S. state (2006-2026), not seasonally adjusted, from the U.S. Census Bureau. |
| `data/date_table.csv` | Lookup table mapping each `(Year, Week)` pair to a calendar start/end date. |
| `README.md` | This file. |

⚙️## Libraries Used

- `pandas`, `numpy` — data loading, cleaning, and aggregation
- `matplotlib` — visualization
- `scikit-learn` — one-hot encoding, train/test split, `RandomForestRegressor`, and evaluation metrics

💻## How to Run

1. Clone this repository.
2. Install dependencies: `pip install pandas numpy matplotlib scikit-learn jupyter`
3. Launch Jupyter and open `US_Business_Formation_Analysis.ipynb`: `jupyter notebook US_Business_Formation_Analysis.ipynb`
4. Run all cells (the notebook expects the two CSV files to be in a `data/` subfolder relative to the notebook, as laid out
   above).

📌## Acknowledgements

Data provided by the U.S. Census Bureau's [Business Formation Statistics program](https://www.census.gov/econ/bfs/index.html).
This project was completed as the first project of the Udacity Data Scientist Nanodegree program.
