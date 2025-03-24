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
   - \( P/B_i = \alpha + \beta_1 ROE_i + \beta_2 \text{Stock Volatility}_i + \epsilon_i \).
   - Report coefficients, statistical significance, and interpret economic implications (e.g., value relevance of profitability and risk).

3. **Decile Portfolio Construction and Performance**: For each month (Jan. 2010–Dec. 2024), sort firms by prior-month P/B ratios into deciles, forming ten equal-weighted portfolios rebalanced monthly. Compute monthly portfolio returns:
   - \( r_{i,t}^p = \frac{1}{N_{i,t}} \sum_{j=1}^{N_{i,t}} r_{j,t}^s \), where \( r_{j,t}^s \) is the stock return and \( N_{i,t} \) is the number of stocks in decile \( i \).
   - Visualize average returns across the ten portfolios via a bar chart and analyze return patterns (e.g., value vs. growth effects).