# Stock Price, Risk and Commodity Analysis (NSE Stocks)

An exploratory data analysis of 5 large NSE-listed stocks over 3 years, covering price statistics, returns, volatility, correlation, moving averages, and a comparison with crude oil and gold.

## Objective
To understand how different stocks compare on **return and risk**, whether their daily movements are related to each other, and whether they move with global commodities (crude oil and gold).

## Data
- **Source:** Yahoo Finance, downloaded with the `yfinance` Python library
- **Stocks (5):** HDFC Bank, Infosys, ITC, Sun Pharma, Tata Steel (NSE)
- **Commodities (2):** Crude Oil futures (`CL=F`), Gold futures (`GC=F`)
- **Period:** 12 Oct 2023 to 9 Oct 2026 (739 trading days)
- **Data quality:** No missing values in the stock price data
- **Note:** `yfinance` returns prices adjusted for splits and dividends, so closing prices may differ slightly from the quoted market prices. Returns therefore include the effect of dividends.

## Methods
1. **Closing price statistics:** mean, maximum and minimum for each stock
2. **Daily percentage change:** `(today - yesterday) / yesterday`, using `pct_change()`
3. **Volatility:** standard deviation of daily returns, annualized by multiplying by `sqrt(252)` (about 252 trading days a year)
4. **Correlation:** correlation matrix of *daily returns* (not prices), shown as a heatmap
5. **Moving averages:** 20-day and 50-day averages to smooth out daily noise and show the trend
6. **Cumulative returns:** compounded daily returns, showing total gain or loss over the period
7. **Commodity comparison:** correlation of stock daily returns with crude oil and gold daily returns

## Results

### Closing price statistics (adjusted, INR)
| Stock | Mean | Max | Min |
|---|---|---|---|
| HDFC Bank | 829.44 | 996.42 | 662.64 |
| Infosys | 1458.55 | 1901.08 | 985.30 |
| ITC | 369.44 | 463.95 | 255.00 |
| Sun Pharma | 1653.66 | 2001.10 | 1059.35 |
| Tata Steel | 158.32 | 216.66 | 109.44 |

### Volatility
| Stock | Daily Volatility % | Annual Volatility % |
|---|---|---|
| Tata Steel | 1.76 | 27.94 |
| Infosys | 1.67 | 26.44 |
| HDFC Bank | 1.29 | 20.43 |
| Sun Pharma | 1.24 | 19.73 |
| ITC | 1.21 | 19.28 |

### Cumulative return (Oct 2023 to Oct 2026)
| Stock | Return % |
|---|---|
| Sun Pharma | +60.00 |
| Tata Steel | +47.08 |
| HDFC Bank | -4.69 |
| Infosys | -23.24 |
| ITC | -31.24 |

### Correlation of daily returns
| | HDFC Bank | Infosys | ITC | Sun Pharma | Tata Steel |
|---|---|---|---|---|---|
| HDFC Bank | 1.00 | 0.19 | 0.22 | 0.12 | 0.34 |
| Infosys | 0.19 | 1.00 | 0.14 | 0.13 | 0.18 |
| ITC | 0.22 | 0.14 | 1.00 | 0.14 | 0.20 |
| Sun Pharma | 0.12 | 0.13 | 0.14 | 1.00 | 0.27 |
| Tata Steel | 0.34 | 0.18 | 0.20 | 0.27 | 1.00 |

### Correlation with commodities (daily returns)
| Stock | Crude Oil | Gold |
|---|---|---|
| HDFC Bank | -0.13 | 0.11 |
| Infosys | 0.06 | -0.01 |
| ITC | -0.09 | 0.06 |
| Sun Pharma | -0.04 | 0.01 |
| Tata Steel | -0.03 | 0.21 |

## Key findings
1. **Tata Steel was the riskiest stock** (27.9% annual volatility), followed by Infosys (26.4%). ITC was the least volatile (19.3%). Tata Steel's daily moves were about 45% larger than ITC's.
2. **The stocks were only weakly correlated** (0.12 to 0.34, average about 0.19, none negative). The highest pair was HDFC Bank and Tata Steel (0.34). A mix of these sectors would spread risk.
3. **Sun Pharma gave the best 3-year return (+60.0%)** and ITC the worst (-31.2%). Infosys also fell sharply (-23.2%).
4. **Higher volatility did not mean higher return.** Sun Pharma had below-average volatility but the best return, while ITC had the lowest volatility but the worst return.
5. **Commodity link was weak.** Stock returns had low correlation with crude oil (-0.13 to 0.06) and gold (-0.01 to 0.21). The highest was Tata Steel with gold (0.21), which is still weak. Crude oil and gold were almost uncorrelated with each other (-0.02).
6. **ITC's chart shows a sharp fall in early 2026**, after which the 20-day moving average stayed below the 50-day average during the decline.

## Limitations
- Only 5 stocks and about 3 years of data, so results may not hold for other stocks or periods.
- Past performance does not predict future returns. This is a descriptive analysis, not investment advice.
- Correlation does not prove one thing causes another.
- Indian and US markets trade at different times, and the data was joined on common trading days, so same-day correlation with commodities may miss delayed effects.
- Reasons behind the findings (sector trends, company news) were not tested in this project.

## Possible next steps
- Add more stocks, including commodity-linked companies such as Coal India
- Test whether commodity moves affect the next day's stock returns
- Compare risk-adjusted returns (for example, the Sharpe ratio)

## Tools
Python, Pandas, NumPy, Matplotlib, Seaborn, yfinance, Google Colab

## How to run
1. Open `Stocks_Analysis_Project.ipynb` in Google Colab
2. Run all cells (Runtime, then Run all). The first cell installs `yfinance`.
