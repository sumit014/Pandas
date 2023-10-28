Machine learning model expects numerical data to work upon and Categorical data is a crucial part in all the dataset. We need to convert categorical data into numeric data for our model to work.

## Encoding Categorical Variables

Encoding categorical variables involves converting them into a numerical format that machine learning algorithms can understand.

Different encoding techniques are:
1. **One-Hot Encoding using pd.get_dummies()**:
   - One-hot encoding creates binary columns( zeros and ones ) for each category, indicating the presence(ones) or absence(zeros) of a category for each data point.
   - In a categorical column, if there are k unique values/category, it will create k new binary columns one for each category.
   - Only drawback of this approach is, it removes the original column.
     example:
```
import pandas as pd

data = {'Category': ['A', 'B', 'A', 'C', 'B'],
         'Count':[1,2,3,4,5]}
df = pd.DataFrame(data)

encoded_df = pd.get_dummies(df, columns=['Category'])
```

2. Label encoding:
   -  Lets say there are 100 unique values in a categorical column, in that case if we use one-hot encoding it would create 100 new columns.
   -  Label encoding help us with the above problem, in which it assigns a unique numerical value to each category.
   -  .astype('category').cat.codes method is used to convert category columns to label encoding.
  
```
import pandas as pd

data = {'Category': ['A', 'B', 'A', 'C', 'B']}
df = pd.DataFrame(data)

df['Category_Encoded'] = df['Category'].astype('category').cat.codes
```


## Sorting ordinal data
- Sorting ordinal data means to sort the ordinal columns in a certain order depending on the values of that column.
- Ordinal data represents categories with a natural order or ranking, such as low, medium, high, or small, medium, or large.
- **pd.categorical()** method helps us to achieve this sorting of ordinal data by converting the ordinal column into a pandas categotrical column, , and by specifying the parameters **categories=ordinal_order** and **ordered=True**.
- example:

```
import pandas as pd

data = {'Product': ['Product A', 'Product B', 'Product C', 'Product D'],
        'Size': ['Medium', 'Small', 'Large', 'Medium']}
df = pd.DataFrame(data)

ordinal_order = ['Small', 'Medium', 'Large']

print('Noraml Sorting:')
print(df.sort_values(by='Size'))

df['Size'] = pd.Categorical(df['Size'], categories=ordinal_order, ordered=True)
print('Ordinal Sorting:')
print(df.sort_values(by='Size'))
```
