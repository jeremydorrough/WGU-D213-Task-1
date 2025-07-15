# WGU D213 Task 1: ARIMA Revenue Forecasting for Telecom Company

This project uses ARIMA modeling to forecast telecom revenue based on two years of daily revenue data. It demonstrates how to prepare, analyze, and model time series data using both manual and auto ARIMA techniques, enabling short-term revenue forecasting to support strategic business decisions.

## 🎯 Objective

**Business Question:**  
Can an ARIMA model be developed to predict the future revenue trend for the telecom company based on its revenue performance in the first two years?

**Goals:**
- Analyze and preprocess the data for stationarity and autocorrelation
- Build and validate an ARIMA model on 80/20 train-test split
- Forecast revenue for the test period and assess model accuracy

## 📁 Files

- `D213_Task1_Jeremy_Dorrough_Submission.ipynb`: Complete time series analysis in Python
- `prepared_data.csv`: Stationary revenue data (first-difference), ready for modeling
- `D213_Task1_Jeremy_Dorrough_Submission.pdf`: Detailed write-up with analysis, visualizations, and model justification

## 🧪 Tools and Libraries

- Python 3.x
- `pandas`, `numpy` – Data manipulation
- `matplotlib`, `seaborn` – Visualization
- `scikit-learn` – Preprocessing, evaluation
- `statsmodels` – ADF test, ARIMA modeling
- `pmdarima` – AutoARIMA modeling and diagnostics

## 📊 Data Summary

- Daily revenue data over two years
- Converted 'Day' to proper date format
- Differenced the data to achieve stationarity (ADF test passed)
- Split into training (80%) and testing (20%) sets

## ⚙️ Modeling Approach

1. **Stationarity Check**  
   - ADF test initially failed (p=0.32)  
   - Differencing applied → ADF passed (p < 0.001)

2. **Decomposition & Autocorrelation**  
   - No significant seasonality beyond weekly cycle
   - Clear trend before differencing; none after
   - ACF and PACF plots used to guide manual model

3. **Model Selection**
   - **Manual ARIMA(1,0,0)**: Based on ACF/PACF and AIC comparison  
   - **AutoARIMA**: Identified ARIMA(1,0,0)(2,1,0)[12] as optimal seasonal model  
   - Best model used for forecasting and diagnostics

## 📈 Forecast Results

- **RMSE:** 0.59  
- **Forecast Window:** Matched test set duration (~4 months)  
- **Uncertainty:** Wider intervals over time; short-term accuracy preferred  
- **Confidence Intervals:** Forecast with 95% bounds for decision-making

## 📌 Insights

- Revenue shows overall growth but limited long-term predictability
- ARIMA(1,0,0) model provides good short-term forecasts
- Seasonal ARIMA identified weekly and monthly cycles
- Prediction intervals widen rapidly — suggests caution on multi-month forecasts

## 📋 Recommendations

- Use this ARIMA model for short-term (monthly) revenue forecasting
- Continuously retrain with new data to maintain accuracy
- Investigate external factors influencing variance to refine future models

## 👤 Author

Jeremy Dorrough  
Western Governors University  

## 📚 References

- [ADF Test – DataScienceConcepts](https://www.datascienceconcepts.com/tutorials/python-programming-language/stationarity-augmented-dickey-fuller-test-in-python/)
- [ARIMA Guide – Machine Learning Plus](https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/)
- [AIC/BIC – Kaggle](https://www.kaggle.com/code/gourab1992/model-selection-using-aic-and-bic-in-python)
- [Spectral Density – GeeksForGeeks](https://www.geeksforgeeks.org/plot-the-power-spectral-density-using-matplotlib-python/)
