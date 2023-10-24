Data Visualisation is a powerful and effective way to explore and communicate insights from the data.

## Finding Correlation
- Correlation is basically how one variable is related to another variable.
- corr() method can be used to get the correaltion of a column with other columns.
- If the value is close to 1 then the columns are highy positively correlated
- If the value is close to -1 then the columns are highly negatively correlated.

## Sorting Data and Creating Basic Plots

- sort_values()
    - This method is used to sort series or dataframe.
    - We can use 'by' parameter to specify based on which column we want to sort.
    - We cna use 'ascending' parameter to sort in ascending or descending order.
 
- Below are some plots which we can plot using pandas.
- In the X and u, we can specify the series we want to plot.
    1. Line Plot
       
      ``` df.plot(x = 'X', y = 'Y', kind = 'line') ```
      
    2. Bar Plot
       
      ``` df.plot(x = 'Category', y = 'Count', kind = 'bar' )```
      
    3. Barh Plot
       
      ``` df.plot(x = 'Count', y = 'Category', kind = 'barh') ```
      
    4. Histogram
       
      ``` df['Value'].plot(kind = 'hist', bins = 20) ```
      
    5. Box Plot
       
      ``` df.plot(y = 'Value', kind = 'box') ```
      
    6. Area Plot
       
      ``` df.plot(x = 'X', y = 'Y', kind = 'area') ```
      
    7. Scatter Plot
       
      ``` df.plot(x = 'X', y = 'Y', kind = 'scatter') ```
      
    8. Pie Chart
       
      ``` df['Category'].value_counts().plot(kind = 'pie') ```
      
    9. Hexbin Plot
        
      ``` df.plot(x = 'X', y = 'Y', kind = 'hexbin', gridsize = 20) ```
      
    10. Stacked Bar Plot
        
      ``` df.pivot_table(index = 'Cagtegory', columns = 'Subcategory', values = 'Value', aggfunc = 'sum').plot(kind = 'bar', stacked = True) ```
       
    11. Line Plot
        
      ``` df.plot(x = 'Date', y = ['Series1', 'Series2'], kind = 'line') ```
       
- Advanced Plots:
  1. KDE Plot(Kernel Density Estimate)
     
         ``` df['Value'].plot(kind = 'kde') ```
    
  2. Density Plot
     
         ``` df['Value'].plot(kind = 'density') ```
    
  3. Boxen Plot
     
         ``` df.plot(y = 'Value', kind = 'boxen') ```
