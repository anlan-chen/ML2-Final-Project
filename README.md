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

## Source:
This project uses hourly electricity price data from two official sources. Historical day-ahead electricity prices for Poland from 2020 to 2023 are obtained from the ENTSO-E Transparency Platform (Energy Prices, Day-Ahead Market). More recent electricity price data for 2024 and 2025 are collected from the Polskie Sieci Elektroenergetyczne (PSE) Raporty platform (RCE prices).

Date range:

Training period: January 2020 – December 2024

Test period: January 2025 – December 2025

Variables:

Target variable:

Hourly day-ahead electricity price (EUR/MWh)

Data processing:

ENTSO-E day-ahead prices, originally published at a 15-minute resolution, are aggregated to an hourly frequency using hourly averages.

PSE RCE prices, originally available at a 15-minute resolution, are also aggregated to hourly values.

All prices are converted to a common hourly time scale to ensure consistency across data sources.

Explanatory variables (constructed):

Lagged electricity prices (e.g. 1-hour, 24-hour, and 168-hour lags)

Rolling statistics (e.g. rolling mean and standard deviation)

Calendar-based features (hour of day, day of week, weekend indicator)

## 4. Methods

This project formulates electricity price forecasting as a supervised time-series regression problem. The main focus is on gradient boosting models, which are designed to capture nonlinear relationships and interactions in time-dependent data.

The dataset is split chronologically. Hourly data from 2020 to 2024 are used as the training set, while data from 2025 are reserved as a strictly out-of-sample test set. This setup reflects a realistic forecasting scenario in which future electricity prices are predicted using only historical information.

As baseline models, a naive lag-based benchmark and a linear regression model are first implemented to provide reference performance. The core models of the project are a Gradient Boosting Regressor and LightGBM, which are trained using lagged price features, rolling statistics, and time-based variables.

Model hyperparameters are optimized using time-series cross-validation to avoid information leakage. Key parameters such as the learning rate, number of estimators, and tree complexity are tuned to improve predictive accuracy. The final models are evaluated by comparing predicted electricity prices for 2025 with the actual observed values.

Model performance is assessed using MAE and RMSE. In addition to overall accuracy, prediction errors are analyzed separately for peak and off-peak price periods to examine how well gradient boosting models capture extreme price movements.

Rolling statistics (e.g. rolling mean and standard deviation)

Time-based features (hour of day, day of week, weekend indicator)
