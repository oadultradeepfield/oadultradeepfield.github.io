class: middle, center

# Introduction to Time Series Analysis

<big>Phanuphat Srisukhawasu (Oad)</big>

**<big>Machine Learning Department<br>
NUS Fintech Society</big>**

Week 6 (16 Sep 2024 - 20 Sep 2024) <br>
_(Modified on February 16, 2025)_

---

class: middle

### What are time series?

- **Time series** are data points indexed in an order of time.
- It could be sampled as frequent as we want: **every second, every minute, hourly, daily, monthly, yearly, etc.**

.center[<img src ="/slides/fintech-society/img/01-time-series-definition.jpg" height="340"/>]

---

class: middle

### Characteristics of Time Series

.center[<img src ="/slides/fintech-society/img/02-time-series-composition.png" height="400"/>

Note: **Residual** (a superset of noises) is **what we are left with**, after analyzing the other components.]

---

class: middle

## 1. Time Series Preprocessing

---

class: middle

### Setting Dataframe Index to Date and Time

- As we have a CSV file containing time series data, we could use `pd.read_csv()` to import your data as usual.
- But when we inspect the data, we generally see that the **data type of the date and time column is a string (object.)**

<br>
.center[<img src ="/slides/fintech-society/img/03-data-loading.png" height="320"/>]

---

class: middle

### Converting Date Column to `Datetime` Object

- We want to process the data in such way that the `Date` column is a `Datetime` object instead of a string.
- To accomplish this, we usually use

```Python
df['Date'] = pd.to_datetime(df['Date'])
```

- We also usually do `df = df.set_index('Date')`. This will make the processing more convenient.

<br>
.center[<img src ="/slides/fintech-society/img/04-time-series-index-datetime.jpg" height="240"/>]

---

class: middle

### Handling Missing Time Series Data

- For time series, a simple method to fill missing values at time $t_0$ is to use the value from the closest previous time $t < t_0$.
- For this example dataset, we already know that we don't have any missing data. But if we do, we could use `df = df.ffill()`. After that, we could use `sns.lineplot()` from Seaborn to visualize the data.

<br>
.center[<img src ="/slides/fintech-society/img/05-time-series-visualization.png" height="280"/>]

---

class: middle

### Aggregating Time Series Data

- In this example, we have a data recorded in a **daily basis.** In some cases, we may want to analyze the data in a **weekly, monthly, or yearly basis.**
- In Pandas, we could resample the data as frequent as we want: `df = df.resample(<FREQ>).mean()`.

.center[<img src ="/slides/fintech-society/img/06-time-series-weekly.png" height="280"/>]

