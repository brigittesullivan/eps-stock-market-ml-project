# eps-stock-market-ml-project
Machine learning project that predicts the percent change in stock price after next earnings event for public companies

## Project Goal

* Predict percent change in stock price after next earnings event for all companies using the date and stock price as inputs
* There will be one record per earning event date per company

## Scope

<table>
  <tr>
   <td><strong>In Scope</strong>
   </td>
   <td><strong>Out of Scope</strong>
   </td>
  </tr>
  <tr>
   <td>Minimum Viable Product (MVP):
<ul>

<li>Only stocks listed in “all_tickers-with-options.csv” list

<li>ML model that predicts percent change of any stock after earnings release

<li>Using publicly available data for previous 4 Earnings releases for each company from 2023

<li>One cycle of optimization / tuning

<li>Measure and interpretation ML model’s effectiveness at predicting target variable (accuracy) using one metric

<p>
Time permitting:
<ul>

<li>Additional rounds of optimization to increase accuracy

<li>Measure and interpretation ML model’s effectiveness at predicting target variable (accuracy) using multiple metrics

<li>Ability to input custom dates/stock to generate ad hoc predictions
</li>
</ul>
</li>
</ul>
   </td>
   <td>
<ul>

<li>Custom ML Model for each stock  

<li>ML model that considers a companies full / continuous stock history to develop predictions for next earnings release

<li>Deployment for re-use, interactivity

<li>model satisfying pre-determined accuracy performance targets

<li>Straddle return data provided in “EarningsStraddles_RecentEarnings_Results.csv”

<li>Unit testing

<li>Time drift evaluation
</li>
</ul>
   </td>
  </tr>
</table>


## Process:

<table>
  <tr>
   <td><strong>Inputs</strong>
   </td>
   <td><strong>Processing</strong>
   </td>
   <td><strong>Output</strong>
   </td>
  </tr>
  <tr>
   <td>Date of previous 4 EPS releases for each stock
<p>
Target date (same day as EPS or next market open day)
<p>
Stock price 1 market day prior to EPS release date (high, open, low, close) 
<p>
Stock price after to EPS release date
<p>
(high, open, low, close) 
   </td>
   <td> 
   <p>
   Cleaning all source data
   <p>
   Remove outliers
   <p>
   Transforming 
<p>
ML Model (Regression Tree)
<p>
Tuning (GridSearchCV)
</li>
</ul>
   </td>
   <td>Predicted % change in stock price based on stock price and earnings release date
   </td>
  </tr>
</table>


## Assumptions:

* Work outlined in this document will be completed by a single learner 
* Project scope and expectations will be reasonable for a single learner to complete within the allotted time, including skipping milestones outlined in Riipen.
* Project may not follow the exact milestones in Riipen, and there is no requirement to do so
* Available data sets will be used regardless of whether they possess the characteristics required for developing a strong (accurate) machine learning model. Best efforts will be made to optimize within the constraints outlined in this document


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
   d. Optimize Regression Tree Model - use mean absolute error to evaluate improvement
   
   
## Findings: 

All models performed relatively the same. 

### Mean Absolute Error for each model:

{{ TABLE }}