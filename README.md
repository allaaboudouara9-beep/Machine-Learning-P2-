# Machine-Learning-P2-

# 🍎 Apple Stock Market Analysis Using Machine Learning

## 📌 Project Overview

This project applies **machine learning and time-series analysis** to historical Apple Inc. stock market data.

The main purpose of the project is to investigate patterns in Apple's historical trading data using **clustering techniques** and to examine the forecasting performance of **ARIMA and SARIMA models**.

Stock market data is numerical, sequential, and highly dynamic, making it suitable for both clustering and time-series forecasting.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* 📊 Explore historical Apple stock market data
* 🧹 Prepare and scale numerical features
* 🔵 Apply K-Means clustering
* 🌳 Apply Agglomerative clustering for comparison
* 📉 Determine an appropriate number of clusters using the Elbow Method
* 🎯 Evaluate clustering using Silhouette Score and Davies-Bouldin Index
* ⏳ Analyse historical stock price trends
* 🌊 Investigate trend, seasonality, and residual components
* 🔮 Apply ARIMA models for forecasting
* 📅 Apply SARIMA models to investigate seasonal forecasting
* ⚖️ Compare ARIMA and SARIMA using AIC

---

# 📂 Dataset Features

The project focuses on several important stock market variables:

* 💵 **Close Price** — final Apple stock price when the market closes
* 📈 **High Price** — highest Apple stock price reached during the trading day
* 📉 **Low Price** — lowest Apple stock price reached during the trading day
* 🔔 **Open Price** — first trading price when the market opens
* 📊 **Volume** — total number of Apple shares traded during the day

These variables provide information about Apple's historical price movements and trading activity.

---

# 🔵 Clustering Analysis

## ⚙️ Standardisation

Before applying clustering algorithms, **StandardScaler** was used to place the numerical features on a comparable scale.

Standardisation is particularly important for distance-based algorithms such as K-Means because variables with larger numerical scales could otherwise have a greater influence on cluster formation.

---

## 🔵 K-Means Clustering

K-Means clustering was applied to identify different groups within Apple's historical stock data.

The clustering analysis initially divided observations into groups representing different market conditions.

The results indicated that:

* 🔵 **Cluster 0** generally represented lower-price periods
* 🟠 **Cluster 1** generally represented higher-price periods

The analysis also suggested differences in trading volume between lower-price and higher-price periods.

These clusters provide a simple way of identifying different historical trading patterns within Apple's stock data.

---

# 📉 Elbow Method

The **Elbow Method** was used to investigate an appropriate number of clusters.

The method examines the reduction in within-cluster variation as the number of clusters increases.

The analysis showed that adding clusters initially produced substantial improvements, while further increases produced progressively smaller benefits.

This helped identify a small number of clusters as appropriate candidates for the dataset.

However, the Elbow Method was considered alongside additional clustering evaluation metrics rather than being used independently.

---

# 🎯 Silhouette Score

The **Silhouette Score** was used to measure how well observations were grouped within their assigned clusters.

A higher Silhouette Score generally represents:

✅ Better separation between clusters
✅ Greater similarity within clusters

The strongest reported result was approximately:

### 🎯 Silhouette Score = 0.60

This result was obtained using **two clusters**, indicating that two clusters provided strong separation for the stock data compared with the alternative cluster configurations examined.

---

# ⚔️ K-Means vs Agglomerative Clustering

K-Means and Agglomerative clustering were compared using:

* 🎯 Silhouette Score
* 📊 Davies-Bouldin Index

The reported results were approximately:

| Model            | Silhouette Score | Davies-Bouldin Index |
| ---------------- | ---------------: | -------------------: |
| 🔵 K-Means       |       **0.6038** |           **0.5696** |
| 🌳 Agglomerative |           0.5382 |               0.5745 |

For the **Silhouette Score**, a higher value is preferred.

For the **Davies-Bouldin Index**, a lower value is preferred.

Therefore, K-Means performed better according to both reported evaluation measures.

### 🏆 Best Clustering Model: K-Means

The results suggest that K-Means produced more compact and better-separated clusters for this dataset.

---

# ⏳ Time-Series Analysis

Time-series analysis was used to investigate how Apple's stock market variables changed over time.

The historical Close Price showed a general **upward long-term trend**, although several periods contained noticeable fluctuations and price declines.

📈 Long-term trend → generally upward
📉 Short-term movements → fluctuations and declines
⚡ Market behaviour → evidence of volatility

These characteristics motivated the use of time-series forecasting models.

---

# 📅 Historical Price Behaviour

Different periods showed different stock market behaviour.

### 📈 2016

Apple's price fluctuated during the year but finished higher, suggesting an overall upward movement.

### 📉 2018

The Close Price increased during much of the year before experiencing a substantial decline towards the end of the period.

### 🚀 2024

The Close Price demonstrated a strong upward trend despite some fluctuations, suggesting substantial price growth during the year.

---

# 🌊 Seasonality & Decomposition

Time-series decomposition was used to separate the data into:

📈 **Trend** — long-term movement
🔄 **Seasonality** — repeating patterns
⚡ **Residuals** — unexplained/random fluctuations

The Close Price analysis showed a strong long-term upward trend.

The seasonal component appeared relatively small compared with the overall trend, while the residual component contained fluctuations and spikes.

These residual movements may represent short-term volatility and unexpected market behaviour.

---

# 📊 Volume Analysis

Trading Volume showed different characteristics from stock prices.

The decomposition suggested a minor declining trend over time, while the residual component contained numerous spikes.

These spikes may reflect periods of unusual trading activity or unexpected market events.

