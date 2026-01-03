# DSA210-Congressional Trading – BARIŞ TÜRKCAN

**Analyzing the Impact of US Congressional Stock Trading on Market Prices**

A data science project examining whether publicly disclosed stock trades by members of the U.S. Congress are associated with benchmark-adjusted returns, using statistical analysis and machine learning methods.


## Contents

- [Project Overview](#project-overview)  
- [Motivation](#motivation)  
- [Data Sources](#data-sources)  
- [Research Questions & Hypotheses](#research-questions--hypotheses)  
- [Methodology](#methodology)  
- [Analysis Plan](#analysis-plan)  
- [Key Findings](#key-findings)  
- [Machine Learning Extension](#machine-learning-extension)  
- [How to Run](#how-to-run)  
- [AI Usage Declaration](#ai-usage-declaration)  



## Project Overview

This project investigates whether stocks purchased by U.S. Senators and Representatives systematically outperform the market after disclosure. By merging congressional trading disclosures with historical stock price data, the analysis evaluates benchmark-adjusted post-transaction returns relative to the S&P 500 (SPY).

The goal is not to claim insider trading, but to empirically test whether observable trading behavior is associated with abnormal performance.



## Motivation

The intersection of politics and financial markets raises important ethical and economic questions:

- **Market Fairness:** Do policymakers exhibit systematic trading advantages over the market?
- **Political Ethics:** Can publicly disclosed trades be linked to later financial performance?
- **Data Science Perspective:** Can publicly available features explain post-trade returns?



## Data Sources

### 1. Congressional Trading Data
- **Source:** Quiver Quant  
- **Format:** Excel export obtained from Quiver Quant, containing congressional purchase transactions between **2014 and 2024**
- **Content:** Ticker, transaction date, transaction type, trade size range, party affiliation, chamber, and state  

### 2. Market Data
- **Source:** Yahoo Finance (`yfinance`)  
- **Content:** Daily adjusted closing prices for individual stocks and SPY (S&P 500 ETF)



## Research Questions & Hypotheses

### 1. Benchmark-Adjusted Returns
**Research Question:**  
Do stocks purchased by members of Congress generate positive benchmark-adjusted returns over a one-year horizon?

- **Null Hypothesis (H₀):**  
  The mean 252-day benchmark-adjusted return is less than or equal to zero (μ ≤ 0).
- **Alternative Hypothesis (H₁):**  
  The mean 252-day benchmark-adjusted return is positive (μ > 0).


### 2. Party-Based Performance
**Research Question:**  
Is there a significant difference in benchmark-adjusted returns between Democratic and Republican members?

- **Null Hypothesis (H₀):**  
  Mean returns are equal across parties.
- **Alternative Hypothesis (H₁):**  
  Mean returns differ between parties.


## Methodology

The analysis follows an event-study-inspired framework:

1. **Data Cleaning:**  
   - Only purchase transactions are included  
   - Invalid dates and non-equity tickers are removed  
   - Analysis period restricted to ensure sufficient price coverage  

2. **Return Construction:**  
   - Forward returns computed over **252 trading days**  
   - Benchmark-adjusted return defined as:  
     \[
     \text{AdjReturn}_{1y} = R_{\text{stock}} - R_{\text{SPY}}
     \]

3. **Statistical Testing:**  
   - One-sample t-test against zero benchmark-adjusted return  
   - Two-sample Welch t-test for party comparison  

4. **Exploratory Data Analysis:**  
   - Return distributions  
   - Party-level comparisons  
   - Normality diagnostics (Q–Q plots)



## Analysis Plan

- **Phase 1:** Data collection and preprocessing  
- **Phase 2:** Statistical hypothesis testing and EDA  
- **Phase 3:** Machine learning classification to test predictability  


## Key Findings

Based on the final dataset (approximately 2,500 valid observations):

- Mean benchmark-adjusted returns are close to zero  
- One-sample t-tests fail to reject the null hypothesis at conventional significance levels  
- No statistically significant difference is observed between parties  
- Effect sizes are economically small  

These results suggest no systematic abnormal performance based on publicly observable congressional trading data.



## Machine Learning Extension

To complement the statistical analysis, a binary classification task was implemented.

- **Target:**  
  Whether a trade outperforms the market over one year (AdjReturn₁ᵧ > 0)
- **Models:**  
  - Baseline (majority-class classifier)  
  - Logistic Regression
- **Features:**  
  Party affiliation, chamber, state, and reported trade size category

### Results
- Logistic Regression performance is close to the baseline model  
- ROC-AUC is approximately **0.50**, indicating no meaningful predictive power  
- Results are consistent with the statistical findings



## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/baristurkcann/Congress-Trading-Analysis-DSA210-Project.git
 **Note:** This project requires the file `congress-trading-all.xlsx`, which is an Excel export obtained from Quiver Quant containing congressional purchase transactions between 2014–2024. The file must be placed in the root directory of the repository before running the notebook.

2. Install dependencies:
pip install -r requirements.txt

3. Run the analysis:
   - Open analysis.ipynb
   - Execute all cells to reproduce the results

### AI Usage Declaration

Per the course academic integrity policy, I explicitly document the use of AI tools in this project. I utilized **Gemini (LLM) and ChatGPT** as a productivity assistant for the following specific tasks:

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
