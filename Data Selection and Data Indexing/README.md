# Data Selection

Data Selection is a fundamental operation in Pandas, allowing us to extracrt specific subsets of data from a dataframe.

## Selecting Columns and Rows

We can select specific columns and rows from dataframe using below methods:
1. Using Square Brackets([]): To select one or more columns by their names, we can use square bracket with the column names as list.
   
   ``` columns = df[['column1', 'column2']]```

2. Using loc[] for label-based selection: The loc[] indexer allows us to select rows and columns by label. e cna specify both row and column labels.

   ``` data = df.loc[3:6, ['column1', 'column2']] ```

   Here both inner and outer indices are inlcusive.

3. Using iloc[] for integer-based selection: The iloc[] indexer allows us to select rows and columns by integer location.

   ``` data = df.iloc[1:4, 0:2] ```

   Here only inner is inclusive and outer is exclusive.

## Filtering/Conditional Selection

Conditional selection enables us to filter rows based on specific criteria.

1. Boolean Indexing: Create a boolean mask by applying a condition to a column and then use this mask to filter rows for the True condition.

   ``` data = df[df['Age'] > 30] ```

2. Multiple Conditions: We can combine multiple conditions using logical operators i.e (& for AND, | for OR).

   ```
   data = df[(df['Age'] > 25) & (df['Salary']> 50000)]

   data = df[(df['Age'] > 25) | (df['Salary']> 50000)]
   ```


## Indexing methods

Pandas provides various methods for customising and resetting the Dataframe index:

1. set_index(): This method allows us to set one or more column as Dataframe index.

   ```
   df = df.set_index('ID')
   or
   df.set_index('ID', inplace = True)
   ```

2. reset_index(): This method resets the index to the default integer index and if drop = True the it removes the existing index.

   ``` df = df.reset_index(drop = True)```

