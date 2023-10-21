# Data Inspection

Pandas provides methods to inspect fundamental insights into your data.

## Data Exploration

1. shape: This attribute gives a set of which the first element specifies the no of rows and second element specifies the no of columns.
2. info(): This method provides a concise summary of the DataFrame, including the data types, non-null counts, and memory usage.
3. dtypes: This attribute helps to see the data types of the columns of dataframe.
4. describe(): This method generates basic statistics for each numeric column in DataFrame, such as cout, mean, standard deviation, minimum, maximum values.

## Unique Values, Value Counts and Basic Statistics

For **categorical and discrete** data, we can explore unique values and their frequencies:

1. nunique(): This method calculates the number of unique values in each column. It helps in understanding of diversity of data in categorical columns.
2. column_name or ['column_name']: Use to access a specific column of a DataFrame. We can use the second approach only if the column name has a space in it.
3. value_counts(): This method is used to get the occurence of each unique value in a particular column.

- Basic Statistics: We can calculate additional statistics for a specific column such as the sum, max, min, mean, median, mode using mathematical functions or using statistics library.
