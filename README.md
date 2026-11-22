# Retail Sales Profitability Analysis

**Where does a US retailer actually make money — and where do discounts destroy it?**

An exploratory data analysis project in Python (Pandas, Matplotlib, Seaborn) that treats the
Sample Superstore dataset like a real business problem: sales are growing, but profit is not
keeping up. The analysis quantifies why, and ends with concrete recommendations.

## Business question

A US office-supply and furniture retailer sees sales grow year over year, yet margins feel thin.
Leadership suspects aggressive discounting is eroding profit. This project answers:

1. How do sales and profit trend over time — is the business seasonally healthy?
2. Which categories and sub-categories earn money, and which consistently lose it?
3. Which regions underperform, and is the problem local or systemic?
4. At what discount level does an average order line stop being profitable?
5. Which customer segments and shipping modes are the most profitable?

## Key findings

| # | Finding | Evidence |
|---|---------|----------|
| 1 | The business grows but leaks margin: 2017 sales grow +20.4% while profit grows only +14.2% | `fig1_quarterly_trend.png` |
| 2 | **Tables (-$17.7K) and Bookcases (-$3.5K) are structurally unprofitable** across all four years | `fig3_subcategory_profit.png` |
| 3 | Central region runs a 7.9% margin vs 14.9% in the West — and its Furniture cell is the only region-category combination in the red | `fig4_region_margins.png` |
| 4 | **Profitability breaks once discounts pass 20%**: +29.5% margin at full price, +11.6% at 11-20% off, -10.0% at 21-30%, -77.4% above 40% | `fig6_discount_bands.png` |
| 5 | The 13.9% of order lines discounted 30%+ lost **$135K combined** — nearly half of the company's $286K total profit | notebook, section 8 |
| 6 | Profit is concentrated: the top 10% of customers generate 57% of it; 155 of 793 customers are lifetime-unprofitable, and 94% of those bought at 30%+ discounts | notebook, section 9 |

## Recommendations

1. **Cap standard discounts at 20%** — anything deeper needs approval as a deliberate clearance decision.
2. **Re-price, renegotiate, or exit Tables and Bookcases** — four years of cumulative losses will not fix themselves with volume.
3. **Fix Central-region Furniture first** (discount approvals, regional pricing) before any national policy change.
4. **Protect and grow the Home Office segment** — highest margin (14.0%), smallest share of sales.
5. **Redirect promotional spend to Technology and Office Supplies**, where margins absorb discounts without going negative.

## Dataset

- **Sample Superstore** — Tableau's public sample dataset, widely used in analytics training.
- 9,994 order lines, 21 columns, US orders from January 2014 to December 2017.
- Fields: order/shipping dates, ship mode, customer, segment, geography, product, category,
  sub-category, sales, quantity, discount, profit.

### Provenance and honesty note

This is **fictional sample data published by Tableau for educational and demonstration use** —
not real company records. It is the standard dataset for this kind of analysis, which makes the
results easy to verify and compare. The copy in `data/superstore.csv` was mirrored from a public
GitHub copy of Tableau's file and converted from Latin-1 to UTF-8 encoding; **no rows or values
were changed**. All cleaning, analysis, and findings in the notebook are original work.

## Project structure

```
├── README.md
├── requirements.txt
├── data/
│   └── superstore.csv
├── notebooks/
│   └── retail_sales_profitability_eda.ipynb
└── figures/                        # charts saved by the notebook
    ├── fig1_quarterly_trend.png
    ├── fig2_category_sales_profit.png
    ├── fig3_subcategory_profit.png
    ├── fig4_region_margins.png
    ├── fig5_discount_scatter.png
    ├── fig6_discount_bands.png
    └── fig7_segment_shipmode.png
```

## How to run

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/retail_sales_profitability_eda.ipynb
```

Run all cells top to bottom. The notebook cleans the data, engineers features
(profit margin, shipping days, order month), answers each business question with a chart and a
written insight, and saves every chart to `figures/`.

## Tech stack

Python 3 · Pandas · NumPy · Matplotlib · Seaborn · Jupyter

---

*Analysis and code: [Youssef Mamdouh](https://www.linkedin.com/in/youssef-mamdouh-322440357) —
final-year Computer Science student and data analyst (SQL, Python, Power BI, Tableau).*
