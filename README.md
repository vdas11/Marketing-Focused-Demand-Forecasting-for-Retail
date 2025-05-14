🏦 Multi-Store Retail Demand Forecasting Project

📅 Objective

This project aims to build a robust demand forecasting pipeline for a retail chain with multiple store branches using time series models. We predict the sales for each store with high accuracy using SARIMAX, Prophet, and LSTM models. The core focus is on evaluating which model is best suited for real-world forecasting by comparing their performance on real historical data through backtesting.

📋 Dataset: Dummy_Marketing_Forecasting_Dataset.csv

This synthetic dataset simulates a national-level retailer, similar to Sainsbury's, with 100 individual branches across the country. Each row represents daily sales activity at a specific branch and contains several relevant features.

🔍 Dataset Columns Explained:

Column

Description

Store

Unique ID for each store branch (1-100)

Date

Date of the sales record (daily frequency)

Sales

Total sales amount for that day (target variable)

Customers

Number of customers that made purchases that day

Open

Whether the store was open that day (1=open, 0=closed)

Promo

Indicates whether a promotional campaign was running (1=Yes, 0=No)

StateHoliday

Type of public holiday ('a'=public, 'b'=religious, 'c'=school, '0'=none)

SchoolHoliday

Whether schools were closed (1=Yes, 0=No)

StoreType

Type of store (e.g., big, small, metro, etc.)

Assortment

Product assortment type (a=basic, b=medium, c=full)

CompetitionDistance

Distance to the nearest competitor store (in meters)

Promo2

Whether the store is participating in ongoing seasonal promos

PromoInterval

Months when promo2 campaigns are active

🌐 Project Pipeline

✅ Step 1: Data Selection

We selected a single store (Store ID: 1) from the dataset to build and evaluate models. This allowed us to test forecasting techniques before generalizing to all stores.

✅ Step 2: Train/Test Split for Backtesting

Training data: From the beginning of the dataset up to 2023-12-01

Testing data: From 2023-12-02 to 2024-01-15

This split simulates a real-world scenario where we predict the near future based only on historical data.

✅ Step 3: Model Training & Forecasting

Three forecasting models were used:

SARIMAX: Captures autoregressive, differencing, seasonality, and incorporates exogenous variables (Promo, SchoolHoliday)

Prophet: Facebook's model designed for business time series, also includes daily seasonality

LSTM: Deep learning approach using sliding windows and sequence modeling, implemented using Keras

Each model was trained using the training set and then used to predict sales during the test period.

✅ Step 4: Model Evaluation

Predictions from each model were compared against actual sales in the test period using:

RMSE (Root Mean Squared Error)

MAE (Mean Absolute Error)

MAPE (Mean Absolute Percentage Error)

📊 Sample Results (Actual):

Model

RMSE

MAE

MAPE (%)

SARIMAX

65.02

53.56

1.07

Prophet

65.03

54.01

1.08

LSTM

65.11

53.03

1.06

All three models performed well, with LSTM slightly outperforming in MAPE. These results give confidence to use these models for future sales forecasting.

📆 Future Forecast: 30-12-2024

A separate script was used to forecast sales for all 100 stores on the future date 30-12-2024 using the trained models. Since actual future values are unknown, this forecast serves as a production-level prediction to aid in planning, marketing, and inventory management.

📊 Output File: future_sales_forecast_2024_12_30.csv

This file includes the following columns:

Store: Store ID (1-100)

Date: Forecast date (2024-12-30)

SARIMAX_Pred: Predicted sales using SARIMAX

Prophet_Pred: Predicted sales using Prophet

LSTM_Pred: Predicted sales using LSTM

🔧 Tools & Libraries Used

Python 3.10+

Pandas, NumPy for data handling

scikit-learn for metrics

Prophet for business time series modeling

statsmodels for SARIMAX

Keras + TensorFlow backend for LSTM

Matplotlib/Seaborn (optional for plots)

🚀 Future Enhancements

Extend model to handle all 100 stores in parallel

Add rolling window cross-validation

Include features like weather, regional demographics, or footfall

Automate model selection based on store performance

📄 Summary

This project demonstrates a complete demand forecasting pipeline with real-world techniques:

Backtesting for true model evaluation

Model comparison and selection

Forecasting unknown future dates with confidence

It's suitable for retail planning, resource optimization, campaign targeting, and inventory management across distributed store networks.
