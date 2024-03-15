# Data Science Stock Earnings Project  </br>
Completed during a Data Science Internship with Vyop Software </br>
Developed by: Brigitte Sullivan</br>
Manager: VYOP Software </br>
Submitted on: March 15, 2024 </br>

## Project Goal
Predict the percent change in stock price after next the earnings event for all companies using the date and stock price as inputs using a Machine Learning (ML) model
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

<li>Using publicly available data for the previous 4 Earnings releases for each company from 2023

<li>One cycle of optimization/tuning

<li>Measure and interpret the ML model’s effectiveness at predicting target variable (accuracy) using one metric

<p>
Time permitting:
<ul>

<li>Additional rounds of optimization to increase accuracy

<li>Measure and interpret the ML model’s effectiveness at predicting target variable (accuracy) using multiple metrics

<li>Ability to input custom dates/stock to generate ad hoc predictions
</li>
</ul>
</li>
</ul>
   </td>
   <td>
<ul>

<li>Custom ML Model for each stock  

<li>ML model that considers a company's full/continuous stock history to develop predictions for the next earnings release

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

* Work outlined in this document will be completed by a single learner, rather than a team of learners
* Project scope and expectations will be reasonable for a single learner to complete within the allotted time, including skipping milestones outlined in Riipen.
* The project may not follow the exact milestones in the Riipen platform as they are optional
* Available data sets will be used regardless of whether they possess the characteristics required for developing a strong (accurate) machine learning model. Best efforts will be made to optimize within the constraints outlined in this document


## Approach: 
### 1. Aquire data: </br>
   a. Companys of Interest - provided ('all_tickers-with-options.csv') </br>
   b. Earnings Events dates - provided ('confirmed_earnings.csv')  </br>
   c. Earnings Per Share - sourced using yfinance API based on earnings events dated in "b" </br> 
   * Notebook link: [1_before_after_eps_days.ipynb](https://github.com/brigittesullivan/eps-stock-market-ml-project/blob/main/1_loading_before_after_eps_days.ipynb) </br>
   * Notebook link: [3_loading_earnings_amounts.ipynb](https://github.com/brigittesullivan/eps-stock-market-ml-project/blob/main/3_loading_earnings_amounts.ipynb)</br>

   d. Stock Price History - sourced using yfinance API based on companies in "a" </br>
   * Notebook link: 
   [2_loading_stock_price_history.ipynb](https://github.com/brigittesullivan/eps-stock-market-ml-project/blob/main/2_loading_stock_price_history.ipynb)

### 2. Merge and join all acquired data into one data set </br>
   * Notebook Link: [4_merge_eps_percent_change.ipynb](https://github.com/brigittesullivan/eps-stock-market-ml-project/blob/main/4_merge_eps_percent_change.ipynb)
   
### 3. Perform EDA to understand high-level the nature of the data

### 4. Cleaning - remove missing values, remove outliers, remove records with no associated EPS data. 

### 5. Modelling: </br>
   Used mean absolute error to compare model strength across each model iteration.  </br>
   a. Baseline Statistical Model - understand summary stats of the data</br>
   b. Baseline Linear Regression Model - generate the mean absolute error for test and evaluation data sets and interpret results</br>
   c.  Regression Tree Model - generate the mean absolute error for test and evaluation data sets and interpret results. The regression tree model was chosen since it is known to be able to handle non-linear data well. </br>
   d. Optimize Regression Tree Model - use mean absolute error to evaluate improvement </br>
   * Notebook Link: [5_EDA_Modelling.ipynb](https://github.com/brigittesullivan/eps-stock-market-ml-project/blob/main/5_EDA_Modelling.ipynb)
   
   
## Findings: 

Mean Absolute Error (MAE): average distance between the actual value and the predicted value for percent change. 

The models are not overfit as the evaluation MAE is greater than the training MAE.

All models performed relatively the same. where the predicted percent change is off by ~5% (e.g., if the actual value is +10% model might predict a +15% change.)

### Mean Absolute Error for each model:

|           |Train                  |Eval               |
|-----------|-------------|-------------------|
|Decision Tree             |0.04534    |0.04847|
|Linear Regression         |0.04570    |0.04833|
|Decision Tree (tuned)     |0.04543    |0.04833|


## Next steps:
Thoughts for the next iteration of this modeling project:

* look at other stock market features and find stronger linear relationships to use for predictions. For instance,  Would there be an improvement to the performance of the model if incorporated:
   * premarket or postmarket announcement (as 1 for premarket, 0 for postmarket)?
   * month announced
day of the week announced
   * straddle returns options data into the dataset
Select the highest priority stocks to evaluate and develop one one model per stock, 
* integrating time series forecasting







