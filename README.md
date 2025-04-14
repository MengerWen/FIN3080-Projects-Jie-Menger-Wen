Here are all the codes and reports of my Projects in the FIN3080 course. All Projects are implemented using Python. The scores of my four Projects are all full marks.

The FIN3080 assignments require a blend of financial econometrics and data science skills applied to CSMAR-sourced A-share market data.
# Project 1

## Overview
This assignment mandates a comprehensive empirical analysis of financial data from the China Stock Market & Accounting Research (CSMAR) database, focusing on A-share listed firms. It requires students to extract, process, and analyze multi-frequency financial data (monthly stock metrics and quarterly accounting indicators) to compute valuation ratios, generate summary statistics, and perform time-series analysis. The tasks emphasize proficiency in data wrangling, statistical summarization, and financial interpretation.

## Q1: Data Extraction and Ratio Computation
- **Data Requirements**: Students must access CSMAR’s Stock Trading, Financial Statements, and Financial Indicators databases to retrieve:
  - **Monthly Data (Jan 2000–Sep 2023)**: Stock prices, stock returns, and market value of tradable shares for all A-share firms.
  - **Quarterly Data (2000Q1–2023Q3)**: Total assets, total liabilities, earnings per share (EPS), return on assets (ROA), return on equity (ROE), and R&D expenses.
  - **Static Data**: Establishment date and market type (main board vs. GEM board, where main board includes SME, and GEM includes ChiNext and STAR).
- **Task (a) – Ratio Calculation**:
  - Compute **monthly P/E ratios** as $P/E_{i,t} = \frac{\text{Closing Price}_{i,t}}{\text{EPS}_{i,q}}$, aligning monthly prices with the most recent quarterly EPS.
  - Compute **monthly P/B ratios** as $P/B_{i,t} = \frac{\text{Closing Price}_{i,t}}{\text{Book Value per Share}_{i,q}}$, where book value per share is derived from total assets minus total liabilities divided by total shares outstanding, using the latest quarterly data.
  - Compute **quarterly R&D expense/total asset ratios** as $\frac{\text{R&D Expenses}_{i,q}}{\text{Total Assets}_{i,q}}$.
  - Compute **quarterly firm ages** as the time difference (in years or quarters) between the current date and the establishment date.
- **Task (b) – Summary Statistics**:
  - Generate descriptive statistics (number of observations, mean, median, 25th percentile, 75th percentile, standard deviation) for monthly stock returns, P/E ratios, P/B ratios, and quarterly ROA, ROE, R&D expense/total asset ratios, and firm ages.
  - Segment the statistics by market type (main board vs. GEM board).
  - Conduct a comparative analysis of the distributional properties across markets, discussing implications for market efficiency, firm profitability, and investment characteristics.

## Q2: Time-Series Analysis and Investment Strategy
- **Data Utilization**: Leverage the computed P/E ratios from Problem 1.
- **Task**:
  - Construct two time-series of median P/E ratios by market type (main board vs. GEM) from Jan 2000 to Sep 2023 and plot them.
  - **Analysis (i)**: Evaluate the investment attractiveness of each market as of Sep 2023, considering the P/E trends (e.g., overvaluation signals if P/E is elevated relative to historical norms).
  - **Analysis (ii)**: Propose a trading strategy using index ETFs (e.g., CSI 300 for main board, ChiNext Index for GEM) based on P/E dynamics, such as a momentum or mean-reversion approach (e.g., shorting high P/E markets and longing low P/E markets).

## Q3: Longitudinal Performance Analysis
- **Data**: Use the provided `problem3_data.csv` containing annual ROE and total revenue for main board firms (excluding financials) from 2011 to 2020.
- **Task**:
  - Calculate **annual median ROE** and **total revenue growth rate** (defined as $\frac{\text{Total Revenue}_t - \text{Total Revenue}_{t-1}}{\text{Total Revenue}_{t-1}}$) for each year.
  - For each metric, compute the percentage of firms consistently exceeding the annual median from 2011 onward (e.g., in 2012, firms above median in both 2011 and 2012; in 2013, firms above median in 2011–2013, etc.).
  - Plot two decaying time-series showing these percentages for ROE and revenue growth rate.
- **Interpretation**: Discuss the persistence of outperformance and implications for firm quality or market competition.
# Project 2
## Overview
This assignment extends the empirical analysis to a longer horizon (2009–2024) and introduces cross-sectional regression and portfolio construction. It requires advanced statistical modeling and portfolio performance evaluation using CSMAR data, with a focus on P/B ratios as a valuation metric.

## Data Extraction and Preprocessing
- **Data Requirements**:
  - **Monthly Data (Dec 2009–Dec 2024)**: Stock closing prices and returns (without cash dividend reinvestment) from the Individual Stock Trading table.
  - **Quarterly Data (2009Q3–2024Q4)**: ROE-TTM (trailing twelve months) and net assets per share from the Financial Indicator table.
  - **Daily Data (Dec 31, 2010)**: Stock volatility (250-day log return volatility) from the Stock Market Derivative Index table.
- **P/B Ratio Derivation**: Compute monthly P/B ratios as $P/B_{i,t} = \frac{\text{Closing Price}_{i,t}}{\text{Net Assets per Share}_{i,q}}$ from Jan 2010 to Dec 2024, using the latest quarterly net assets per share. Exclude outliers by trimming P/B ratios below the 5th percentile or above the 95th percentile.

