# Data Structures

Pandas provide two fundamental data structures:
1. Series
2. DataFrame

These data structures are the building block of data manipulation and analysis in Python.

Understandig of these two data structures is essential for effective data handling with Pandas.

## Series

- A series is a **one-dimensional labeled array** that can hold various data types, such as integers, floats, string, or even custom objects.
- It is similar to a column in an Excel or a SQL table.

Key Features of the Series are:

1. **Labeling**: Each element in a Series has a label or an index, which allows for easy access and manipulation of data.
2. **Homogenous data**: Series typically stores data of same data type throughout the column unlike lists, ensuring consistency.aa
3. **Vectorized Operations**: We can perform vectorized operations on a Series which makes it very effiecient for element wise calculations without applying any loop. This increases the performance and reduces the execution time.
   - Example:
     ```
     import pandas as pd
     
     data = [1, 2, 3, 4, 5]
     
     series = pd.series(data, name="MySeries")
     
     series = series * 2 # Vectorized operation
     ```


## DataFrame

- A dataframe is a **two-dimensional, tabular data structure with labeled axes**(i.e rows and columns).
- It resembles a spreadsheet or an SQL table.
- It is the primary data structure for data analysis in Pandas.

Key Features of the DataFrames are:

1. **Columns**: Each column in a dataframe is a **series**, which means it can hold different data types.
2. **Indexing**: DataFrames have both row and column indexing, allowing for a flexible data selection.
3. **Data Allignment**: Like Series, DataFrames can align data based on labels, making operations easy and intuitive.
4. **Data Integration**: We can merge, join, and concatenate DataFrames to combine and analyze data from various sources.

- Example:
  ```
  import pandas as pd
     
     data = { "Name":["Alice", "Bob", "Charlie", "David"],
  
               "Age":[25, 30, 35, 40],

               "City":["New York", "San Francisco", "Los Angeles", "Chicago"] }
     
     df = pd.DataFrame(data)
     
     df.rename(columns = {'Name': 'Person_name'}, inplace = True)
  ```

