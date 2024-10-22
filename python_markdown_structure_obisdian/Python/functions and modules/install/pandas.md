___
[[modules]]
#pip 
___

### How to pandas

```python
import pandas as pd
```

### Creating pandas data frame objects

From a #dictionary
```python
# from Dictionary - KEY = Column name, Value = Series

dict = {

    'ID': ['001', '002', '003', '004', '005'],

    'Dupe': ['Alex', 'Bianca', 'Rony', 'Sam', 'Nico'],

    'Age': f'{1} day',

    '': np.array([1, 1, 2, 4, 4])

}

# create the pandas dataframe

dframe = pd.DataFrame(dict)
```

```python
# view first/last 5 (default) entries of dataframe

dframe.head()

dframe.tail()
```

From a #list of #dictionary 
```python
# from LIST of DICTs: 1 Dict = 1 dataset (row)

list_to_dframe = [

    {'ID': '001', 'Dupe': 'Alex', 'Age': 1, 'Job': 'Digger', 'Skill-level': 3},

    {'ID': '002', 'Dupe': 'Bianca', 'Age': 1},

    {'ID': '003', 'Dupe': 'Rony', 'Age': 1},

    {'ID': '004', 'Dupe': 'Sam', 'Age': 1},

    {'ID': '005', 'Dupe': 'Nico', 'Age': 1},

]

  

dframe = pd.DataFrame(list_to_dframe)

dframe
```

From #list of lists
```python
# from LIST of Lists - without indicies for column names

list_to_dframe = [

    ['001', 'Alex', 1],

    ['001', 'Binca', 1],

    ['001', 'Rony', 1],

]

  

dframe = pd.DataFrame(list_to_dframe)

dframe
```

```python
# Add a cheeky column

dframe['handy1'] = None
```

### Create data frame from .csv file

```python
dataframe = pd.read_csv('my_data.csv')  # 'C:/Users/Administrator/wbs_python/M5/tag_3/data/my_data.csv'

  

# alternatively

# df = pd.read_csv('my_data.csv', delimiter= ',')

# df1 = pd.read_csv('my_data.csv', delimiter='/t')

  

# Determine index by name

df = pd.read_csv('my_data.csv', index_col='Order ID')

# or index with index

df1 = pd.read_csv('my_data.csv', index_col= 0)
```

Save that data frame
```python
df.to_csv('output_no_index.csv', index= False, sep= ';')
```

### Column names & indexing

```python
dframe = pd.DataFrame(list_to_dframe, columns=['ID', 'Dupe', 'Age'])

dframe

  

#   ID  Dupe    Age

# 0 001 Alex    1

# 1 001 Binca   1

# 2 001 Rony    1

# replace the auto-index

dframeID = dframe.set_index('ID')

dframeID
```

Indexing column names from read .csv file
```python
df = pd.read_csv('C:/Users/Administrator/wbs_python/M5/tag_3/data/my_data.csv', names= ['A','B','C'])

  

# if you are mad, make a row the header even ...

df = pd.read_csv('C:/Users/Administrator/wbs_python/M5/tag_3/data/my_data.csv', header= 42)

df.head()
```

### Dataframe information

```python
df.head()# 5 top records

df.tail()# 5 last records

  

# shape (row_count, Column_count)

df.shape # (186850, 6)

# count of rows

df.shape[0] # 186850

# count of Columns

df.shape[1] # 6

# size: Count of all items

df.size # 186850 * 6
```

```python
# random entry (rows)

df.sample() # show one random row

df.sample(5) # show 5 random rows
```

```python
# Describe the dataset - lists counts, unique values and most frequent for each series

df.describe()
```

```python
# show only one column

df['Product']

df['Price Each']

  

# Alternatively

df.Product

  

# show several columns

df[['Product','Price Each' ]]
```

### Loop over dataframe contents

```python
# Loop over columns

for column_name in df:

    print(column_name)
```

```python
# Loop over rows

for row in df.iterrows():

    print(row)
```

```python
for index , row_data  in df.iterrows():

    print(index)

    print('+'*20)

    print(row_data)

    print ('+'*20)

    print(row_data.values)

    print()
```

### Inspecting column data

```python
# Inspect unique values of series

df['Product'].unique()

len(df['Product'].unique())

  

# HERE

df['Product'].nunique()

  

# count

df['Product'].value_counts()

  

# checks

df['Product'].isnull()

df['Product'].isnull().sum()

  

df['Product'].is_unique # False

df['Order ID'].is_unique # False
```

```python
# Loop over a dataframe - across column names or rather KEYs

for column_name in dframe:

    print(column_name, ' -->', dframe[column_name].unique(), '\n')
```

### Filter data with loc & logicals

