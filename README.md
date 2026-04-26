# Risk-Return Comparison of AAPL, MSFT, and TSLA

> **ACC102 Mini Assignment – Track 2 (GitHub Data Analysis)**

## Problem & Users

Retail investors often need to compare multiple stocks before making investment
decisions but lack a systematic, data-driven framework for evaluating risk
versus return. This project answers the question:

> **Among Apple (AAPL), Microsoft (MSFT), and Tesla (TSLA), which stock
> offered the best risk-adjusted return from 2020 to 2025?**

Target users: retail investors, finance students, and anyone interested in
quantitative stock analysis.

## Data Source

| Item | Detail |
|------|--------|
| Provider | [Stooq](https://stooq.com/) (free historical data) |
| Tickers | AAPL.US, MSFT.US, TSLA.US |
| Period | 2020-01-02 → 2024-12-31 (≈ 1,258 trading days) |
| Frequency | Daily |
| Fields | Date, Open, High, Low, Close, Volume |

Raw CSV files are stored in the `data/` folder.

## Method

1. **Data Loading** – Read CSV files with `pandas`.
2. **Data Cleaning** – Parse dates, remove duplicates, forward-fill missing
   values.
3. **Metric Calculation** –
   
   - Daily return:
     $$
     r_t = P_t / P_{t-1} − 1
     $$
     
   - Annualised return: *mean(r) × 252*
   - Annualised volatility: *std(r) × √252*
   - Sharpe Ratio (Rf = 0): *Ann. Return / Ann. Volatility*
   - Maximum drawdown
4. **Visualisation** – Four charts produced with `matplotlib`:
   - Normalised closing price trend
   - Daily return distribution (histogram)
   - Cumulative return comparison
   - Risk-return scatter plot

## Key Findings

| Ticker | Cumulative Return | Ann. Return | Ann. Volatility | Sharpe | Max Drawdown |
|--------|------------------:|------------:|----------------:|-------:|-------------:|
| AAPL   | 244.00 % | 29.79 % | 31.68 % | 0.94 | −31.43 % |
| MSFT   | 174.39 % | 24.89 % | 30.49 % | 0.82 | −37.15 % |
| TSLA   | 1 307.89 % | 75.53 % | 67.18 % | 1.12 | −73.63 % |

### Interpretation

1. **TSLA** delivered the highest return but with extreme volatility
   (67 %) and a max drawdown of −74 %, representing a high-risk-high-reward
   profile.
2. **MSFT** offered the most stable risk-return balance with the lowest
   volatility among the three.
3. **AAPL** sat in between, providing solid returns with moderate risk.
4. Risk-averse investors may favour MSFT or AAPL; risk-tolerant investors
   may lean toward TSLA.

## How to Run

### Prerequisites

- Python 3.8+
- Required packages: `pandas`, `numpy`, `matplotlib`

```bash
pip install pandas numpy matplotlib
```

### Run the Jupyter Notebook

```bash
jupyter notebook stock_analysis.ipynb
```

All output charts and metrics will be saved to the `output/` folder.

## Project Structure

```
.
├── data/
│   ├── aapl_us_d.csv        # AAPL daily data (Stooq)
│   ├── msft_us_d.csv        # MSFT daily data (Stooq)
│   └── tsla_us_d.csv        # TSLA daily data (Stooq)
├── output/
│   ├── price_trend.png
│   ├── return_distribution.png
│   ├── cumulative_return.png
│   ├── risk_return_scatter.png
│   └── summary_metrics.csv
├── stock_analysis.ipynb      # Jupyter Notebook version
└── README.md
```

## Product Link

- **GitHub Repository:**https://github.com/rena-123-etuidw/acc102-data-project
- **Jupyter Notebook:** [`stock_analysis.ipynb`](stock_analysis.ipynb)
- **Demo Video:**https://www.bilibili.com/video/BV17EZcBGEkW/?spm_id_from=333.1387.list.card_archive.click&vd_source=aa6693a5639cb7b678b7d743d0426b0a


## Limitations & Next Steps

### Limitations
- Analysis covers only **three stocks** – conclusions may not generalise
  to broader market.
- **Risk-free rate is set to 0** when computing the Sharpe Ratio; a more
  accurate analysis would use T-bill yields.
- **No adjustment for dividends or stock splits** beyond what Stooq
  provides in its adjusted close prices.
- The period (2020–2025) includes COVID-19 market disruptions, which may
  skew volatility estimates.

# Reflection
This reflection summarises my experience completing the ACC102 mini assignment, focusing on the process, challenges, learning outcomes, limitations, and professional practice.

The goal of this project was to build a data product that compares the risk and return of three stocks: AAPL, MSFT, and TSLA. I used Python to load, clean, and analyse historical price data, calculate key financial metrics, and create visualisations to communicate insights clearly. This project helped me understand how data analysis can support investment decisions and how to present findings in a structured, user‑friendly way.

During the project, I faced several challenges. The first was handling missing values and ensuring the time series data was consistent across all three stocks. I solved this by checking dates, removing duplicates, and using forward‑fill to handle small gaps. The second challenge was correctly calculating annualised return, volatility, and Sharpe ratio. I double‑checked formulas and tested outputs to ensure accuracy. The third challenge was organising files properly on GitHub and making sure the notebook, README, and data were easy for someone else to follow.

Through this assignment, I strengthened my technical skills in pandas, numpy, and matplotlib. I also learned how to structure a data analysis project, write a clear README, and use GitHub for version control and submission. More importantly, I understood the full workflow of a data product: from defining a problem and sourcing data to cleaning, analysing, visualising, and communicating results. This experience will be useful for future courses and for building a professional portfolio.

I also recognise several limitations of this project. The analysis only includes three stocks, so the findings cannot be generalised to the whole market. The Sharpe ratio used a risk‑free rate of 0 for simplicity, which is not fully realistic. Dividends and stock splits were not adjusted beyond the provided close prices. In future improvements, I could include more stocks, use real risk‑free rates, add dividend adjustments, and build an interactive tool so users can select their own time periods.

### AI Disclosure
I used AI tools to assist with code structure, README writing, grammar checking, and formula explanations. All data analysis, design decisions, interpretation of results, and project logic were completed independently. I understand how each part of the code works and can explain every step of the project.

Overall, this assignment helped me develop both technical and communication skills required for a data product. I learned how to turn raw data into useful insights and how to present work professionally. This project has given me confidence to explore more advanced data analysis tasks in the future.

