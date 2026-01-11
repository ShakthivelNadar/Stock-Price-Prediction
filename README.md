# Stock-Price-Prediction
Stock Price Prediction with LSTM
Introduction
This notebook demonstrates how to build and evaluate a Long Short-Term Memory (LSTM) neural network model for stock price prediction. The goal is to forecast the closing price of a given stock using historical data, including technical indicators like Moving Averages (MA) and Relative Strength Index (RSI).

Data Acquisition
Stock data is acquired using the yfinance library. The stock_symbol, start_date, and end_date variables can be modified to fetch data for different stocks and time periods.

Stock Symbol: AAPL (Apple Inc.)
Start Date: 2015-01-01
End Date: 2024-01-01
Feature Engineering
To enhance the model's predictive capability, the following technical indicators are calculated and added to the dataset:

Moving Averages (MA):
MA_20: 20-day Simple Moving Average
MA_50: 50-day Simple Moving Average
Relative Strength Index (RSI): A momentum oscillator that measures the speed and change of price movements.
After calculating these features, rows with NaN values (due to rolling window calculations) are dropped.

Data Preprocessing
Scaling: The data is scaled using MinMaxScaler to normalize values between 0 and 1, which is a common practice for neural networks to ensure stable training.
Sequence Creation: A function create_sequences is used to transform the time series data into sequences suitable for LSTM training. Each sequence consists of time_steps (defaulting to 60) previous data points to predict the next closing price.
Train-Test Split: The dataset is split into training and testing sets, with 80% for training and 20% for testing.
Model Development
An LSTM model is constructed using TensorFlow/Keras:

Architecture:
Two LSTM layers with 100 units each.
Dropout layers (0.2) are included after each LSTM layer to prevent overfitting.
A final Dense layer with 1 unit for predicting the single output (closing price).
Compilation: The model is compiled with the adam optimizer and mean_squared_error as the loss function.
Training: The model is trained for 25 epochs with a batch size of 32 and a 10% validation split.
Model Evaluation
After training, the model's performance is evaluated on the test set:

Prediction: The model predicts stock prices for the test set.
Inverse Scaling: The predicted and actual prices are inverse-scaled to bring them back to their original dollar values.
RMSE Calculation: The Root Mean Squared Error (RMSE) is calculated to quantify the difference between actual and predicted prices.
Visualization: A plot is generated to compare the actual and predicted stock prices over the test period.
Results
The RMSE for the model on the test data is approximately 6.34, indicating the average magnitude of the error in dollar terms for the predictions.

How to Use This Notebook
Run all cells: Execute all code cells sequentially to reproduce the analysis and predictions.
Modify Stock Data: Change stock_symbol, start_date, and end_date in the 'Data Acquisition' section to analyze different stocks or timeframes.
Adjust Model Parameters: Experiment with time_steps in create_sequences, LSTM units, dropout rates, epochs, and batch size to optimize model performance.
