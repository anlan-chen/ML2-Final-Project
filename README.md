# ML2-Final-Project

## 1. Background & Motivation

Electricity prices in Poland exhibit substantial volatility and pronounced intraday patterns. Short-term price movements are driven by fluctuating demand, supply conditions, and market constraints, which makes accurate forecasting challenging, particularly during peak demand periods.

With the availability of detailed day-ahead electricity price data published by Polskie Sieci Elektroenergetyczne (PSE) and the ENTSO-E Transparency Platform, it is possible to model short-term price dynamics using historical information. These datasets provide a realistic basis for evaluating machine learning methods in an applied time-series forecasting context.

In this course, we studied regression-based and tree-based machine learning models, with a particular focus on gradient boosting techniques and hyperparameter tuning. These methods are well suited for capturing nonlinear relationships and complex temporal patterns in structured data.

The motivation of this project is to apply gradient boosting models to electricity price forecasting in Poland, evaluate their predictive performance relative to simple benchmarks, and analyze their strengths and limitations. Special attention is given to model behavior during peak and low-price periods, where forecasting errors tend to be largest and most economically relevant.

## 2. Research Questions / Goals

RQ1:
How accurately can machine learning regression models predict hourly electricity prices in Poland using historical price information?

RQ2:
Do gradient boosting models outperform a naive benchmark and linear regression in out-of-sample electricity price forecasting?

RQ3:
Does hyperparameter tuning improve predictive performance, and does it reduce systematic errors during peak and trough price periods?

## 3. Data
This project uses hourly electricity price data from official European sources.

Historical day-ahead electricity prices for Poland from 2020 to 2025 are obtained from the ENTSO-E Transparency Platform.


3.1 Date range

Training period: January 2020 – December 2024

Test period: January 2025 – December 2025

The test period is strictly out-of-sample and is not used in model training or tuning.


3.2 Variables

## Target variable

Hourly day-ahead electricity price (EUR/MWh)

## Data processing

Both ENTSO-E price data are originally available at a 15-minute resolution.

Prices are aggregated to an hourly frequency using simple hourly averages to ensure consistency.

All timestamps are aligned to a common hourly time grid.

## Explanatory variables： 

Lagged electricity prices (e.g. 1-hour, 24-hour, and 168-hour lags)

Rolling statistics (rolling mean and rolling standard deviation)

3.3 Calendar-based features:
- Hour of day
- Day of week
- Weekend indicator

## 4. Methods

Electricity price forecasting is formulated as a supervised time-series regression problem. The primary focus is on gradient boosting models, which are capable of capturing nonlinear relationships and interactions between lagged prices and temporal features.

The dataset is split chronologically to reflect a realistic forecasting setup. Hourly data from 2020 to 2024 are used for training, while 2025 is reserved as a strictly out-of-sample test set. No future information is used during model training or feature construction.

As baseline approaches, a naive lag-based benchmark and a linear regression model are implemented to provide reference performance. The main machine learning models are LightGBM and CatBoost, both trained using lagged price features, rolling statistics, and time-based variables.

Hyperparameter tuning is conducted using a time-ordered validation split to avoid information leakage. Key parameters such as learning rate, tree depth, and the number of estimators are adjusted to assess whether tuning improves predictive accuracy. Model performance is evaluated on the 2025 test set using MAE and RMSE.

Beyond overall accuracy, prediction errors are analyzed in detail. Model performance is examined separately for peak and trough price periods, as well as across different hours of the day. This allows for an assessment of systematic underestimation or overestimation and provides insight into model limitations during periods of high market volatility.

Overall, the methodology combines standard time-series feature engineering with gradient boosting models and detailed error diagnostics to evaluate both predictive accuracy and economic relevance in electricity price forecasting.
