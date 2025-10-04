# Time-Series Forecasting: Predicting AAPL Stock Prices with ARIMA and LSTM

This project compares the performance of a traditional statistical model (ARIMA) and a deep learning model (LSTM) for forecasting the daily closing price of Apple Inc. (AAPL) stock. The goal is to determine which model provides more accurate predictions and generalizes better to unseen data.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Table of Contents
* [Problem Statement](#problem-statement)
* [Dataset](#dataset)
* [Methodology](#methodology)
* [Usage](#usage)
* [Results](#results)
* [Deployment](#deployment)
* [Conclusion](#conclusion)

---

## Problem Statement

The core task is to forecast future stock values using a public stock price dataset. The key requirements were:
-   **Implement a traditional statistical model:** ARIMA was chosen for this role.
-   **Implement a machine learning / deep learning model:** An LSTM network was implemented.
-   **Compare performance:** The models were evaluated and compared using standard regression metrics.
-   **Use robust evaluation:** A rolling window (walk-forward) validation method was used to simulate real-world forecasting.

---

## Dataset

The dataset used is the historical daily stock price for **Apple Inc. (AAPL)**, obtained from [Yahoo Finance](https://finance.yahoo.com/quote/AAPL/history/).

-   **Ticker:** `AAPL`
-   **Time Period:** `2015-01-01` to `2023-12-31`
-   **Feature Used for Forecasting:** `Close` price

---

## Methodology

### 1. Data Preprocessing
-   **ARIMA:** The time series was checked for stationarity using the Augmented Dickey-Fuller (ADF) test. First-order differencing was applied to make the series stationary.
-   **LSTM:** The data was normalized using `MinMaxScaler` to scale values between 0 and 1. It was then transformed into supervised learning sequences with a look-back window of 60 days.

### 2. Model Architecture
-   **ARIMA (Autoregressive Integrated Moving Average):** A standard ARIMA(p,d,q) model was implemented. The optimal parameters were determined using ACF and PACF plots and grid search techniques.
-   **LSTM (Long Short-Term Memory):** A sequential deep learning model was built using Keras/TensorFlow. The architecture consists of multiple LSTM layers followed by Dense layers to output the prediction.

### 3. Evaluation
A **rolling window (walk-forward) validation** approach was used. The model is trained on a window of historical data, makes a prediction for the next step, and then the window is moved forward to include the actual value of the predicted step for the next training round.

The following metrics were used to measure forecast accuracy:
-   **Root Mean Squared Error (RMSE)**
-   **Mean Absolute Percentage Error (MAPE)**

---

## Usage

The entire analysis and modeling process is documented in the Google Colab.

1.  Launch Google Colab:
    ```bash
    Google Colab
    ```
2.  Open and run the cells in `Jalal_Uddin_ML_JobTask_SET_B.ipynb`.

---

## Results

The LSTM model significantly outperformed the ARIMA model in forecasting the AAPL closing price, demonstrating its superior ability to capture the non-linear dynamics of the stock market.

| Model | RMSE      | MAPE       |
| :---- | :-------- | :--------- |
| ARIMA | `15.795903` | `0.085728` |
| LSTM  | `5.874788`  | `0.030564`  |

---

## Deployment

The superior-performing LSTM model has been containerized and deployed as an interactive web application on **Hugging Face Spaces**. The application allows users to see the latest forecast for the next trading day.

** [Live Demo on Hugging Face Spaces](https://huggingface.co/Jalal10/DataSynthis_ML_JobTask)**

---

## Conclusion

The LSTM model is the recommended choice for this forecasting task. Its ability to learn long-term dependencies and model complex, non-linear patterns makes it fundamentally more suitable for volatile financial time-series data compared to the linear assumptions of the ARIMA model. The lower RMSE and MAPE values provide quantitative evidence of its superior predictive power.
