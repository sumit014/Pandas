Data Manipulation is a core task in data analysis and involves transforming and modifying the data to derive insights or prepare it for further analysis.

## Apply Functions to Dataframes

1. iterrows()
   
We can do element wise operations for the data frame using python .iterrows() method. However, it is not recommended to do element or row wise operation on a dataframe.
Pandas is optimised for vectorised operation. Vectorised operation can be more effiecient than any other approach.

```
import pandas as pd

data = {'Name': ['Alice', 'Bob', 'Charlie'],
        'Age': [10, 15, 20]}

df = pd.DataFrame(data)

for index, row in df.iterrows():

  print(f"Index: {index},, Name:{row['Name']}, 'Age':{row['Age']}")
```

2. apply()

   - This method is use to apply custom function to a series or to a entire dataframe.
   - When used on a series, each element of the column will be passed to a function.
   - When used on an entire dataframe, based on the axis(1-row, 0-column)  the entire row or the entire column will be passed to the function.
  
   ```
   def square(x):
   
     return x**2

   df['column'] = df['original_column'].apply(square)
   ```

3. map()

   - This method applies a function to each element of a Series.
   - It is particularly useful for transforming one column based on values from another.
  
   ```
   mapping_dict = {'A': 1, 'B':2, 'C':3}
   
   df['new_column'] = df['old_column'].map(mapping_dict)
   ```

4. applymap()

   - When we want to apply a function to each element in the entire DataFrame.

   ```
   data = {'A':[1,2,3], 'B':[4,5,6]}
   
   df = pd.DataFrame(data)

   def add(x):
   
     return x + 10

   df = df.applymap(add)

   ```

## Adding and Removing Columns

1. Adding Columns: To add a new column or replace a existing one, simply assign values to it.

   ```
   df['New_column'] = [1,2,3,4]
   ```

2. Removing Columns
   - drop() method is used to remove columns
   - We can use axis = 1/'columns' to drop column, or use axis=0/'index' to drop the row.
  
   ```
   df['New_column'] = [1,2,3,4]

   df.drop(['Column1', 'Column2'], axis=1, inplace=True)
   ```

3. Combining DataFrames(Concatenation, Joining, Merging)

   1. Concatenation
      - We can concatenate Dataframes vertically or horizontally using pd.concat().
      - axis=0 will concatenate them in the rows, axis=1 will concatenate them in the columns.
      - It will check for the common columns between both the dataframes and for the matched columns, it will concatenate in the rows.

      ```
      df1 = pd.DataFrame(data1)
      
      df2 = pd.DataFrame(data2)

      result = pd.concat([df1, df2], axis=0)
      ```

   2. Joining
      - We can use SQL-like joins on DataFrames using the merge() method.

   3. Merging
      - Pandas allows to merge the dataframe based on common columns.
      - We can perform various join operation such as inner, outer, left and right with merge().
      - An inner join will only keep where the cells of common columns have matched.
      - An outer join will keep every row from both data frames.
      - Left will keep all the rows from the left table
      - Right will keep all the rows from the right table.

      ```
      import pandas as pd
      
      result = pd.merge(df1, df2, on='ID', how='inner') # Inner join on ID

      result = pd.merge(df1, df2, on='ID', how='left') # Left join on ID
      ```

      - If the mathcing column names are different in both the data frames then we can use below code:

      ```
      pd.merge(df1, df2, left_on="ID1", right_on="ID2")
      ```
      

   
