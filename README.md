# DSA210-Congressional Trading - BARIŞ TÜRKCAN

**Analyzing the Impact of US Congressional Stock Trading on Market Prices**

A data science project investigating whether US Congress members generate "Abnormal Returns" and outperform the market using potential non-public information.

## Contents

* [Project Overview](#project-overview)
* [Motivation](#motivation)
* [Data Sources](#data-sources)
* [Research Questions & Hypotheses](#research-questions--hypotheses)
* [Methodology](#methodology)
* [Analysis Plan](#analysis-plan)
* [Key Findings (Preliminary)](#key-findings-preliminary)
* [How to Run](#how-to-run)
* [AI Usage Declaration](#ai-usage-declaration)

## Project Overview

This project aims to determine if trades made by US Senators and Representatives systematically outperform the S&P 500 index. By merging political trading disclosures with historical market data, I analyze the "Abnormal Returns" following transaction dates to identify potential informational advantages.

## Motivation

I am working on this project because the intersection of politics and finance raises significant ethical and economic questions.
* **Market Fairness:** Do policymakers have an unfair advantage over retail investors?
* **Political Ethics:** Are members of congress voting on bills that directly benefit their portfolios?
* **Signal Processing:** Can following congressional trades serve as a profitable investment strategy for the public?

## Data Sources

I collect and merge data from the following sources:

### 1. Congressional Trading Data
* **Source:** Quiver Quant (and manual scraping/simulated data for preliminary phase).
* **Content:** Transaction date, Representative name, Party, Ticker symbol, Transaction type (Buy/Sell), and Amount range.

### 2. Market Data
* **Source:** Yahoo Finance API (`yfinance`).
* **Content:** Daily OHLCV (Open, High, Low, Close, Volume) data for individual stocks and the benchmark index (S&P 500 / SPY).

## Research Questions & Hypotheses

Based on the initial feedback, I have formulated the following hypotheses to be tested using statistical methods:

### 1. Abnormal Returns Analysis
**Research Question:** Do stocks purchased by congress members show positive abnormal returns in the 30 days following the trade?
* **Null Hypothesis (H0):** The average 30 day benchmark adjusted return for congressional trades is less than or equal to zero (μ ≤ 0).
* **Alternative Hypothesis (H1):** The average 30d ay benchmark adjusted return for congressional trades is significantly positive (μ > 0).


### 2. Party Performance Comparison
**Research Question:** Is there a significant difference in trading performance between Democrats and Republicans?
* **Null Hypothesis ($H_0$):** There is no significant difference in the mean returns between the two major parties.
* **Alternative Hypothesis ($H_1$):** One party consistently generates higher returns than the other.

## Methodology

I approach this analysis using the standard **Event Study** framework:

1.  **Data Collection:** Fetching trades and matching them with historical price data using Python.
2.  **Enrichment:** Calculating 30 day post transaction returns and adjusting them relative to the market benchmark (SPY) to isolate performance beyond general market movements:
    $$Return = \frac{Price_{t+30} - Price_{t}}{Price_{t}}$$
3.  **Hypothesis Testing:** Using a one-sample **t-test** to check if the mean return is statistically different from zero.
4.  **EDA:** Visualizing return distributions and volume spikes around trade dates.

## Analysis Plan

* **Phase 1 (Completed):** Data collection script, cleaning, and preliminary EDA.
* **Phase 2 (Current):** Statistical Hypothesis Testing on the sample dataset.
* **Phase 3 (Upcoming):** Implementing Machine Learning models (Random Forest) to predict trade success based on politician attributes.

## Key Findings (Preliminary)

*Based on the analysis of the initial dataset (referenced in `analysis.ipynb`):*

1.  **Positive Returns:** The sample data indicates a positive average return for selected high-profile trades (e.g., Nancy Pelosi's tech trades).
2.  **Statistical Significance:** Preliminary t-tests suggest that these returns are statistically significant ($p < 0.05$) for the tested window, though a larger dataset is needed for final confirmation.
3.  **Sector Focus:** Tech giants (AAPL, NVDA, MSFT) constitute the majority of high-volume trades.

## Project Files

* `analysis.ipynb`: The Jupyter Notebook containing data fetching, cleaning, visualization (EDA), and hypothesis testing code.
* `requirements.txt`: List of Python libraries required to run the analysis.
* `README.md`: Project documentation.

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/baristurkcann/Congress-Trading-Analysis-DSA210-Project.git
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the analysis:**
    Open `analysis.ipynb` in Jupyter Lab or Google Colab and run all cells to reproduce the charts and test results.



    ## AI Usage Declaration
Per the course academic integrity policy, I explicitly document the use of AI tools in this project. I utilized **Gemini (LLM)** as a productivity assistant for the following specific tasks:

1.  **Code Debugging & Library Syntax:**
    * I used AI to troubleshoot connection errors with the `yfinance` library (specifically handling the `Empty DataFrame` and `MultiIndex` issues).
    * **Prompt used:** *"How to handle yfinance download errors and clean multi-level column headers in Python?"*

2.  **Documentation Formatting:**
    * I generated the Markdown table templates for the "Data Sources" section to ensure clean formatting.
    * **Prompt used:** *"Create a Markdown table template for describing data sources."*

3.  **Statistical Concept Verification:**
    * I verified the syntax for `scipy.stats.ttest_1samp` to ensure correct hypothesis testing parameters.

4.  **Formatting & Style Refinement:**
    * Used to generate Markdown table templates and **refine the professional tone** of the documentation to meet academic standards.
    * **Prompt used:** *"Help me format the README file and polish the language for a data science project proposal."*

**Statement of Originality:** All logical structuring, hypothesis formulation, and final code execution/verification were performed by me. The AI outputs were used as code snippets and technical references, which I then integrated and refined.
