# MarketInsight: Enhanced Stock Market Prediction Algorithm
This Project preedicts trends in the stock market using the models: LSTM, SVR, ARIMA, XGBoost, Randomforest
## 1. Summary:

People right now are talking about recession, layoff, and inflation. Are we facing the
downturn of the current business cycle or is it just a temporary retreat caused by the
pandemic? It is hard to tell. Nevertheless, we can draw some insights from the objective
data. 

As the world’s largest stock market, the U.S. stock market has the most mature
investors that are sensitive to the changes in the economy and also forward looking.
Therefore, I believe the stock market indices might be a good place for us to find out
what’s going on with the economy.

In this project, I focused on the Dow Jones Industrial Average(DJIA) index (Yahoo,
2022). The DJIA is composed of thirty blue-chip U.S. stocks, and those component
companies have sustained earnings performance over a significant period of time.

Analysis of those companies will give us a nice picture of the most solid part of the U.S.
economy. Furthermore, DJIA is the oldest continuing U.S. stock market index and will
make my analysis technically feasible. I hereby used DJIA closing data from 1992 to
present (Sept 2022), and 7533 data points were involved.

The data of DJIA is typical time series data. Time series data is a sequence of data
points collected over an interval of time, and it usually has four characteristics, i.e. trend,
seasonality, cyclicity and irregularity.

During my exploratory data analysis, I found an obvious uptrend which was backed
by the constant economic growth, significant cyclicity which could be explained by the
business cycles, and irregular patterns which were caused by many complicated
factors.

In time series analysis, time is taken as the independent variable. In this project, I
used both the traditional methods, such as ARIMA, and machine learning techniques,
including XGBoost, Random Forest, SVR and LSTM.

Traditional time series analysis such as ARIMA requires preprocessing of the target
variable (Dhaduk, H., 2021), while machine learning techniques can be much more
straightforward and are flexible with extra independent variables.

In my implementation of this project, I had the best result from the LSTM model which
produced the lowest root mean squared error. Unfortunately, LSTM is not a good model
for long-term prediction. But still, it can give us a peek into the near future.

Meanwhile, ARIMA can be a good reference for the long term trend. Therefore, the combination of
LSTM and ARIMA may give us a pretty good picture of the future market.

In my future work, I can further improve the modeling by implementing incremental
learning, transforming the target variable, considering extra independent variables, and
applying algorithms to inculcate outliers

## 2. Method

For this project, I started with exploratory data analysis to understand the structure
and hidden patterns in the data. I used the moving average technique to smooth the
data to avoid the impact of outliers.

After data preprocessing, I used LSTM, ARIMA, Random Forest, XGBoost and
Support Vector Regressor for data modeling and the Root Mean Squared error for
evaluation.

Details of my modeling algorithms are as follows:

● LSTM:

LSTM is a type of recurrent neural networks (RNNs) that is capable of learning
long-term dependencies, especially in sequence prediction problems. I hereby
used the values within the 60 days prior to i day to predict the value for i day.

● ARIMA:

ARIMA is a general class of model denoted as ARIMA(p,d,q), where p is the
order of the autoregressive model, d is the degree of differencing, and q is the
order of the moving-average model. ARIMA models use differencing to convert a
non-stationary time series into a stationary one, and then predict future values
from historical data. In this project, auto_arima model was implemented from
pmdarima.arima package, and 90 days moving average was selected as
dependent variable to control the fluctuation of the data. Model was selected by
minimizing the AIC score, and p = 1, d = 2, and q = 1 were chosen because they
generated the minimum AIC score, which was 23764.369. 

● Random Forest:

Time series cross validation was used to select training and testing data, and
random forest regressor was selected from sklearn.ensemble package.

● XGBoost:

Time series cross validation was used to select training and testing data, and
instead of using daily closed prices as the dependent variable, I used 60 days
moving average to control the fluctuation of the data. XGboost regressor from the
xgboost package was applied, with a learning rate of 0.3 and an iteration of 1000.

● Support Vector Regressor:

SVR is a learning method that differs from SVM in that it employs assumptions of
a linear function in a high-dimensional feature space. SVR employs an
insensitive loss function. SVR's regression function is as follows:

<img width="189" alt="Screenshot 2023-10-19 at 9 17 27 AM" src="https://github.com/vk1309/MarketInsight/assets/39329373/c7ea1c99-0924-4959-8492-276796379c8c">

Where w denotes weight and b denotes bias. The notation is a point in
feature space that represents the mapping result of x in an input space.

## 3. Results: 

This project compared the accuracy of different models based on their RMSE scores
and ploted visualization and concluded that LSTM performed the best. 

<img width="445" alt="Screenshot 2023-10-19 at 9 20 57 AM" src="https://github.com/vk1309/MarketInsight/assets/39329373/926c4a90-90cd-4b90-8b04-bbe0e65097a4">