## Q1: Cross-Sectional Regression
- **Task**: For all A-share firms at Dec 2010, estimate the cross-sectional regression:
  $$
  P/B_i = \alpha + \beta_1 \text{ROE}_i + \beta_2 \text{Stock Volatility}_i + \epsilon_i
  $$
  where:
  - $P/B_i$: P/B ratio at Dec 2010.
  - $\text{ROE}_i$: ROE-TTM at 2010Q4.
  - $\text{Stock Volatility}_i$: 250-day volatility at Dec 31, 2010.
- **Deliverables**: Report coefficients ($\alpha, \beta_1, \beta_2$), standard errors, t-statistics, R-squared, and interpret the economic significance (e.g., whether higher ROE or volatility drives P/B ratios).

## Q2: Portfolio Construction and Performance
- **Task**:
  - For each month from Jan 2010 to Dec 2024, sort firms by prior-month P/B ratios and form ten equal-weighted portfolios based on deciles (D0 to D10, where D0 is the minimum and D10 the maximum).
  - Calculate monthly portfolio returns as:
    $$
    r_{i,t}^p = \frac{1}{N_{i,t}} \sum_{j=1}^{N_{i,t}} r_{j,t}^s
    $$
    where $N_{i,t}$ is the number of stocks in portfolio $i$ at time $t$, and $r_{j,t}^s$ is the monthly return of stock $j$.
  - Plot a bar chart of average portfolio returns over the period and analyze patterns (e.g., value vs. growth effects).
- **Interpretation**: Discuss whether low P/B (value) or high P/B (growth) portfolios outperform, linking findings to market efficiency or behavioral finance.
# Project 3
## Q1: CSI 300 Index Return Analysis

### Overview
This task requires an empirical analysis of the CSI 300 index’s daily closing data to derive monthly returns, compute distributional statistics, visualize the return distribution, and assess normality, emphasizing statistical rigor in financial time-series analysis.

### Requirements
- **Data Extraction**: Retrieve daily Closing Index values for the CSI 300 from CSMAR’s China Stock Market Series/Stock Trading/Market Index table over Jan 1, 2006, to Dec 31, 2023.
- **Task (a) – Monthly Returns and Statistics**:
  - Compute monthly returns as $R_{k,t} = \frac{I_{k,t}}{I_{k,t-1}} - 1$, where $I_{k,t}$ is the closing index at month-end $t$.
  - Calculate summary statistics: mean, standard deviation, skewness, and kurtosis for the monthly return series to characterize central tendency, volatility, asymmetry, and tail behavior.
- **Task (b) – Visualization**:
  - Plot a histogram of monthly CSI 300 returns to visually inspect the empirical distribution.
- **Task (c) – Normality Assessment**:
  - Analyze whether the return distribution conforms to normality, using statistical metrics (e.g., skewness ≈ 0, kurtosis ≈ 3 for normal distribution) and visual evidence from the histogram. Discuss implications for financial modeling (e.g., violations of normality affecting risk models).

## Q2: CAPM Replication in Chinese A-Share Market

### Overview
This task involves replicating an empirical test of the Capital Asset Pricing Model (CAPM) as adapted by Chen et al. (2019) for the Chinese A-share market, focusing on cross-sectional and time-series regressions to evaluate the risk-return relationship, following the methodology of Jensen, Black, and Scholes (1972).

### Requirements
- **Data Extraction**:
  - **Task (a)**: Download weekly Returns With Cash Dividend Reinvested for all A-share mainboard stocks from CSMAR’s China Stock Market Series/Stock Trading/Individual Stock Trading table, spanning the first week of 2017 to the last week of 2022.
  - **Task (b)**: Compute weekly market returns as the equal-weighted average of individual stock returns across mainboard stocks for each week.
  - **Task (c)**: Import weekly risk-free rates from the provided Excel file (`weekly_risk_free_rate.xlsx`), using the “risk_free_return” column as a proxy for the 1-year government bond yield.
- **Task (d) – CAPM Replication**:
  - Replicate Tables 2 and 3 from Chen et al. (2019) using the 2017–2022 data, adapting their methodology:
    - **Table 2 (Time-Series Regression)**:
      - Divide the sample into three equal periods (each ~104 weeks).
      - Period 1: Estimate individual stock betas ($\beta_i$) via time-series regression: $r_{i,t} = \alpha_i + \beta_i r_{m,t} + \epsilon_{i,t}$.
      - Sort stocks by $\beta_i$, form 10 equal-weighted portfolios, and estimate portfolio betas ($\beta_p$) in Period 2 via: $r_{p,t} - r_{f,t} = \alpha_p + \beta_p (r_{m,t} - r_{f,t}) + \epsilon_{p,t}$.
      - Report $\alpha_p$, $\beta_p$, t-statistics, and $R^2$ for each portfolio.
    - **Table 3 (Cross-Sectional Regression)**:
      - Use Period 2 portfolio betas ($\beta_p$) as the independent variable and Period 3 average excess portfolio returns ($\overline{r_{p,t} - r_{f,t}}$) as the dependent variable in: $\overline{r_{p,t} - r_{f,t}} = \gamma_0 + \gamma_1 \beta_p + \epsilon_p$.
      - Report $\gamma_0$, $\gamma_1$, t-statistics, $R^2$, F-statistic, and p-value.
  - Discuss whether the results support CAPM’s prediction of a positive risk-return relationship and compare findings qualitatively to Chen et al. (2019), acknowledging data period differences.
