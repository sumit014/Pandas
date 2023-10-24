Data Aggregations plays a critical role in data analysis and involves applying aggregation functions like sum, mean, count, etc to groups of data.

## Grouping Data

1. groupby with a single column
   - This method allows you to group data based on one or more columns.
   - It is same as SQL version of GROUP BY statement.
   - How to use this function:
     - First, we need to pass the column name on which we want to group the data.
     - Then we can choose the column between which we want to compare the grouped data.
     - Select the aggregate function like mean, sum, median, max, etc.
  
   - example:
   ```
   import pandas as pd
   
   data = {'Category': ['Electronics', 'Clothing', 'Electronics', 'Clothing'],
           'Sales': [1000, 500, 800, 5000]}
   
   df = pd.DataFrame(data)
   
   grouped_data = df.groupby('Category')

   total_sales = grouped_data['Sales'].sum()
   ```

2. groupby with multiple columns
   - We can even group with multiple columns by passing a list of columns we want to groupby
   - Suppose we have a dataset of students marks and we want to group it according to Class and Gender.
   ```
   import pandas as pd
   
   data = {'Class': ['A', 'B', 'A', 'B', 'A', 'B'],
           'Gender': ['Male', 'Male', 'Female', 'Female', 'Male', 'Female'],
           'Math_Score': [85, 92, 78, 89, 90, 86],
           'English_Score': [88, 94, 80, 92, 92, 88]}
   
   df = pd.DataFrame(data)
   
   grouped_data = df.groupby(['Class', 'Gender'])

   agg_results = grouped_data['Math_Score'].mean()
   ```

### Note: When we apply an aggregation function to grouped data without specifying the column, then it will be applied to all the numeric columns in the DataFrame.

## Aggregation Functions
- Aggregation functions are essential for summarizing data with groups.
- Common Aggregations functions are: sum(), max(), min(), mean(), median(), count()
- agg() - this allows you to apply custom aggregation functions.
- example:
```
   import pandas as pd
   
   data = {'Class': ['A', 'B', 'A', 'B', 'A', 'B'],
           'Gender': ['Male', 'Male', 'Female', 'Female', 'Male', 'Female'],
           'Math_Score': [85, 92, 78, 89, 90, 86],
           'English_Score': [88, 94, 80, 92, 92, 88]}
   
   df = pd.DataFrame(data)
   
   grouped_data = df.groupby(['Class', 'Gender'])

   agg_results = grouped_data['Math_Score'].agg(['mean', 'min', 'max'])

   OR

   agg_results = grouped_data.agg({'Math_Score': ['mean', 'min', 'max'],
                                    'Physics_Score': ['mean', 'min', 'max']})
```

## Pivot tables and Cross-Tabulations

- Pivot tables provides a structured way to arrange and analyze data from different angles.
- we can use pd.pivot_table() to create pivot tables.
- pd.crosstab() are another method to aggregate data, especially dealing with categorical variables.
- example:
```
import pandas as pd
   
   data = {'Class': ['A', 'B', 'A', 'B', 'A', 'B'],
           'Gender': ['Male', 'Male', 'Female', 'Female', 'Male', 'Female'],
           'Math_Score': [85, 92, 78, 89, 90, 86],
           'English_Score': [88, 94, 80, 92, 92, 88]}
   
   df = pd.DataFrame(data)
   
   pivot_table = pd.pivot_table(df, index = 'Class', columns = 'Gender', values = 'Math_Score', aggfunc = 'sum')
   cross_tab = pd.crosstab(df['Class'], df['Gender'])

```
