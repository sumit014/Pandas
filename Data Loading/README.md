# Data Loading

Pandas provide a wide range of functions and methods for efficiently loading data **from various sources and formats into DataFrames.**

## Reading data from different sources(CSV, Excel, SQL, etc.)

1. Load data from csv file
   ```
   import pandas as pd
   df = pd.read_csv('data.csv')
   ```

2. Load data from exccel file
   ```
   import pandas as pd
   df = pd.read_excel('data.xlsx')
   ```

   
3. Load data from a particular sheet from a excel file
   ```
   import pandas as pd
   df = pd.read_excel('data.xlsx, sheet_name = 'Sheet1')
   ```

4. Load data from a SQL database table
   ```
   import pandas as pd
   from sqlalchemy import create_engine
   engine = create_engine('sqlite:///mydatabase.db')
   query = 'SELECT * FROM mytable
   df = pd.read_sql_query(query, engine)
   ```

6. Load data from an HTML table on a webpage
   ```
   import pandas as pd
   url = 'https://example.com/data-table.html'
   df = pd.read_html(url)
   ```

7. Load data from a JSON file
   ```
   import pandas as pd
   df = pd.read_json('data.json')
   ```
   
8. Load data from a Parquet file
   ```
   import pandas as pd
   df = pd.read_parquet('data.parquet')
   ```

## Important Parameters for read_csv:

1. **filepath**: specifies the path to the csv file. We can provide the file path as a string, a URL, or a file like object.
2. **names**: to override the column names we need to use this parameter with the list of new column names.
3. **sep**: defines the characterused to separate fields in CSV files. Default value is ',' nut e can specify other character.
4. **index_col**: this parameter specifies which column should be used as the data frame index. We can pass either the column name or index of it.
5. **skiprows**: this parameter allows you to skip a specific number of rows at the begining of the CSV file. It can be useful when there are metadata or comments at the top of the CSV file.

## Displaying DataFrames

We can see the top 5 and bottom 5 rows of a dataframe by just typing the name of the data frame and executing the cell.

- head(n): This method displays the first n rows of the data. Default is 5 rows.
  ```df.head(n)```
- tail(n): This method shows the last n rows of the data frame.
  ```df.tail(n)```
- sample(n): if want to see random rows from the DataFrame, use this method.
  ```
  df.sample(n)
  Here, 10 represents the number of random rows to represent.
  ```
  
