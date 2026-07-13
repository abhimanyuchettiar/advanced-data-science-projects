# Diamond Price Analysis & Prediction

An end-to-end data analysis and machine learning project on the classic **Diamonds dataset** (~54,000 records) — covering data cleaning, feature engineering, interactive visualization, and regression modeling to understand and predict diamond prices.

▶️ **[View the fully rendered notebook on nbviewer](https://nbviewer.org/github/abhimanyuchettiar/advanced-data-science-projects/blob/main/diamond-price-analysis/notebooks/diamond_price_analysis.ipynb)**
*(GitHub's built-in preview doesn't render Plotly's interactive charts — use the nbviewer link above to see everything working.)*

---

## Dataset

The [Diamonds dataset](https://ggplot2.tidyverse.org/reference/diamonds.html) — 53,940 diamonds with attributes:
- **Physical:** carat, x/y/z dimensions (mm), depth %, table %
- **Quality:** cut, color, clarity
- **Target:** price ($)

## What This Project Does

1. **Data Cleaning** — removed rows with physically impossible zero dimensions, duplicates, and extreme outliers in depth/table/dimensions.
2. **Feature Engineering** — derived `volume`, `density_proxy`, `table_to_depth_ratio`, ordinal quality ranks (`cut_rank`, `color_rank`, `clarity_rank`), a composite `quality_score`, and carat bins.
3. **Exploratory Visualization (Plotly)** — interactive histograms, scatter plots, box plots, a correlation heatmap, and a 3D scatter of carat/clarity/price.
4. **Modeling (scikit-learn)** — trained and compared Linear Regression, Ridge Regression, Random Forest, and Gradient Boosting to predict price.
5. **Model Interpretation** — actual-vs-predicted plots, residual analysis, and feature importance ranking.

## Key Findings

- **Carat dominates price** — carat and related size features (volume, x/y/z) are by far the strongest predictors of diamond price.
- **Cut quality is deceptive at first glance** — the *raw* average price by cut looks counter-intuitive (Fair-cut diamonds can appear pricier on average) simply because buyers of large stones don't always choose the best cuts. Normalizing by **price-per-carat** reveals the true premium that better cuts command.
- **Pricing is non-linear** — tree-based ensembles (Random Forest, Gradient Boosting) clearly outperform linear models, confirming that carat, cut, color, and clarity interact rather than combine additively.
- **Engineered features add real value** — `volume` and `quality_score` rank among the most informative features for the best model.

### Sample Visualizations

**Price vs. Carat, colored by Cut**
![Price vs Carat](../images/price_vs_carat.png)

**Average Price vs. Price-per-Carat by Cut** — the insight that raw price comparisons hide
![Price vs Price-per-Carat by Cut](../images/price_vs_ppc_by_cut.png)

## Tech Stack

`pandas` · `numpy` · `scikit-learn` · `plotly` · `seaborn` (for dataset loading)

## Project Structure

```
diamond-price-analysis/
├── README.md
├── data/
│   └── raw/
│       └── diamonds.csv
├── notebooks/
│   └── diamond_price_analysis.ipynb
└── images/
    ├── price_vs_carat.png
    └── price_vs_ppc_by_cut.png
```

## How to Run

```bash
pip install pandas numpy seaborn scikit-learn plotly jupyter
jupyter notebook notebooks/diamond_price_analysis.ipynb
```
