<h1 align="center">Financial Crisis Bank Stock Analysis (2006–2016)</h1>

> A Python-based exploratory analysis of six major U.S. banks during the 2008 financial crisis, using time-series techniques and statistical visualization to reveal volatility patterns, correlation dynamics, and institutional recovery trends across a decade of market data.

---

## Table of Contents

- [Executive Summary](#executive-summary)
- [Data Acquisition and Pipeline](#data-acquisition--pipeline)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Technical Analysis and Visuals](#technical-analysis--visuals)
- [Conclusion](#conclusion)

---

## Executive Summary

![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/closing_price_linegraph.png)

This project analyzes how major U.S. financial institutions behaved during the 2008 global financial crisis and the recovery period that followed through 2016. Using daily stock price data for six systemically important banks — Bank of America (BAC), Citigroup (C), Goldman Sachs (GS), JPMorgan Chase (JPM), Morgan Stanley (MS), and Wells Fargo (WFC) — the analysis focuses on price volatility, extreme market movements, correlations between institutions, and recovery trends.

The purpose of this project is to demonstrate exploratory data analysis, time-series handling, and data visualization using real-world financial data. Rather than building predictive models, the analysis serves as a practical case study in working with noisy datasets and communicating insights clearly through visual exploration.

---

## Data Acquisition and Pipeline

The dataset consists of daily OHLC (Open, High, Low, Close) stock price data from January 2006 through early 2016, covering pre-crisis conditions, the 2008–2009 financial crisis, and the post-crisis recovery period. Data was retrieved using Python and ingested into Pandas DataFrames for analysis.

A MultiIndex DataFrame was used to organize stock price data across both financial institutions and price attributes (Open, High, Low, Close, Volume). This structure makes it easier to analyze multiple banks simultaneously, apply transformations consistently, and scale the analysis if additional assets are added later.

**[Table 1 — View of MultiIndex DataFrame](./outputs/bank_stocks.csv)**

To ensure consistent results and avoid repeated API calls, the dataset was saved using the `.pickle` format. This approach preserves data types and index structure while allowing the analysis to be rerun quickly and reliably. From a data workflow perspective, this mirrors common industry practices around caching and reproducibility when working with external data sources.

---

## Exploratory Data Analysis

This section focuses on transforming raw price data into metrics that help describe market behavior, institutional risk, and periods of stress.

Daily returns were calculated using percentage change to normalize price movements across banks with different share prices. This enables meaningful comparison of volatility and correlation across institutions.

![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/ms_return.png)
![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/c_return.png)

To identify periods of heightened stress, the analysis examines the largest negative daily returns for each bank. These extreme values often align with known market disruptions, including the peak of the 2008–2009 crisis and structural events such as Citigroup's 2011 reverse stock split. Rather than treating these points as errors, they are interpreted as meaningful indicators of market instability.

**[Table 2 — Returns by institution](./outputs/returns.csv)**

**[Table 2 — Worst daily returns by institution]**

| Bank | Return Date | Note |
|------|-------------|------|
| **BAC Return** | 2009-01-20 | Inauguration day |
| **C Return** | 2011-05-06 | |
| **GS Return** | 2009-01-20 | Inauguration day |
| **JPM Return** | 2009-01-20 | Inauguration day |
| **MS Return** | 2008-10-09 | |
| **WFC Return** | 2009-01-20 | Inauguration day |

Volatility, measured using the standard deviation of daily returns, is used as a proxy for institutional risk. To understand how risk changed over time, volatility is compared between 2008, representing crisis conditions, and 2015, representing a more stable market environment. This comparison shows how some institutions experienced sustained volatility even after broader market recovery.

![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/volatility_comparison.png)

---

## Technical Analysis and Visuals

This section focuses on using visualization techniques to make time-series behavior easier to interpret and communicate.

A 30-day moving average was applied to daily closing prices to reduce short-term noise and highlight broader market trends. During the financial crisis, this smoothing clearly reveals extended periods of decline that are less obvious in raw price plots.

![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/30_day_avg_linegraph.png)

To understand how banks moved relative to one another, a correlation matrix was created using daily returns. Heatmaps show that many institutions became highly correlated during crisis periods, reflecting shared exposure to systemic risk.

![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/corr_heatmap.png)

To further illustrate changes in volatility over time, Bollinger Bands were applied to selected bank stocks. Candlestick charts were also used to provide additional context around daily price movement and market uncertainty.

![image](https://github.com/EndreGuljas/Python_Bank_Stock_Analysis/blob/main/outputs/BAC_candlestick.png)

---

## Conclusion

This project demonstrates a practical approach to exploratory financial data analysis using real historical data. By focusing on return behavior, volatility comparison, correlation analysis, and clear visualization, the analysis highlights how major financial institutions responded to market stress during the financial crisis and recovery period. 

Beyond the financial context, the project reinforced core data analysis skills, including structuring time-series data, working with noisy real-world datasets, validating findings against known events, and communicating insights through effective visuals. Overall, the project shows how thoughtful data preparation and visualization can uncover meaningful patterns in complex datasets.
