# Data Cleaning

Data Cleaning is a critical step in the data preparation process.

## Handling Missing Data

Missing data is a common issue in read-world datasets.

1. **isna() and notna()**: These methods allows us to identify missing and non missing values in a dataframe.

   Applying this method for a column will return the boolean list with True for the indices where there is a missing value.

   ``` data = df[df['Column'].isna()]```

   To get the sum of null values in a column

   ```df.Column.isna().sum()```

   To get the sum of null values for each column

   ```df.isna().sum()```

2. **fillna()**: We can replace missing values with a specified value or a calculated value using the fillna() method.

   ```
   df['Column'].fillna(value = 0, inplace = True)

   df['Column'].fillna(value = df['Column'].mean(), inplace = True)

   df['Column'].fillna(value = df['Column'].median(), inplace = True)

   df['Column'].fillna(value = df['Column'].mode(), inplace = True)
   ```
   
3. **dropna()**: This method is used to remove rows and columns containing missing values from the dataframe. Default, it will remove the rows(axis = 0) where any of the column values is missing(how = 'any').

   ```
   df.dropna() # drops all rows where any columns is missing
   
   df.dropna(subset = ['Column1', 'Column2'], how = 'any', inplace = True) # It will check for missing values in only Column1 and Column2 columns.

   df.dropna(axis = 1) # drops columns
   ```
   
  Note: 
  - By using how = 'any', will drop the rows where any of the column values are missing.
  - By using how = 'all', will drop the rows where all of the specified column values are missing.

## Removing Duplicates

Duplicate rows can skew our analysis results. Pandas offers below methods to remove duplicates:

1. **duplicated()**: This method identifies duplicate rows in a DataFrame.

   ```
   duplicates = df[df.duplicated()] # Results the duplicated columns when there is an any other row with exact match of all the columns.
   
   duplicates = df[df.duplicated(subset = ['Column1', 'Column2'])] # when there is a match of the specified columns
   
   df.duplicated(subset=['column1', 'column2']).sum()# to check the count of the duplicates
   ```
   
  Note:
  - By default duplicated() uses keep='first', which keeps the first observed row in the dataframe and marks the later observed one as True, which specifies they are duplicates
  - If we want to keep the last observed duplicated row in the dataframe then wwe can give keep='last'.
  - If we want to see all the occurence, then give keep='False'.

2. **drop_duplicates()**: This method removes duplicate rows from the DataFrame.

   ```
   df.drop_duplicates() # drop duplicated rows, it will show the data after dropping
   
   df.drop_duplicates().shape() # check the shape after dropping
   
   df.drop_duplicates(inplace = True)# to save the dataframe after dropping
   ```

## Data Type Conversion

Correct data types are crucial for data analysis.

1. **astype()**:
   - We can chanhge the data type of a specific columns using the astype() method.
   - astype is also useful to convert booleans to int, basically for all True values it will replace with 1, and the False to be 0.

   ```
   df['Column'] = df['Column'].astype('float')

   df.Sex = pd.Series(df.Sex == 'Male').astype('int')
   ```

## String Operations

When working with text data, Pandas offers string operation through **.str**, an accessor to apply for the entire column which is of object type.

1. **.str.lower() and .str.upper()**: These methods converts strings to lowercase or uppercase for the entire column values.
   ```
   df['Name'] = df['Name'].str.lower()
   
   df['Name'] = df['Name'].str.upper()
   ```

2. **.str.replace()**: This method is used to replace substrings within strings.

3. **.str.contains()**: This method allows you to check if a specific substring or pattern exists within a string.
   ```
   data = df[df['Text'].str.contains('keyword')]

   df.item.str.contains('chicken').astype('int')
   ```

4. **.str.slice()**: We can extract a substring from each string in a Series using .str.slice() method. Specify the start and end positions to define the slice.
   ```
   df['Substring'] = df['Text'].str.slice(start = 2, stop = 5)
   ```
   
