DSA 210 Term Project: Analyzing US Congressional Stock Trading

1. Project Overview & Motivation
This project aims to investigate the stock trading activities of United States Congress members. Public scrutiny suggests that congress members may have access to non-public information, potentially allowing them to outperform the general market. 

The primary goal is to determine if there is a statistically significant difference between the returns of stocks traded by congress members and the market benchmark (S&P 500) immediately following the transaction date.

2. Research Question & Hypotheses
Research Question: Do US Congress members generate "Abnormal Returns" (AR) in their stock trades compared to the market performance?

To answer this, I will conduct a statistical hypothesis test centered on the Cumulative Abnormal Return (CAR) metric.

Null Hypothesis (H_0): The average Cumulative Abnormal Return (CAR) for stocks purchased by congress members is equal to zero ($\mu_{CAR} = 0$). This implies their trades perform no better than the market average.
Alternative Hypothesis (H_1): The average Cumulative Abnormal Return (CAR) for stocks purchased by congress members is significantly greater than zero ($\mu_{CAR} > 0$). This implies they systematically outperform the market.

3. Data Sources
I will utilize two primary datasets and enrich them by merging based on ticker symbols and dates.

| Data Type | Source | Description |
|-----------|--------|-------------|
| Trading Data | [Quiver Quant](https://www.quiverquant.com/) | Dataset containing transaction date, ticker, representative, transaction type (purchase/sale), and amount. |
| Market Data | Yahoo Finance (`yfinance`) | Historical daily OHLCV (Open, High, Low, Close, Volume) data for individual stocks and the S&P 500 index (SPY). |

4. Methodology
The project will follow a standard Data Science pipeline:

A- Data Collection & Cleaning
Collection: Use Python scripts to scrape/fetch trading data from Quiver Quant and download historical price data via the `yfinance` API.
Cleaning: Handle missing values, correct ticker symbol inconsistencies, and filter out penny stocks with low liquidity.
Enrichment: Calculate daily returns for both the specific stocks and the market index (S&P 500).

B- Exploratory Data Analysis (EDA)
* Visualize the distribution of trades by party (Democrat vs. Republican).
* Analyse the most traded sectors and companies.
* Time-series visualization of trading volume vs. major political events.

C- Statistical Analysis (Event Study)
I will implement an Event Study methodology:
1.  Define Event Window: A period surrounding the transaction date (e.g., $t-5$ to $t+30$ days).
2.  Calculate Expected Return ($E[R]$): Use the Market Model: 
    $$R_{stock} = \alpha + \beta \cdot R_{market} + \epsilon$$
3.  Calculate Abnormal Return (AR): $$AR_{it} = R_{it} - (\alpha_i + \beta_i \cdot R_{mt})$$
4.  Hypothesis Testing: Perform a one-sample t-test on the Cumulative Abnormal Returns (CAR) to check for statistical significance at the 95% confidence level ($p < 0.05$).

D- Machine Learning (Future Work)
After statistical validation, I plan to train a classification model (e.g., Random Forest or Logistic Regression) to predict whether a specific trade will result in a positive return, using features such as:
* Politician's Party
* Committee Assignments
* Sector of the Stock
* Transaction Amount
  
