# Stock-Price-Prediction-and-Back-Testing #
In this project, I conducted independent research on time series data analysis for Apple stock price forecasting. Utilized the traditional machine learning model, ARIMA, as a benchmark. Implemented a deep learning model, LSTM. Backtesting is conducted to evaluate the performance of a specified investment strategy based on predicted data from LSTM.

# Web Crawling for AAPL Data # 
Run "webscraper_cy.py" to get daily AAPL price data from https://sg.finance.yahoo.com/

# Data Preprocessing # 
1. Handle missing data: Filled with the previous day`s data
2. Remove outlier: use 0.01 to 0.99 quantile

# Base Model: ARIMA(p,d,q) # 
ARIMA stands for Autoregressive Integrated Moving Average which analyzes the current values of the time series and uses past values to forecast future values. Specifically, it uses differencing of past values to remove any trend or seasonality that might be present.

Key Requirement/Assumption:
- Linearity
- Stationary
- Independence of Errors: no autocorrelation in the residuals
- No Seasonal Patterns --> otherwise, apply seasonal ARIMA

AR(p): Assume analytical components based on the assumption that the future value of the series can be predicted using its own past values (its own lag terms). To figure out the order of an AR model, you would use the PACF.

MA(q): Assume the current value is dependent on the error terms including the current error. To figure out the order of an MA model, you would use the ACF.

I(d): Evaluate differences in time series

weakness: The need for manual selection of hyperparameters as the state of systems can gradually change over time.

Modelling: 
1. Data transformation is conducted before the modelling to convert non-stationary data into stationary data. 
2. Use auto_arima package to find best ARIMA(p,d,q) model.

# Deep Learning model: LSTM #
Besides ARIMA, RNNs did a good job in time series data analysis. Recurrent Neural Networks (RNNs) are a type of artificial neural network that is well-suited for sequential data and time series analysis. However, it is not able to capture long-term dependencies in data and suffers from a vanishing gradient problem. Hence, Long Short-Term Memory (LSTM) networks and Gated Recurrent Unit (GRU) networks are introduced to address these limitations through the use of memory cells and gates.

LSTMs are more complex and capable of capturing longer-term dependencies, while GRUs offer a simpler architecture with potentially lower computational requirements. The choice between them depends on the specific task, available computational resources, and the trade-off between model complexity and performance.

In this project,  I use the previous 7 days' data to predict the next day data.
