Here are all the codes and reports of my Projects in the FIN3080 course. All Projects are implemented using Python. The scores of my four Projects are all full marks.

The FIN3080 assignments require a blend of financial econometrics and data science skills applied to CSMAR-sourced A-share market data.
# Project 1
This assignment mandates a comprehensive empirical analysis of A-share market firms listed on the main board (including SME) and GEM board (ChiNext and STAR) using the CSMAR database. The tasks require:

1. **Data Extraction and Ratio Computation**: Retrieve longitudinal data spanning January 2000 to September 2023 (monthly stock prices, returns, market value of tradable shares) and 2000Q1 to 2023Q3 (quarterly financial metrics: total assets, liabilities, EPS, ROA, ROE, R&D expenses, plus establishment date and market type). Compute:
	- Monthly P/E (price-to-earnings) and P/B (price-to-book) ratios using the latest quarterly accounting data aligned with monthly closing prices.
	- Quarterly R&D expense-to-total asset ratios and firm age (time elapsed since establishment).

2. **Descriptive Statistics and Comparative Analysis**: Generate summary statistics (N, mean, median, 25th/75th percentiles, standard deviation) for stock returns, P/E, P/B, ROA, ROE, R&D expense ratios, and firm ages, segmented by market type. Conduct a comparative evaluation of these metrics across the main board and GEM board, discussing heterogeneity and trends.

3. **Time-Series Visualization and Investment Strategy**: Construct and plot median P/E ratio time-series by market type from 2000 to September 2023. Assess:
	- Investment viability in each market as of September 2023 based on P/E dynamics.
	- Formulate a trading strategy leveraging index ETFs, exploiting observed P/E patterns.

4. **Longitudinal Performance Tracking**: Using provided data (problem3_data.csv) for main board firms (2011–2020, excluding financials), compute annual median ROE and total revenue growth rates. Plot decaying time-series of the percentage of firms consistently exceeding these medians over the period, reflecting survivorship and performance persistence.
# Project 2
This assignment focuses on advanced financial econometrics and portfolio construction for A-share market firms over December 2009 to December 2024 utilizing CSMAR data. The requirements are:

1. **Data Retrieval and P/B Derivation**: Extract monthly stock closing prices and returns (Dec. 2009–Dec. 2024), quarterly ROE-TTM and net assets per share (2009Q3–2024Q4), and daily stock volatility (250-day log-return variance at 2010/12/31). Derive monthly P/B ratios (closing price divided by latest net assets per share) and apply a 5th–95th percentile filter to exclude outliers.

2. **Cross-Sectional Regression**: For December 2010, estimate a cross-sectional OLS regression of P/B ratios on ROE-TTM (2010Q4) and stock volatility (2010/12/31):
   - $P/B_i = \alpha + \beta_1 ROE_i + \beta_2 \text{Stock Volatility}_i + \epsilon_i$.
   - Report coefficients, statistical significance, and interpret economic implications (e.g., value relevance of profitability and risk).

3. **Decile Portfolio Construction and Performance**: For each month (Jan. 2010–Dec. 2024), sort firms by prior-month P/B ratios into deciles, forming ten equal-weighted portfolios rebalanced monthly. Compute monthly portfolio returns:
   - $r_{i,t}^p = \frac{1}{N_{i,t}} \sum_{j=1}^{N_{i,t}} r_{j,t}^s$, where $r_{j,t}^s$ is the stock return and $N_{i,t}$ is the number of stocks in decile $i$.
   - Visualize average returns across the ten portfolios via a bar chart and analyze return patterns (e.g., value vs. growth effects).
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
