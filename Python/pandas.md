# Pandas

## Introduction

pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool.

## Usage

```python
import pandas as pd
# Pandas Series
s = pd.Series([1, 2, 3, 4])

# Index
s.index

# Values
s.values

# Get values by [index]
s[2]

# Create DataFrame
pd.DataFrame(dict)
df = pd.read_excel('file-name')
df = pd.read_csv('file-name')

# head()
df.head(3) # default 5 rows

# Get data
## dict
df['city']
## loc for index label
df.loc[['Goldfinger', 'city']]
## iloc
df.iloc[[0,4]]
df.iloc[0:4]

# drop()
## axis=1 >> colums; axis=0 >> rows
df.drop(["math"], axis=1)
## dropna()
## drop_duplicates()

# filter
df[df["math"] > 80]
## isin()
df[df["name"].isin(["John"])]

# sort_values()
## ascending=True >> increment; ascending=False >> decrease 
df.sort_values(["math"], ascending=True)
```

## Reference

[Pandas](https://pandas.pydata.org/)

[Pandas Basic Introduction](https://medium.com/seaniap/pandas%E5%9F%BA%E7%A4%8E%E4%BB%8B%E7%B4%B9-%E9%80%B2%E5%85%A5%E8%B3%87%E6%96%99%E7%A7%91%E5%AD%B8%E7%9A%84%E9%A0%98%E5%9F%9F-be9894b3548)

[Pandas DataFrame](https://medium.com/seaniap/pandas%E5%9F%BA%E7%A4%8E%E4%BB%8B%E7%B4%B9-%E9%80%B2%E5%85%A5%E8%B3%87%E6%96%99%E7%A7%91%E5%AD%B8%E7%9A%84%E9%A0%98%E5%9F%9F-be9894b3548)