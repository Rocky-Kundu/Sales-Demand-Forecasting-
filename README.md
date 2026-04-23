Sales Demand Forecasting for
Inventory Planning
FreshMart — FMCG Retail Chain | Supply Chain Analytics | Time Series | Regression
April 2025
1. Executive Summary
FreshMart manages thousands of SKUs across multiple store locations and currently relies on simple
historical averages for inventory planning — resulting in frequent stockouts and costly overstocking.
This project builds a demand forecasting system using Linear Regression and Random Forest
Regressor on 731 days of sales data. The best model achieved MAPE of 9.1% and R2 of 0.816, and
generated a 30-day forward forecast recommending 3,861 units of total stock.
2. Problem Definition
Business Problem
• Frequent stockouts of high-demand products causing revenue loss
• Overstocking of slow-moving items increasing holding and wastage costs
• Demand planning based on simple historical averages — not capturing seasonality or trends
• No product-level or store-level forecasting capability
• Promotions and holidays not factored into existing inventory decisions
Key Objectives
• Analyse sales trends, seasonality, and weekly/monthly demand patterns
• Quantify the impact of promotions, holidays, and pricing on demand
• Build an accurate forecasting model with MAPE below 15%
• Compare at least two models and select best based on error metrics
• Generate a 30-day forward demand forecast
• Provide actionable inventory planning recommendations
3. Dataset Description
Dataset Attribute Details
Total Records 731 daily sales records (2 years)
Total Features 15 input features + 1 target
Products (SKUs) 10 products (SKU_100 to SKU_109)
Stores 5 stores (STORE_1 to STORE_5)
Categories Beverages, Groceries, Dairy, SnacksKey Features Price, Discount, Promotion_Flag,
Holiday_Flag, Season, Stock_Available
Target Variable Units_Sold (daily)
Missing Values None — dataset fully clean
4. Methodology & Data Preprocessing
Data Preprocessing
• Date column converted to datetime format for time-based feature extraction
• Label Encoding applied to: Store_ID, Product_ID, Category, Season
• Feature Engineering: extracted Week_of_Year and Quarter from Date
• Train/Test split: first 80% for training, last 20% for testing (time-order preserved — no data leakage)
• StandardScaler applied to all features
Modelling Approach
• Model 1 — Linear Regression: simple interpretable baseline
• Model 2 — Random Forest Regressor (100 trees): captures non-linear patterns
• Evaluation metrics: MAE, RMSE, MAPE, R2 Score
• Feature importance extracted from Random Forest
• 30-day future forecast generated using average feature values as input
• 10% confidence band added to forecast for safety stock planning
5. Results & Model Performance
KPI / Metric Target / Benchmark
Linear Regression — MAE 7.52 units
Linear Regression — MAPE 11.8%
Linear Regression — R2 0.742
Random Forest — MAE 5.89 units
Random Forest — MAPE 9.1% (below 15% target)
Random Forest — R2 0.816 (explains 81.6% of variance)
Promotion Sales Lift +33.9% more units during promotion periods
30-Day Forecast Total 3,861 units (~129 units/day average)
Recommended Stock Order 4,247 units (+10% safety buffer)
Demand Insights
Finding DetailTop selling product SKU_107 — needs priority restocking
Top category Dairy — highest average daily demand
Highest demand season Summer — stock up before season begins
Top demand driver Promotion_Flag (33.9% importance score)
6. Business Recommendations
• Replace manual average-based planning with this ML forecast model immediately
• Order stock at least 7 days before high-demand months to avoid stockouts
• Safety stock formula: Average Daily Demand x 1.5 for top-selling SKUs
• Total stock to order for next 30 days: 4,247 units (+10% buffer over forecast)
• Schedule promotions strategically — they increase demand by 33.9%
• Reduce order quantities for bottom-3 products by 20% to cut overstock costs
• Stock up before Summer season — highest average demand across all products
• Retrain model monthly with fresh sales data to maintain forecast accuracy
• Build store-manager dashboard showing daily forecast vs actual units
7. Conclusion & Future Work
• Random Forest (MAPE 9.1%, R2 0.816) significantly outperforms Linear Regression baseline
• Promotion_Flag is the single most important demand driver at 33.9% feature importance
• The model is ready to replace manual historical-average planning at FreshMart
• Future work: ARIMA/SARIMA for pure time series, product-level individual models, LSTM for deep
learning
• Target: reduce stockouts by 20% and overstock holding costs by 15% within 6 months
