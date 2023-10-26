Time Series data consists of data points collected or recorded at specific time intervals.

## Working with DataTime Data
- DateTime data is essential for time series analysis
- We can use pandas **pd.to_datetime()** method which provides robust support working with dates and times.
- pd.to_datetime()
  - This method allows us to convert our series with datetime to a pandas datetime series through which we can do much more analysis.
  - We can get year, month, day and hours.
  example:
```
import pandas as pd
data = {'DateTime' : ['2023-01-01 00:00:00', 2023-02-02 02:02:02', 2023-03-03 03:03:03']}
df = pd.DataFrame(data)

df['DateTime'] = pd.to_datetime(df['DateTime'])

df['Year'] = df['DateTime'].dt.year
df['Month'] = df['DateTime'].dt.month
df['Day'] = df['DateTime'].dt.day
df['Hour'] = df['DateTime'].dt.hour
```

## Resampling and Shifting

### Resampling
- Resampling is the process of changing the frequency of your time series data.
- It allos us to aggregate or transform data from one time frequency to another time frequency
- Common reasons behind resampling:
  - Aggregation: To get the broader view of the data, we may change the frequency of the data from high(eg: daily) to low(eg: monthly)
  - Interpolation: We may have data at irregular intervals and want to resample it to a regular interval or frequency for analysis or visualization.
 
- example:
  ```
  import pandas as pd
  data = {'Date': pd.date_range(start = '2023-01-01', periods = 10, freq = 'D'),
          'Sales': [i  for i in range(40)]}
  df = pd.DataFrame(data)
  monthly_sales = df.resample('M', on='Date').sum()
  ```

- In the above example, we resample daily sales data to monthly frequency and aggregating it by summing the sales for each month

### Shifting
- It is often used to calculate differences or time-based features in time series data.
- Also known as time lag or time shifting, involves moving data points forward or backward in time.
- Common usecase for shifting includes:
  - Calculating Differences: We can calculate the difference between the current data point and a previous or future data point. It is useful in understanding trends or changes in the data.
  - Time lags: We may want to create time lags of a variable to analyse how past values of that variable affect the future outcomes.
 
- example:
  ```
  import pandas as pd
  data = {'Date': pd.date_range(start = '2023-01-01', periods = 5, freq = 'D'),
          'Price': [100, 105, 110, 108, 112]}
  df = pd.DataFrame(data)
  df['price_change'] = df['Price'] - df['Price'].shift(1)
  ```

## Rolling Statistics
- Rolling statistics involves applying a statistical function to a fixed-size window of data points that moves through the dataset one step at a time
- It can be helpful to smooth out the noise in time series data, making underlying patterns more visible.
- They help detect trends and patterns over time, such as moving averages.
- It mainly consists of two things:
  - Window size: The rolling window has a fixed size specified by the user. This size determines how many data point are considered in each calculation or each step. The window size 3 means it will consider current point and two previous points.
  - Rolling Function: We apply a specific function to the data only within the rolling window.
 
- example:
  ```
  import pandas as pd
  data = {'Date': pd.date_range(start = '2023-01-01', periods = 5, freq = 'D'),
          'Price': [100, 105, 110, 108, 112]}
  df = pd.DataFrame(data)
  df['rolling_mean'] = df['Price'].rolling(window = 3).mean() # Here window size is 3 and rolling function is mean()
  ```
  
