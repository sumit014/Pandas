## Element-wise operations using eval

**eval()**: 
- The eval() method in Pandas allows you to perform efficient element-wise operations on a DataFrame using a string expression.
- It's particularly useful for large DataFrames and complex operations.
- example:

```
# Example DataFrame
import pandas as pd

data = {'A': [1, 2, 3, 4],
        'B': [10, 20, 30, 40]}
df = pd.DataFrame(data)

# Using eval to create a new column C
df.eval('C = A + B', inplace=True)

# Calculate a new column 'D' using a complex expression
df.eval('D = (A * 2) + (B / 3)', inplace=True)
```

## Advanced Filter Operations Using query

**query()**:
- The query() method allows you to filter rows in a DataFrame based on a specified condition using a string expression.
- It's a concise way to filter data.
- example: we use query() to filter rows where the 'Age' is greater than 30.

```
# Example DataFrame
import pandas as pd

data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],
        'Age': [25, 30, 35, 40],
        'Salary': [50000, 60000, 70000, 80000]}
df = pd.DataFrame(data)

# Using query to filter rows
filtered_df = df.query('Age > 30')

# Use query to filter rows based on multiple conditions
filtered_df = df.query('(Age > 30) and (Salary > 60000)')
```

## **Note**: Both eval() and query() are designed to improve performance when working with large DataFrames and complex operations.




## Multi-Indexing
- Multi-indexing allows you to create DataFrame structures with multiple levels of index hierarchy.
- It’s especially useful for handling data with complex, multi-dimensional relationships.
- It is also known as hierarchical indexing
- example:

```
import pandas as pd

# Sample hierarchical DataFrame
data = {'Department': ['HR', 'HR', 'Engineering', 'Engineering'],
        'Employee': ['Alice', 'Bob', 'Charlie', 'David'],
        'Salary': [60_000, 65_000, 80_000, 75_000]}
df = pd.DataFrame(data)

# Create a hierarchical index
hierarchical_df = df.set_index(['Department', 'Employee'])

# Accessing data
print(hierarchical_df.loc[('HR','Bob')])  # Access HR department Bob data
```

## Handling Outliers

- Outliers are values that deviate from the rest of the data.
- Handling outliers is an essential step in data preprocessing, as outliers can significantly impact the results of your analysis and statistical models.

### **Identifying Outliers**: 
- We can use boxplot to visualize the outliers.
- The box in the plot represents the interquartile range (IQR), which is the range between the first quartile (Q1) and the third quartile (Q3) of the data.
- The length of the box indicates the spread of the middle 50% of the data.
- The “whiskers” are lines extending from the box’s edges. They represent the range of data within a certain distance from the quartiles. Typically, they extend 1.5 times the IQR.
- Any data points outside this range are considered potential outliers.

## Note: It’s important to note that not all data points outside the whiskers are necessarily outliers; they are considered potential outliers that should further be investigated. Outliers can provide valuable information or errors in the data, so it’s essential to understand the context and domain when deciding how to handle them.

```
# Create a sample DataFrame
data = {'Values': [25, 30, 200, 40, 20, 300, 35, 45, 30]}
df = pd.DataFrame(data)

# Box plot to visualize outliers
df.boxplot(column='Values')
```

### **Outlier Handling by NaN**: 
- Once we have identified outliers, we can handle them manually.
- We can replace outlier values with NaN to effectively remove them from calculations.
- example:

```
threshold = 100  # Define your threshold for outliers
df['Values'][df['Values'] > threshold] = None  # Replace outliers with NaN
```

### **Outlier Handling by Clip Values**: 
- Clipping is the process of setting upper and lower bounds on a variable to limit extreme values to a specified range.
- This can be useful for mitigating the impact of outliers without removing them entirely from the dataset.
- It replaces values in the DataFrame with the specified bounds if they fall outside the specified range.
- example:

```
import pandas as pd
data = {'Values': [25, 30, 200, 40, 20, 300, 35, 45, -100]}
df = pd.DataFrame(data)

# Define upper and lower bounds
lower_bound = 0
upper_bound = 100

# Clip values to the specified bounds
df['Values'] = df['Values'].clip(lower=lower_bound, upper=upper_bound)
```

- Eg: In this example, values 200,300, and -100 are outliers. So once we set a range of lower bound and upper bound, we can pass it to the clip function. Any values higher than the upper bound will be replaced with the upper bound values, and similarly lower bound value for the values lesser than the lower bound. So, 200 and 300 will be replaced with 100 and -100 will be replaced with 0.

## Memory Optimisation

- Memory optimisation is crucial while working with large dataset.
- Pandas provide techniques to reduce memory consumption while maintaining data integrity.

1. **Choose the Right Data Types**:
- Use appropriate data types for your columns. For example, use int8 or int16 for integer columns with small value ranges, and float32 for floating-point columns.
- Consider using categorical data types for columns with a limited number of unique values. This reduces memory usage and can improve performance when working with categorical data.

2. **Use Sparse Data Structures if your data has too many missing values**:
- Pandas support sparse data structures, such as SparseDataFrame and SparseSeries, which are suitable for datasets with a lot of missing values.
- Sparse data structures store only non-missing values, reducing memory usage.

3. **Read Data in Chunks**:
- When reading large datasets from external sources, use the chunksize parameter of functions like read_csv() to read the data in smaller chunks rather than loading the entire dataset into memory at once.
  
4. **Optimize GroupBy Operations:**
- Use the as_index=False parameter when performing GroupBy operations to avoid creating a new index, which can consume additional memory

5. **Release Unneeded DataFrames**:
- Explicitly release memory by deleting DataFrames or Series that are no longer needed, using the del keyword. This frees up memory for other operations.
