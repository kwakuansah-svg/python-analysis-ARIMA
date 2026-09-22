# ARIMA Stock Price Forecasting

## Overview

This project applies time-series analysis and the Autoregressive Integrated Moving Average (ARIMA) model to historical Google stock price data.

The analysis explores historical share-price and trading-volume patterns, tests the stationarity of the stock-price series, transforms the data where necessary, examines autocorrelation using ACF and PACF plots, fits and compares different ARIMA specifications, and uses the selected model to generate short-term forecasts.

The project demonstrates the application of Python-based statistical and econometric techniques to a financial forecasting problem.

## Objectives

The main objectives of this project are to:

* Analyse historical Google stock prices and trading volume.
* Examine the statistical characteristics of the stock-price series.
* Test the original share-price series for stationarity.
* Apply differencing and log transformation to obtain a stationary series.
* Examine autocorrelation and partial autocorrelation using ACF and PACF.
* Fit multiple ARIMA model specifications.
* Compare candidate models using information criteria, particularly BIC.
* Generate a 30-business-day stock-price forecast.
* Examine model residuals using diagnostic plots.
* Evaluate forecasting performance using a 90-day backtest.

## Data

The dataset contains historical Google stock-market observations from:

**2 January 2020 – 28 October 2025**

The dataset contains **1,464 observations** and the following variables:

* `Close` – Closing share price
* `High` – Highest price
* `Low` – Lowest price
* `Open` – Opening price
* `Volume` – Trading volume

The analysis primarily focuses on the **closing price** and **trading volume**.

## Analysis and Methodology

### 1. Exploratory Data Analysis

The project begins by examining the structure and descriptive statistics of the dataset.

The analysis includes:

* Data information and descriptive statistics
* Missing-value checks
* Historical closing-price visualisation
* Trading-volume visualisation
* Correlation between closing price and volume
* Average yearly closing prices
* Year-end closing prices
* Highest and lowest yearly closing prices
* Monthly periods associated with yearly price highs and lows

### 2. Stationarity Testing

The original Google share-price series is tested for stationarity using the **Augmented Dickey-Fuller (ADF) test**.

The original price series produces a p-value of approximately **0.994**, indicating that the series is non-stationary under the test criterion used in the notebook.

The analysis then calculates log first differences:

```python
price_return_diff = np.log(price).diff().dropna()
```

The transformed series produces an ADF p-value of approximately **1.01 × 10⁻²²**, indicating stationarity under the same criterion.

### 3. ACF and PACF Analysis

The project uses **Autocorrelation Function (ACF)** and **Partial Autocorrelation Function (PACF)** plots to investigate the dependence structure of the transformed series and inform the selection of ARIMA parameters.

The notebook then evaluates several candidate ARIMA specifications.

### 4. ARIMA Model Estimation

The following models are fitted and compared:

* ARIMA(1,1,1)
* ARIMA(0,1,0)
* ARIMA(1,1,0)
* ARIMA(0,1,1)
* ARIMA(2,1,1)
* ARIMA(1,1,2)

The models are compared using information criteria, including **AIC and BIC**.

Based on the BIC comparison performed in the notebook, **ARIMA(0,1,0)** has the lowest BIC among the tested specifications and is therefore selected for the forecasting exercise.

### 5. Forecasting

The selected ARIMA(0,1,0) model is used to generate a **30-business-day forecast** of the Google closing share price.

The forecast is plotted alongside the historical closing-price series to visualise the model's projected path.

### 6. Residual Diagnostics

The fitted model is examined using diagnostic plots to assess the behaviour of the residuals.

The notebook uses:

* Residual plots
* Standardised residuals
* ACF of residuals
* Distributional diagnostics
* Other diagnostic information produced by the ARIMA results

### 7. Forecast Backtesting

The project also includes a simple out-of-sample backtesting exercise.

The final **90 observations** are separated as a test set, while the earlier observations are used to train the model.

The ARIMA(0,1,0) model is then used to forecast the 90-day test period.

The resulting performance measures are:

* **MAE:** 49.15
* **RMSE:** 57.49

The notebook also calculates RMSE relative to the mean of the test-period prices.

## Technologies and Libraries

The project was developed using:

* Python
* Jupyter Notebook
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Statsmodels
* yfinance

## Project Structure

```text
python-analysis-ARIMA/
│
├── ARIMA_TRY_WORK.ipynb
└── README.md
```

## Key Learning Outcomes

This project provided practical experience in applying time-series modelling techniques to financial market data.

Through the analysis, I developed practical understanding of:

* Financial time-series data
* Stock-price analysis
* Stationarity and the Augmented Dickey-Fuller test
* Log returns and differencing
* Autocorrelation and partial autocorrelation
* ARIMA model specification
* AIC and BIC model comparison
* Forecasting with ARIMA
* Residual diagnostics
* Out-of-sample model evaluation
* Python-based financial data analysis

## Future Improvements

Potential extensions to this project include:

* Testing additional ARIMA specifications systematically.
* Comparing ARIMA with alternative forecasting models.
* Conducting more extensive out-of-sample validation.
* Examining whether trading volume provides useful explanatory information.
* Comparing forecasts across different financial assets.
* Exploring volatility modelling using GARCH.
* Investigating machine-learning approaches to financial time-series forecasting.

## Author

**Kwaku Manu Ansah**

Bachelor of Commerce (Finance)
University of Cape Coast, Ghana
