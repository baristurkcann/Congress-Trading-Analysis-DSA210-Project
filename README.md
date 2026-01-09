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
     `AdjReturn_1y = Return_stock − Return_SPY`
   
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

<img width="895" height="432" alt="image" src="https://github.com/user-attachments/assets/6f5e319d-fcdf-426d-b0d5-7be48b778e6a" />


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
<img width="1057" height="684" alt="image" src="https://github.com/user-attachments/assets/b5ee643b-90fe-4aed-b219-01fb49b70407" />

## Conclusion

This project examined whether U.S. congressional stock trades exhibit abnormal performance relative to the market using two complementary analytical approaches with different scopes and time horizons.

In the first phase of the analysis, a short-term event-study style approach was applied using a small, manually curated dataset and a 30-day post-transaction window. This analysis focused on specific, high-profile trades and was designed to closely inspect immediate post-trade market reactions. Under this narrow and short-term framework, the results suggested positive benchmark-adjusted returns for certain individuals, and one-sample t-tests indicated statistical significance. These findings are consistent with the intuition that short-term price movements may reflect timely information advantages or market anticipation effects following specific trades.

In contrast, the second phase employed a broader and more systematic approach. A large-scale dataset covering congressional purchase transactions between 2014 and 2024 was used, with forward returns calculated over a 252-trading-day (approximately one-year) horizon. This phase incorporated both traditional statistical testing and machine learning classification models. The benchmark-adjusted one-year returns were centered close to zero, with confidence intervals spanning zero and negligible effect sizes. Furthermore, machine learning models (logistic regression) performed close to baseline and random classification, indicating limited predictive signal in the observable features such as party affiliation, chamber, or trade size.

Additionally, the results demonstrate that inference is highly sensitive to both sample composition and time horizon. When the analysis focuses on a small, manually curated subset of trades and a short 30-day window, particularly involving high-profile individuals such as Nancy Pelosi, hypothesis test outcomes may change and appear statistically significant. This suggests that certain individuals can exhibit short-term, trade-specific effects that are not representative of the broader population. However, when the dataset is expanded to include a large number of trades between 2014 and 2024 and the evaluation horizon is extended to one year, these effects no longer persist. In both short-term and long-term analyses, no statistically significant differences are observed between political parties. This indicates that while individual-level behavior may occasionally generate localized patterns, party affiliation does not systematically explain benchmark-adjusted trading performance.


**30 DAY STATS**

<img width="869" height="491" alt="image" src="https://github.com/user-attachments/assets/6e9500a6-0c26-41b4-a07b-8c2196016745" />
<img width="839" height="458" alt="image" src="https://github.com/user-attachments/assets/71efe8f8-75f4-40ed-a7f1-72cd6091de7d" />
<img width="820" height="456" alt="image" src="https://github.com/user-attachments/assets/9587942f-d84d-4d00-be24-298bda8a75ef" />

**1 YEAR ML STATS**

<img width="836" height="443" alt="image" src="https://github.com/user-attachments/assets/e2e0ab8b-5223-4fb2-9791-940284b8fc5c" />
<img width="563" height="510" alt="image" src="https://github.com/user-attachments/assets/b52b6251-6f1f-4521-8741-908cf36fa14e" />

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
