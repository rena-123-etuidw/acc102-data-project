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

- **GitHub Repository:**https://github.com/lds-cyx/track2
- **Jupyter Notebook:** [`stock_analysis.ipynb`](stock_analysis.ipynb)

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

