3.1.1 Dataset
The GDP data used in this study was obtained from the World Economic Outlook database of
the International Monetary Fund (IMF) (International Monetary Fund, 2026). The GDP data set
was selected from 2000 to 2026.

3.1.2 Missing data
Using the dropona() function, missing values can be removed to ensure data consistency.

3.1.3 Train-Test Split
The data set is divided into a training set and a test set in a 4:1 ratio. The training set covers the
period from 2000 to 2021, while the test set spans from 2022 to 2026.

3.1.4 Stationarity
An Augmented Dickey-Fuller (ADF) test was conducted to assess the stationarity of the GDP
series. If the results indicated that the series was non-stationary, first-order differencing was
applied to stabilize the mean of the series.

3.1.5 Feature Engineering
To enable the use of machine learning models, the time series was transformed into a supervised
learning problem. Lag features were constructed on the basis of the differenced GDP series, where
past observations were used as predictors for the current value. In the program, the model will
automatically evaluate the number of lag features and select the optimal number of lag features
for the prediction of GDP.

3.2.1 ARIMA Model
The optimal order (p,d,q) was selected on the basis of the lowest Akaike Information Criterion
(AIC). After fitting the model in the training set, a one-step rolling forecast was performed on the
test set to predict future GDP values. This approach ensures that the model is always trained on
past observations before forecasting the next value.

3.2.2 Support Vector Regression (SVR)
In SVR, hyperparameters C, gamma, and epsilon were adjusted by brute-force traversal to minimize
the root mean square error (RMSE) after standardization. Then, the final model trained on the
entire training set using the best parameters was applied to generate the prediction results for the
test set.

3.2.3 Random Forest
The model parameters in the Random Forest regression, including the number of trees, maximum
depth, minimum samples per split, and leaf size, were predefined on the basis of previous experi-
mentation. This model is trained based on the logarithmic difference of the values, as it has been
verified through comparative tests that this training method yields better results.
