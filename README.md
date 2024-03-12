# eps-stock-market-ml-project
Machine learning project that predicts the percent change in stock price after next earnings event for public companies


## Approach: 
1. Aquire data:
   a. Companys of Interest - provided ('all_tickers-with-options.csv')
   b. Earnings Events dates - provided ('confirmed_earnings.csv') 
   c. Earnings Per Share - sourced using yfinance API based on earnings events dated in "b"
   d. Stock Price History - sourced using XXXX API based on companies in "a"
2. Merge and join all aquired data into one data set
3. Perform EDA to understand high-level the nature of the data
4. Cleaning - remove missing values, remove outliers, remove records with no associated EPS data. 
5. Modelling:
   * Used mean absolute error to compare model strength accross each model iteration. 
   a. Baseline Statistical Model - understand summary stats of the data
   b. Baseline Linear Regression Model - generate mean absolute error for test and evaluation data sets and interpret results
   c.  Regression Tree Model - generate mean absolute error for test and evaluation data sets and interpret results. Regression tree model chosen since it is known to be able to handle non-linear data well.
   d. Optimize Regression Tree Model - use mean absolute error to 
   
   
## Findings: 

In the end, all models performed relatively the same. 