Note: The above plot is generated from sampling the data using `'W'` as `<FREQ>` and calculate the average. This will resample the data **weekly.** The plot is more smoothed out compared to the previous. For other frequencies, you may refer to this [link](https://pandas.pydata.org/docs/user_guide/timeseries.html).

---

class: middle

### Creating Time Series Features - Lag Features

- To use machine learning, we need inputs or features. **What are the features for time series?**
- It does not make any senses to use the time index as the features, as the **date should not be correlated to the values.**
- In time series forecasting, we want to use values from the **past to predict the future** values.
- Using this principle, we can create features from the past values known as **lag features**.
- For example, we can use

```Python
df['lag1'] = df['Close'].shift(1)
```

This command creates a new column `'lag1'` that shows the closing price from one time step earlier.

- In general, we can pass in different values of steps other than `1` (i.e. `2,3,…`) to create lagging from multiple time steps.
- This allow us to have **multiple features** to train the model.

Note: The **numbers of lagging features** to use could be one of the **hyperparameters** to tune.

---

class: middle

### Creating Time Series Features - Lag Features

<br>
.center[<img src ="/slides/fintech-society/img/07-time-series-features.png" height="340"/>]
<br>

Note: The **numbers of lagging features** to use could be one of the **hyperparameters** to tune.

---

class: middle

## 2. Time Series Modeling

---

class: middle

### Introduction to ARIMA

<big><b>AR</b> (Autoregressive) + <b>I</b> (Integrated) + <b>MA</b> (Moving Average)</big>

- **ARIMA** is a **statistical model** used to forecast the time series based on the past values.
- Sometimes, we could solve the simpler problems using just ARIMA and _without any machine learning!_.
- In simple words, each part of ARIMA play the following roles:
  - **AR** = Previous values **lag features**.
  - **I** = Adjustments to make data stable _removing trends_.
  - **MA** = Adjustments to _smooth out the noises_.
- If you want to explore the mathematics behind ARIMA, feel free to visit this site (click on the formula XD):

[$$y\_t=\phi\_1y\_{t-1}+\phi\_2y\_{t-2}+\cdots+\phi\_py\_{t-p}+\theta\_1\epsilon\_{t-1}+\theta\_2\epsilon\_{t-2}+\cdots+\theta\_q\epsilon\_{t-q}+\epsilon\_t.$$](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average)

---

class: middle

### Implementing ARIMA in Python

- **ARIMA** is in a library called `statsmodels`. We can import it using

```Python
from statsmodels.tsa.arima.model import ARIMA
```

- We can **fit the model** to the data using

```Python
model = ARIMA(df['Close'], order=(p, d, q)).fit()
```

- `p` is the **number of lag features** to use (i.e. `p = 2` will use only the values at step $t-1$ and $t-2$.)
- `d` is the **number of times we differenced the series** ($x(t)-x(t-1)$,) to make it stationary. We start with $d=0$.
- `q` is the **number of lagged forecast errors** to use.
- After fitting the model, we could **forecast** the time series values by assigning

```Python
predictions = model.predict(start=0, end=len(df)-1)
```

---

class: middle

### Example Results of ARIMA

.center[<img src ="/slides/fintech-society/img/08-time-series-arima.png" height="400"/>

Note: Sometimes, it is difficult to judge the **performance** by eyes. In the next section, we will introduce **numerical metrics to evaluate the models**.]

---

class: middle

## Machine Learning Models for Time Series

---

class: middle

### Splitting Time Series Data

- When it comes to time series, we **cannot use random subsets** of data as the _training and testing sets_.
- Obviously, we want to train the model on _the past data to forecast the future_ Therefore, this is what we usually do:

.center[<img src ="/slides/fintech-society/img/09-time-series-data-split.png" height="360"/>]

---

class: middle

### Using Random Forests and XGBoost

- Last week, you have already learned about **Decision Trees.** In this session, we are introducing more advanced tree-based models which are _constructed by ensembling multiple trees_.
- With that being said, we shall introduce two primary methods for ensembling multiple trees:
- **Bagging**: We construct multiple decision trees using _random subsets of data and features_. The final model decision is the **voting (average prediction)** from all of the trees. The model that use this ensembling method is **Random Forest.**
- **Boosting**: We construct _new trees from the previous trees._ The early trees are called the **weak learner.** The errors made by them are taken into account as **the weights of importance**. to train the subsequent trees, creating **strong learner** at the end. The models that use this ensembling method are **XGBoost, LightGBM**, and their variations.

---

class: middle

### Bagging and Boosting Illustration

.center[<img src ="/slides/fintech-society/img/10-bagging-and-boosting.jpg" height="400"/>

Note: you can read more about the mathematical details of each model [here](https://www.mit.edu/~9.520/spring06/Classes/class10.pdf?ref=jeremyjordan.me).]

---

class: middle

### Implementing Random Forests & XGBoost in Python

- Like most models, Random Forests can also be accessed through `Scikit-learn` library.

```Python
from sklearn.ensemble import RandomForestClassifier # or RandomForestRegressor
```

- However, XGBoost **is not** inside `Scikit-learn`. We can import it from the library `xgboost`, where we could use `XGBClassifier` and `XGBRegressor`. You may need to install it first if you haven't

```bash
pip install xgboost
```

- After having the models, you could use `model.fit()` on the training data as well as the other methods you have learned.
- Now, how do we evaluate the models using **metrics?**

---

class: middle

### Evaluating Machine Learning Model Performance

- In time series forecasting, we are trying to predict the _numerical outputs based on inputs._ It's just **regression!**
- To evaluate regression models, we usually look at the **average errors** they made (lower is better.)
- **Root Mean Squared Error (RMSE):**
  $$RMSE=\left(\frac{\sum\_{i=1}^N(y\_i-\hat{y\_i})^2}{N}\right)^{1/2}$$
- **Mean Absolute Error (MAE):**
  $$MAE=\frac{\sum\_{i=1}^N|y\_i-\hat{y\_i}|}{N}$$

Note: Sometimes, we may also want to look at the _coefficient of determination (`r2_score`)_. This value range from $0-1$, **higher is better.**

---

class: middle

## Time Series Processing in

## `Scikit-learn` Cheat Sheet

---

class: middle

## Data Preprocessing Summary

1. Convert the date and time column from string to Pandas' `Datetime` object using
   ```Python
   df['Date'] = pd.to_datetime(df['Date'])
   ```
2. Set the dataframe index to be that date and time column using
   ```Python
   df = df.set_index('Date')
   ```
3. Deal with the missing data with the appropriate methods. You could try a forward fill using `df = df.ffill()`.
4. Resample the data to be indexed at the frequency you need (i.e. weekly, daily, hourly, etc.) using
   ```Python
   df = df.resample(<FREQ>).mean()
   ```
5. Generate multiple lag features and assigning them to multiple columns using
   ```Python
   df[<LAG>] = df['Close'].shift(<STEP>)
   ```

---

class: middle

### Model Training Summary

1. Split the data into **training and testing** by simply _slicing the dataframe_ If we have enough data, we could split the data into half training and half testing (i.e.

   ```Python
   df_train = df.loc[:len(df)//2, :] # and
   df_test = df.loc[len(df)//2:, :]
   ```

2. Create **features and target** (for each training and testing):

   ```Python
   X_train = df_train.loc[:, ['lag1', 'lag2', 'lag3', ...]]` # and
   y_train = df_train.loc[:, 'Close']
   ```

3. Train the model on the training data. For example:
   - Using **Random Forests**: `model = RandomForestRegressor()` and then<br> `model.fit(X_train, y_train)`.
   - Using **XGBoost**: `model = XGBRegressor()` and then `model.fit(X_train, y_train)`.

---

class: middle

### Model Evaluation Summary

1. View the predicted time series by using
   `Python
    y_train_pred = model.predict(X_train) # and/or
    y_test_pred = model.predict(X_test)
    `
   then plot the results.

2. Evaluate the numerical metrics **(RMSE, MAE, and R-Squared)** using functions from `sklearn.metrics`. For example:

- `mae = mean_absolute_error(y_test, y_pred_test)`
- `rmse = root_mean_squared_error(y_test, y_pred_test)`
- `r2 = r2_score(y_test, y_pred_test)`

**Recap**: Generally, we want to evaluate the model performance on the **testing set**, which reflects how well can the _model generalize to unseen data_.

3. Using the performance metrics, we can iteratively _tune the models until getting the desired performance_.

---

class: middle

## Extra: Time-Series Cross Validation

---

class: middle

### Introducing `TimeSeriesSplit`

- We know from the previous sessions that we use **cross-validation** to properly tune the _hyperparameters_ while having a separated test set as the **actual unseen data.**
- For time series, the appropriate way for cross validation is to use
  ```Python
  sklearn.model_selection.TimeSeriesSplit()
  ```
- You may also pass an argument `gap` which determines how many samples you want to **exclude** between the training and validation set.
- After assigning `cv = TimeSeriesSplit(n=5, gap=1)`, we can pass `cv` to classes like `GridSearchCV(cv=cv)` or `RandomizedSearchCV(cv=cv)` and then tune the hyperparameters as wished.

---

class: middle

### `TimeSeriesSplit` Example

- This is how the cross-validation looks like when using `TimeSeriesSplit(n_splits=4)`.

.center[<img src ="/slides/fintech-society/img/11-time-series-split.png" height="360"/>

Note: More complex models like **Random Forests** and **XGBoost** have lots of hyperparameters to tune. You may consider looking at a _lightweight version of XGBoost_, **LightGBM** as well.]
