# ML2-Final-Project

## 1. Background & Motivation

Electricity prices in Poland show strong volatility and clear daily and weekly patterns. Price changes are influenced by demand fluctuations, supply conditions, and market mechanisms, which makes short-term price movements difficult to predict accurately.

With the availability of hourly electricity price data published by Polskie Sieci Elektroenergetyczne (PSE), it is possible to use historical information to model and forecast future price behavior.

In this course, we have learned several regression-based and tree-based machine learning models, as well as hyperparameter tuning techniques. These methods are designed to capture nonlinear relationships and temporal patterns in data. Applying these models to electricity price forecasting provides a practical way to evaluate their performance in a real-world time-series setting.

This project aims to use historical electricity price data to predict future prices and to assess whether model optimization through hyperparameter tuning can improve forecasting accuracy, especially during high-price and low-price periods.

## 2. Research Questions / Goals

RQ1:
How accurately can machine learning regression models predict hourly electricity prices in Poland using historical price data?

RQ2:
Do gradient boosting models outperform simple baseline and linear regression models in out-of-sample electricity price forecasting?

RQ3:
Does hyperparameter tuning improve forecasting performance, particularly during peak and off-peak price periods?

## 3. Data

Source:
Hourly electricity price data (RCE, PLN/MWh) published by Polskie Sieci Elektroenergetyczne (PSE), obtained from the PSE Raporty platform.

Date range:

Training data: January 2020 – December 2024

Test data: January 2025 – December 2025

Variables:

Target variable:

Hourly electricity price (RCE, PLN/MWh)

Explanatory variables (constructed from historical data):

Lagged prices (e.g. 1 hour, 24 hours, 168 hours)

## 4. Methods

This project formulates electricity price forecasting as a supervised time-series regression problem. The main focus is on gradient boosting models, which are designed to capture nonlinear relationships and interactions in time-dependent data.

The dataset is split chronologically. Hourly data from 2020 to 2024 are used as the training set, while data from 2025 are reserved as a strictly out-of-sample test set. This setup reflects a realistic forecasting scenario in which future electricity prices are predicted using only historical information.

As baseline models, a naive lag-based benchmark and a linear regression model are first implemented to provide reference performance. The core models of the project are a Gradient Boosting Regressor and LightGBM, which are trained using lagged price features, rolling statistics, and time-based variables.

Model hyperparameters are optimized using time-series cross-validation to avoid information leakage. Key parameters such as the learning rate, number of estimators, and tree complexity are tuned to improve predictive accuracy. The final models are evaluated by comparing predicted electricity prices for 2025 with the actual observed values.

Model performance is assessed using MAE and RMSE. In addition to overall accuracy, prediction errors are analyzed separately for peak and off-peak price periods to examine how well gradient boosting models capture extreme price movements.

Rolling statistics (e.g. rolling mean and standard deviation)

Time-based features (hour of day, day of week, weekend indicator)
