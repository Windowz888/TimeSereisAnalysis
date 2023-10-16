# Toronto Bus Delay Forecast

## Overview
Forecast the overall minutes of delay (`Min Delay`) for Toronto buses from the upcoming month until the end of 2023, and the beginning of 2024. This prediction utilizes Time Series Analysis and the SARIMAX model, considering the types of incidents (`Incident` column) as exogenous factors to enhance prediction accuracy.

## Table of Contents

- [Time Series Analysis](#time-series-analysis)
  - [Initial Approach with ARIMA](#initial-approach-with-arima)
  - [SARIMA Model](#sarima-model)
- [Transition to SARIMAX](#transition-to-sarimax)
  - [Exogenous Variables Visualization](#exogenous-variables-visualization)
- [Stationarity Testing](#stationarity-testing)
- [Model Selection](#model-selection)
- [Model Evaluation](#model-evaluation)
  - [SARIMAX Model Components](#sarimax-model-components)
- [Prediction](#prediction)
- [Conclusion](#conclusion)

## Time Series Analysis

Time series analysis is a statistical technique that deals with time series data or data points arranged in chronological order. It helps uncover patterns, trends, and makes future predictions.

### Initial Approach with ARIMA

ARIMA stands for AutoRegressive Integrated Moving Average:
- **AR (AutoRegressive):** Uses past values to predict future values.
- **I (Integrated):** Represents the differencing of raw observations to allow for stationarity.
- **MA (Moving Average):** Uses past forecast errors to predict the future.

### SARIMA Model

Given unsatisfactory predictions from the ARIMA model and noticing a weekly seasonality pattern in the `Min Delay` data, the SARIMA (Seasonal ARIMA) model was adopted. SARIMA caters to seasonality, allowing it to model univariate time series data exhibiting recurring patterns.

## Transition to SARIMAX

To further refine the predictions, SARIMAX (Seasonal ARIMA with eXogenous variables) was introduced. The 'type of incident' was used as the exogenous variable, enhancing the model's accuracy. SARIMAX is beneficial for modeling time series data with seasonality and integrating external variables for improved predictions.

### Exogenous Variables Visualization

Before modeling with SARIMAX, the daily occurrences of various incidents related to bus delays were visualized. Individual plots showcased each incident type over time, revealing potential patterns. The correlation between these incidents and `Min Delay` was calculated to gauge their impact on delays.

## Stationarity Testing

To ensure accurate time series analysis, the data's stationarity was verified using the ADF (Augmented Dickey-Fuller) and KPSS (Kwiatkowski-Phillips-Schmidt-Shin) tests. Stationary data has stable statistical properties over time, making it ideal for time series forecasting.

## Model Selection

The best model parameters were chosen based on:
- **AIC (Akaike Information Criterion):** Measures the goodness of fit of a statistical model and penalizes models with more parameters.
- **BIC (Bayesian Information Criterion):** Similar to AIC but with a stricter penalty for models with more parameters.
- **MSE (Mean Squared Error):** Represents the average squared difference between observed and predicted values.

## Model Evaluation

To ensure accurate predictions, the model's residuals (differences between predictions and actual values) were examined. A lack of patterns in the residuals over time, a normal distribution of residuals, and no auto-correlation (verified using ACF and PACF plots) confirmed the model's robustness.

### SARIMAX Model Components

The SARIMAX model used in this project had the following structure:
- ARIMA component: `order=(0,1,1)`
- Seasonal component: `seasonal_order=(0,1,1,7)`

## Prediction

The model was trained, and its predictions for July were compared with the test set, yielding an RMSE (Root Mean Squared Error) of 662.80 minutes. Given the complexity of the data, this RMSE indicates the model's respectable performance. The model was then used to predict the overall `Min Delay` for the entire dataset.

## Conclusion

This analysis offers a robust foundation for understanding and predicting bus delays in Toronto. The pursuit of even more accurate forecasting continues, with the hope of enhancing Toronto's transportation system efficiency.
