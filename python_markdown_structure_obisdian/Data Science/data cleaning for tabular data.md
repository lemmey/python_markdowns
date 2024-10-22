___
[[pandas]]
[[data exploration]]
#project 
#NaN 
#Null
___
## Data cleaning with pandas

Good practice:

```python
original_df = pd.read_csv('my_data.csv')

cleaned_df = original_df.copy()

# Like this, I can compare both throughout the process
```

Note that it is possible for a dataset (row) to have only partial faulty data. So two datasets might not be a complete duplicate or only consist out of missing values. Use subsets or try `.any()` method to extract faulty data.

```python
# Get column information

for col in dataframe:

    print(f'\nAll unique values for series {col}:\n{dataframe[col].unique()}')

    print(f'\nNo duplicates in the series {col}:\n{dataframe[col].is_unique}')

    print(f'\nUnique value counts of series {col}:\n{dataframe[col].value_counts()}')

    print(f'\nIs Null for each entry in series {col}:\n{dataframe[col].isnull()}')
```
___
### Dropping data

Rows:
```python
# Note: by default, drops rows unless axis parameter is set to 1

# delete a row

df.drop(index = 1)

#delete several rows

df.drop(index = [0,1,2])

df.drop([0,1,2])
  

df.drop(index = [30], errors= 'ignore') # no error

  

# delete an interval of indexes

  
df.drop(df.index[0:4])
  

df.drop(df.index[0:6:2])
```

Columns:
```python
# Drop a Column

new_df = df.drop(columns = ['id1'])
  

df1 = pd.DataFrame(data)

df1.drop(columns = ['id1'], inplace= True) # df1 = df1.drop(columns = ['id1'])


# Drop several columns

new_df_2 = df.drop(columns= ['id','id1'])
```
### Dropping duplicates

```python
# Find duplicates in a pandas dataframe

# get a bool Serie across the rows

df.duplicated() # True/False


# By default, the first (original) is not marked as duplicate 
# and is kept when duplicates are dropped!

df.duplicated(keep= 'first')

df.duplicated(keep= 'last')

  
# get the duplicates rows

df[df.duplicated(keep= 'first')] # 4    5   Maria

df[df.duplicated(keep= 'last')] #  3    5   Maria

# Drop duplicates

df.drop_duplicates()

# df.drop_duplicates(keep= 'last')

  

# Drop dupes within a subset

df.drop_duplicates(subset=['name', 'id'])
```

If you want to delete all datasets that were part of a duplicate compilation
```python
df.drop_duplicates(keep=False, inplace=True)
```
___
### Cleaning string data

Cleanse non alphabetic characters with #RegEx
```python
# What faulty characters are there in my subset

# Therefore substract all alphabetic characters as regex expression '[]'
# for all characters a-z, A-Z (here we could also include numbers 0-9) AND the 'space' character
# replace with empty space
df['User_Name'].str.replace('[a-zA-Z ]', '', regex=True).unique()

# Strip unique extracted outside characters
df['User_Name'] = df['User_Name'].str.strip('all non alphabetics')

# Replace inbetween characters 
df['User_Name'] = df['User_Name'].str.replace('-', ' ')
```

### Dropping NaN/Null values

```python
# Count of all single missing values per series (column)
print(dataframe.isna().sum()

# Count of all single missing values
print(dataframe.isna().sum().sum())

# Quick series overview if Null-values exist

df_clean.isnull().any() # False? Great!
```

```python
# Drop NaN (Null) values - default with  axis = 'rows', how = any

df.dropna()

df.dropna(axis = 0 , how= 'any')    # drops row when any NaN value is in that row

df.dropna(axis = 0 , how= 'all')    # drops only when all in row are NaN values


# Drop applied to a subset of the dataframe

df.dropna(axis = 0 , how= 'all', subset=['name'])

df.dropna(axis = 0 , how= 'all', subset=['name', 'id1'])
```
___
### Fill in categorical & numerical data

```python
# fill the NaN entries with a specific value/string

df2 = df.fillna(0)
```

```python
# Fill missing values based on last/first to come valid value

# Forward fill NaN with the last valid entry from top to bottom

df_filled = df.fillna(method='ffill')

  

df_filled = df.fillna(method='ffill', limit = 2)

  

# Backward fill NaNs

df6 = df.fillna(method='bfill')

  

df7 = df.fillna(method='bfill', limit = 1)
```

```python
# Basic interpolate() function fills gaps in even steps based on the range 
# (last valid -- NaNs (interpolated) -> first valid entry)
# the interpolate method can take lots of arguments, from linear to polynomial

df.score = df.score.interpolate()
```

```python
# handy

df['name'].ffill(inplace=True)
```