The seasonal component of Volume also appeared more noticeable than the seasonal patterns observed in some of the price variables.

---

# 🔮 ARIMA Forecasting

**ARIMA — Autoregressive Integrated Moving Average** — was used for time-series forecasting.

Appropriate model parameters were selected with support from **ACF and PACF plots**.

The **Akaike Information Criterion (AIC)** was also used to compare model configurations.

### 📉 AIC Interpretation

When comparing models fitted to the same target series:

### Lower AIC = preferred model ✅

A lower AIC indicates a better trade-off between model fit and model complexity.

---

# 💵 Close Price — ARIMA

The selected model was:

### ARIMA(0,1,0)

The reported results included:

* 📈 **R² ≈ 0.99**
* 🔮 Forecast range ≈ **254.51–264.08**
* 📉 AIC ≈ **11,608.10**

The model produced a close fit between the reported predicted and observed values.

---

# 📉 Low Price — ARIMA

The selected model was:

### ARIMA(2,1,1)

The reported minimum AIC was approximately:

### 📊 AIC = 11,246.76

Daily Low Prices may be particularly sensitive to short-term market volatility and intraday price movements.

---

# 🔔 Open Price — ARIMA

The selected model was:

### ARIMA(2,1,2)

Reported results included:

* 📊 **AIC ≈ 11,787.47**
* 🎯 **R² ≈ 0.9989**
* 🔮 Forecast ≈ **259.96**
* 📏 95% forecast interval ≈ **254.98–264.94**

---

# 📊 Volume — ARIMA

The selected model was:

### ARIMA(1,1,2)

The reported minimum AIC was:

### 📉 AIC ≈ 94,412.54

The analysis suggests that trading Volume was more difficult to forecast using a univariate ARIMA approach.

One possible reason is that trading activity can be affected by unexpected events and other external market factors.

---

# 📅 SARIMA Model

**SARIMA — Seasonal Autoregressive Integrated Moving Average** — extends ARIMA by incorporating seasonal components.

SARIMA was used to investigate whether modelling seasonality could improve forecasting performance.

---

## 💵 Close Price — SARIMA

Reported AIC:

### 📊 11,627.46

The corresponding ARIMA model produced a lower reported AIC.

Therefore, based on the models compared in this project:

### 🏆 ARIMA performed better for Close Price.

This result is also consistent with the relatively weak seasonality observed in the Close Price decomposition.

---

## 🔔 Open Price — SARIMA

The reported SARIMA AIC was approximately:

### 📊 11,810.288

The corresponding ARIMA model produced a lower reported AIC of approximately **11,787.47**.

Therefore, ARIMA was preferred according to AIC.

---

## 📊 Volume — SARIMA

The reported SARIMA AIC was:

### 📊 94,550.347

The ARIMA model produced a lower reported AIC of approximately:

### 📉 94,412.54

Therefore, ARIMA again produced the preferred result according to AIC.

---

# ⚖️ ARIMA vs SARIMA

Based on the reported AIC results:

| Feature   |         ARIMA |     SARIMA | Preferred |
| --------- | ------------: | ---------: | --------- |
| 💵 Close  | **11,608.10** |  11,627.46 | 🏆 ARIMA  |
| 🔔 Open   | **11,787.47** | 11,810.288 | 🏆 ARIMA  |
| 📊 Volume | **94,412.54** | 94,550.347 | 🏆 ARIMA  |

Overall, the tested **ARIMA models produced lower AIC values than the corresponding SARIMA models**.

This suggests that introducing additional seasonal components did not improve these models sufficiently to compensate for their additional complexity.

---

# 🛠️ Technologies & Libraries

The project was completed using:

* 🐍 Python
* 📓 Jupyter Notebook
* 🐼 Pandas
* 🔢 NumPy
* 📊 Matplotlib
* 📈 Seaborn
* 🤖 Scikit-learn
* 📉 Statsmodels

---

# 🔑 Key Findings

The main findings of the project include:

* 🔵 K-Means successfully identified different groups within Apple's historical trading data.
* 🎯 Two clusters achieved the strongest reported Silhouette Score of approximately **0.60**.
* 🏆 K-Means outperformed Agglomerative clustering according to the reported Silhouette Score and Davies-Bouldin Index.
* 📈 Apple's Close Price demonstrated a strong long-term upward trend over the analysed period.
* 🌊 Price variables showed relatively limited seasonal behaviour compared with their long-term trends.
* ⚡ Residual components demonstrated short-term volatility and unusual market movements.
* 📊 Trading Volume appeared more difficult to forecast than price variables.
* 🔮 ARIMA successfully modelled several of the analysed time series.
* 📅 SARIMA was tested to account for potential seasonal patterns.
* 🏆 ARIMA produced lower reported AIC values than SARIMA for the directly compared Close, Open, and Volume models.

---

# 🏁 Conclusion

This project demonstrates how **machine learning clustering and time-series forecasting** can be applied to historical stock market data.

K-Means clustering was useful for identifying different historical trading patterns within Apple's stock data. Based on the reported evaluation metrics, the two-cluster K-Means solution provided the strongest clustering performance.

Time-series analysis also identified a substantial long-term upward trend in Apple's historical stock prices, accompanied by periods of short-term volatility.

Both ARIMA and SARIMA models were investigated for forecasting. Based on the reported AIC values, **ARIMA generally performed better than SARIMA for the directly compared variables**, suggesting that the additional seasonal components did not provide sufficient improvement for these particular models.

Overall, the project demonstrates how clustering, visualisation, time-series decomposition, and forecasting techniques can provide useful insights into historical financial market behaviour. 🍎📈✨