```python
# example data

data = {

    'id': [1, 2, 3, 4, 5],

    'name':['thomas', 'ingo', 'sara', 'julia', 'lena'],

    }

  

# create DataFrame

df = pd.DataFrame(data)

# gives a series of True/False for each row

bool_thomas = df['name'] == 'thomas'

print(bool_thomas)

  

# print the rows where condition is met

# df[df['name'] == 'thomas']    # short version

thomas = df[bool_thomas]

print(thomas)
```

### Group and or aggregate data

```python
participants = [

    (10,'thomas',40,'Berlin',77),

    (11,'Ingo',40,'Berlin',80),

    (12,'Sara',40,'Berlin',90),

    (13,'Lena',30,'Frankfurt',70),

    (14,'Julia',30,'Berlin',77),

    (15,'Frank',20,'Stuttgart',78),

    (16,'Matthias',20,'Aachen',77),

    (17,'Ali',40,'Aachen',90),

    (18,'timo',40,'Stuttgart',77),

    (19,'Steffi',40,'Stuttgart',77),

]

  

# create a DataFrame

df = pd.DataFrame(participants, columns = ['ID','name','age','city','score'])

  

# set the index

df.set_index('ID', inplace = True)

df
```

```python
# create groups based columns

groups = df.groupby('city')

  

groups.size()

  

# Loop over the groups

for group_name, data in groups:

    print('Group Name: ',group_name)

    print('Group Data: ')

    print(data, '\n')
```

```python
# Aggregate function

  

# get the count of the rows of each group

groups.size()

  

# mean, max, min, sum

mean_values = groups.mean(numeric_only = True)

mean_values

  

# apply different Aggregate Function for different columns

result = groups.agg(

    {

        'age':'mean',

        'score':'sum'

    }

)

  

# apply different aggregate Functions for a column

result2 = groups['age'].agg( ['sum','mean','max','min'])

  

result3 = groups[['age', 'score']].agg( ['sum','mean','max','min'])
```

### Concatenate/merge/join dataframes

```python
# example data

data1 = {

    'id':[1, 2],

    'name':['frodo', 'sam'],

    'locale': 'Mordor',

}

data2 = {

    'id':[3, 4],

    'name':['gandalf', 'pippin'],

    'locale': 'Gondor',

}

data3 = {

    'id':[5, 6, 7],

    'game':['legolas', 'aragorn', 'gimli'],

    'locale': 'Gondor',

}

  

df1 = pd.DataFrame(data1)

df2 = pd.DataFrame(data2)

df3 = pd.DataFrame(data3)

# concatenate vertically/'adding rows' (axis = 0)

df_all = pd.concat([df1,df2,df3])

#df_all = pd.concat([df1,df2,df3], axis= 0)

  

df_all

# concatenate horizontally/ 'adding columns'(axis = 1)

df_all = pd.concat([df1,df2,df3], axis= 1)

df_all
```

```python
cities ={

    'city_code':['MDD','MT','ER'],

    'city_names':['Mordor am MtDoom', 'Minas Tirith', 'Erodas']

}

  

fellows = {

    'id':[1,2,3,4],

    'name':['Frodo','Gandalf','Theoden','Smeagol'],

    'city_code':['MDD','MT','ER','PF']

}

  

df_cities = pd.DataFrame(cities)

df_fellows= pd.DataFrame(fellows)
```

```python
# Inner Join on a common column name

# Includes (inner) parts of the second dataframe that are within the first

city_fellows = pd.merge(df_cities, df_fellows, how='inner', on = 'city_code')

  

# right Join based on the input frames

merged_df = pd.merge(df_cities, df_fellows, how='right', on = 'city_code')

  

# left Join

merged_df = pd.merge(df_cities, df_fellows, how='left', on = 'city_code')

print(merged_df)
```

```python
cities ={

    'city_code':['FFM','AA','BO','STD'],

    'city_names':['Frankfurt am Main', 'Aachen', 'Bonn','Stuttgart']

}

  

data_emp = {

    'id':[1,2,3,4],

    'name':['Thomas','Ingo','Sara','Maria'],

    'emp_code':['FFM','AA','BO','MU']

}

  

df_cities = pd.DataFrame(cities)

df_emp= pd.DataFrame(data_emp)

  

# Inner Join on different (somehow matching) columns

merged_df = pd.merge(df_cities, df_emp, how='inner', left_on = 'city_code', right_on = 'emp_code')

  

# Alternatively

df_emp.merge(df_cities, how = 'right', left_on = 'emp_code', right_on = 'city_code')
```

### Transform data

```python
# example data, upon creation datatypes are string (object)

data = {

    'ID': ['1','2'],

    'name':['thomas','Ingo'],

    'price':['12.2','13.3']

}

df = pd.DataFrame(data)

# df.info()

  

df.dtypes
```

```python
# change a datatype

df['ID'] = df['ID'].astype(int) # float etc.

df.dtypes
```

