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
