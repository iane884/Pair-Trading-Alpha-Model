# Pair Trading Alpha Model Using Cointegration

## Project Overview
This project demonstrates a pair trading algorithm based on cointegration, which allows us to identify pairs of stocks that are likely to revert to a mean relationship over time. By exploiting these mean-reverting pairs, we can enter long-short positions and potentially profit as the prices converge. The project covers concepts of pair trading, data retrieval, and the use of statistical tests for cointegration, with instructions to complete each part of the algorithm.

## Background Information

### What is Pair Trading?
Pair trading is a strategy that involves identifying two stocks that typically move together. When the price ratio of the two stocks diverges from its historical mean, we enter trades expecting this relationship to eventually return to the mean. This is achieved by buying the undervalued stock and shorting the overvalued one.

### What is Cointegration?
Cointegration measures the relationship between two time-series datasets, identifying if they move in sync over time. In this project, we use cointegration to find pairs of stocks within the S&P 500 Technology sector that demonstrate a mean-reverting relationship, making them suitable candidates for pair trading.

## Coding the Pair Trading Algorithm
This guide explains how to code the pair trading algorithm by providing step-by-step instructions. Each section includes explanations of the task and hints for implementation.

## Steps Completed

### Grabbing Data
**Objective:** Collect historical data for S&P 500 Technology sector stocks.  
**Implementation:** A web scraper extracts stock tickers from Wikipedia’s S&P 500 list, filtering for Information Technology companies. Using yfinance, the script then retrieves one year of historical adjusted close prices for these stocks, adjusted for splits and dividends.

### Identifying Pairs Using Cointegration
**Objective:** Identify stock pairs within the sector that demonstrate cointegration.  
**Implementation:**
- Generated all possible pairs of stocks from the Technology sector.
- Used the statsmodels cointegration test to determine if each pair is statistically cointegrated. Pairs with significant t-statistics and p-values are flagged as tradeable.

### Trade Signal Generation
**Objective:** Determine entry points for trades based on the price ratio of cointegrated pairs.  
**Implementation:**
- Calculated the ratio between the prices of each cointegrated pair to identify divergence points.
- Applied the z-score function to standardize these ratios and create a signal function that flags extreme values (±1.5 standard deviations) as buy or sell signals.

## Further Implementation Ideas

### Testing the Model
Suggested ways to test the model, including:
- **Backtesting:** Simulating trades using historical data to evaluate profitability.
- **Classification:** Evaluating hit rates by checking if trades revert after signals.
- **Rolling Cointegration for Real-Time Trading:** Recommended using a rolling window to calculate cointegration, ensuring that signals are generated based on information available at the time, avoiding lookahead bias.

## Moving Forward

### Testing
With the generated signals, there are two potential ways to test the model’s effectiveness:
- **Backtest:** Simulate trades using historical data to calculate the overall returns.
- **Classify:** Assess the accuracy of the signals by calculating the rate of mean reversion following the entry points.

### Revisiting the Model
Consider using a rolling window for cointegration calculations to avoid forward-looking bias. Instead of using future data to calculate cointegration, analyze only past data up to the signal date.