```python
df['ID'] = pd.to_numeric(df['ID'])          # recognizes as int

df['price'] = pd.to_numeric(df['price'])    # recognize as float

df.dtypes
```

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

```python
# Drop a Column

new_df = df.drop(columns = ['id1'])

  

df1 = pd.DataFrame(data)

df1.drop(columns = ['id1'], inplace= True) # df1 = df1.drop(columns = ['id1'])

  

# Drop several columns

new_df_2 = df.drop(columns= ['id','id1'])
```

```python
# Drop NaN (NULL) values - default with  axis = 'rows', how = any

df.dropna()

df.dropna(axis = 0 , how= 'any')    # drops row when any NaN value is in that row

df.dropna(axis = 0 , how= 'all')    # drops when all are NaN values in that row
```

```python
# Drop applied to a subset of the dataframe

# drop with subset

df.dropna(axis = 0 , how= 'all', subset=['name'])

df.dropna(axis = 0 , how= 'all', subset=['name', 'id1'])
```

```python
# fill the NaN entries with a specific value/string

df2 = df.fillna(0)
```

```python
# Fill NaN values differently for each column

df3 = df.fillna(

    {

        'name': 'Not Found',

        'score': 0

    }

)
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
# handy

df['name'].ffill(inplace=True)
```

```python
# Basic interpolate() function fills gaps in even steps based on the range (last valid --NaNs-> first valid entry)

df.score = df.score.interpolate()
```

### Duplicates

```python
# Find duplicates in a pandas dataframe

  

# get a bool Serie across the rows

df.duplicated() # True/False

  

# By default the first is not a duplicate and is kept when duplicates are dropped!

df.duplicated(keep= 'first')

df.duplicated(keep= 'last')

  

# get the duplicates rows

df[df.duplicated(keep= 'first')] # 4    5   Maria

df[df.duplicated(keep= 'last')] #  3    5   Maria
```

```python
# Drop duplicates

df.drop_duplicates()

# df.drop_duplicates(keep= 'last')

  

# Drop dupes within a subset

df.drop_duplicates(subset=['name', 'id'])
```

### Pandas String methods

```python
df['name'].str.title()

df['name'].str.upper()

df['name'].str.lower()

df['name'].str.capitalize()

df['name'].str.strip()

df['name'].str.strip().str.capitalize()
```

```python
# startwith()

df.name.str.startswith('t') # case sensitiv

df.loc[df.name.str.startswith('t')]

df[df.name.str.startswith('t')]

  
  

df[df.name.str.startswith('T')]

df[df.name.str.startswith(('t','T'))]
```

```python
# replace

df.name.str.replace(' ','_')

df.name.str.replace('t','x') # case sensitiv

  

# split

df.name.str.split()

df.name.str.split(expand = True)

  

# contains

df[df.name.str.contains('t')]

df[df.name.str.contains('t|T')]

  

# len()

df.name.str.len()

df[df.name.str.len() > 10]
```

### Changing/accessing content with apply/map 

```python
# example data

df = pd.DataFrame(

    {

        'number1':[10, 20],

        'number2':[100, 200],

    }

)

# create an example function

def increment(x):

    return x + 10

  
  

# Use the Function in the DataFrame

df2 = df.apply(increment)

print(df2)
```

```python
# 2. Example

df3 = df.apply(lambda x: x+20)

print(df3)
```

```python
# 3. Example

print(df)

print()

# default is the axis = 0, adding rows

df4 = df.apply(np.sum, axis = 0)

print(df4)

print()

# adding across columns

df5 = df.apply(np.sum, axis = 1)

print(df5)
```

```python
# Mapping functions

df = pd.DataFrame(

    {

        'name':['Frodo','Lutz','Sam'],

        'city':['hobbington','bree','bruchtal']

    }

)

  

df_upper = df.applymap(str.upper)

print(df_upper)
```

### Date/time in Pandas

```python
# example data

df = pd.DataFrame(

    {

        'date':['20/03/2023','10/03/2024','20/05/2025'],

        'score':[30,50,10]

    }

)

  

df.info()
```

```python
df['date'] = pd.to_datetime(df['date'])

df['date'] = pd.to_datetime(df['date'], dayfirst = True)

df['date'] = pd.to_datetime(df['date'], format = '%d/%m/%Y')
```

```python
df['year'] = df.date.dt.year

df['month'] = df.date.dt.month

df['day'] = df.date.dt.day

df['day_name'] = df.date.dt.day_name()

df['day of the Week'] = df.date.dt.day_of_week
```

```python
date_mapping ={

    0:'Montag',

    1:'Dienstag',

    2:'Mittwoch',

    3:'Donnerstag',

    4:'Freitag',

    5:'Samstag',

    6:'Sonntag',

}

  

# map the values of the column day_name

df['day_name_DE'] = df['date'].dt.day_of_week.map(date_mapping)

df['day_name_DE1'] = df['day of the Week'].map(date_mapping)
```