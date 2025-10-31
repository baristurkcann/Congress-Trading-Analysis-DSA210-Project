DSA 210 Project Proposal: The Impact of US Congressional Stock Trading on Market Prices
1. Project Motivation
The primary motivation for this project is to analyze whether stock trades (purchases and sales) made by members of the US Congress generate abnormal returns in the stock market. I aim to investigate, using statistical and machine learning methods, whether congress members outperform the market due to their potential access to non-public information, or if the market perceives their trades as a significant signal.

2. Data Sources
This project will utilize two main public datasets:

Congressional Trading Data:

Source: Quiver Quant (quiverquant.com) API or platform.

Content: Data on which congress member traded which stock, on what date, and for what volume/amount.

Stock Price Data:

Source: Yahoo Finance (specifically the yfinance Python library).

Content: Daily (or hourly) open, high, low, close (OHLC) prices and volume data for the traded stocks, as well as for benchmark indices like the S&P 500.

3. Data Collection Plan
The data collection process will involve the following steps:

Congress Data: All congressional buy/sell transactions from the last 1-2 years will be fetched using Python from the Quiver Quant platform and stored in a DataFrame.

Price Data: The yfinance Python library will be used to retrieve all historical price data for the stocks identified in step 1. This will cover a window around the transaction date (e.g., 10 days before and 30 days after the trade).

Merging: These two datasets will be merged based on the stock ticker and date to create the final dataset for analysis.

4. Analysis & Methodology Plan (Future Work)
Due 28 November (Exploratory Data Analysis): EDA and visualizations will be conducted on trading volumes, most active members, and most traded sectors.

Due 02 January (Machine Learning): An "event study" methodology will be applied to test for abnormal returns (alpha) in the days surrounding the transaction date (T=0). Furthermore, classification models (e.g., Random Forest, Logistic Regression) may be explored to predict whether a trade will lead to a significant positive or negative price movement.
