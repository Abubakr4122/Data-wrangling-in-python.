# Data-wrangling-in-python.

24. Data wrangling in python.
             Join, combine and reshape, hierarchical indexing , combining and merging datasets reshape 

import pandas as pd

data = pd.Series([100, 200, 300, 400], index=[['USA', 'USA', 'India', 'India'], ['NY', 'CA', 'Delhi', 'Mumbai']])
print("1. Hierarchical Indexing:\n", data, "\n")
df1 = pd.DataFrame({
    'ID': [1, 2, 3],
    'Name': ['Alice', 'Bob', 'Charlie']
})

df2 = pd.DataFrame({
    'ID': [1, 2, 4],
    'Score': [85, 90, 75]
})

merged = pd.merge(df1, df2, on='ID', how='outer')
print("2. Merged Dataset:\n", merged, "\n")
df = pd.DataFrame({
    'ID': [1, 2],
    'Math': [90, 80],
    'Science': [85, 75]
})
melted = pd.melt(df, id_vars=['ID'], var_name='Subject', value_name='Score')
print("3. Melted DataFrame:\n", melted, "\n")
pivoted = melted.pivot(index='ID', columns='Subject', values='Score')
print("Pivoted DataFrame:\n", pivoted)
Output:
1. Hierarchical Indexing:
USA     NY        100
        CA        200
India   Delhi     300
        Mumbai    400
dtype: int64 

2. Merged Dataset:
   ID     Name  Score
0   1    Alice   85.0
1   2      Bob   90.0
2   3  Charlie    NaN
3   4      NaN   75.0 

3. Melted DataFrame:
   ID  Subject  Score
0   1     Math     90
1   2     Math     80
2   1  Science     85
3   2  Science     75 

Pivoted DataFrame:
Subject  Math  Science
ID                    
1          90       85
2          80       75

