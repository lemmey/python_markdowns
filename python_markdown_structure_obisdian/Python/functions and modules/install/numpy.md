___
[[modules]]
#pip 
___

## How to

### NumPy arrays

By static list
```python
import numpy as np


array = np.array([55, 22, 11])

print(array)

# [55 22 11]

# <class 'numpy.ndarray'>

```

With range-object
```python
array = np.arange(0, 101, 10)

print(array)

# [  0  10  20  30  40  50  60  70  80  90 100]
```

Multidimensional arrays (matricies)
```python
mat = np.array([[55, 22, 11], [0, 0, 0]])   # double-brackets!

print(mat)

# [[55 22 11]

#  [ 0  0  0]]
```

### Generate array data

```python
from numpy import random
```

```python
# array with random content between 0 and 1

array_rnd = np.random.rand(5)

print(array_rnd)

  

# floats in range

array_rnd = np.random.uniform(1, 11, 5)

print(array_rnd)

# [2.78239759 4.57891287 2.26319308 4.64652633 3.73310195]
```

```python
# 1D

array_rnd = np.random.randint(1, 11, 5) # possible range + size, or sampled from range

print(array_rnd)

# [10  3  1  8  1]

  

#mD

array_rnd = np.random.randint(1, 11, (3,5))

print(array_rnd)

# [[ 2  5  8  8  4]

#  [ 1  2 10  1  6]

#  [ 7  6  4  7  1]]

  

array_rnd = np.random.randint(1, 11, (2,2,2))

print(array_rnd)

# [[[3 5]

#   [2 1]]

  

#  [[1 4]

#   [5 4]]]
```

```python
# Use round function for display of results

array_rnd.round(decimals=3)
```

'Sometimes to duplicate an example or run an algorithm remotely 
while creating the same output we need to randomize the same values

For that we generate a seed, which determines the values shuffled
in context to the script
```python
```

```python
# generate zeros

m_zeros = np.zeros((3,2,2))

print(m_zeros)

# [[[0. 0.]

#   [0. 0.]]

  

#  [[0. 0.]

#   [0. 0.]]

  

#  [[0. 0.]

#   [0. 0.]]]

  

m_ones = np.ones((3,2,2))

print(m_ones)

  

# generate a specific 'FillValue'

m_fillvalue = np.full((1,3,1), 0.69)

print(m_fillvalue)

# [[[0.69]

#   [0.69]

#   [0.69]]]
```

```python
# For ML

# Generate a diagonal line of 1s, eg. as arbitrary correlation

eye = np.eye(3)

print(eye)

  

eq_numbers = np.linspace(0,20,41)   # Von, bis, n values in gleichen Schritten!

print(eq_numbers)
```

### Reshape arrays

```python
array_high = np.array([[1, 2], [3, 4], [5, 6]])

print(array_high.shape)  # (3,2) = shape(rows,cols)

# Reshape, has to maintain product of shape dimensions

array_wide = array_high.reshape(2,3)

# or flatten

array_flat = array_high.reshape(1,6)

# [[1 2 3 4 5 6]]
```

```python
# array_high = np.array([[1, 2], [3, 4], [5, 6]])

array_flatten = array_high.ravel()

print(array_flatten)

# [1 2 3 4 5 6]
```

```python
a = np.array(

    [

    [1,2,10],

    [3,4,11],

    [5,6,12],

    ]

    )

  

print(a)

# Mirrored on the diagonal

result = a.T

result
```

```python
array_A = np.array([

    [1,2],

    [3,4]

])

array_B = np.array([

    [10,20],

    [30,40]

])

# Vertical stacking, columns grow

m_vstack = np.vstack( (array_A, array_B) )

print(m_vstack)

# [[ 1  2]

#  [ 3  4]

#  [10 20]

#  [30 40]]

# Horizontal stacking, rows grow

m_hstack = np.hstack( (array_A, array_B) )

print(m_hstack)

# [[ 1  2 10 20]

#  [ 3  4 30 40]]
```
### Array datatypes

```python
# define array content as (int)

array_int = np.array([[55, 22, 11], [0, 0, 0]], dtype=np.int32)

print(array_int)

# define as (float)

array_float = np.array([[55, 22, 11], [0, 0, 0]], dtype=np.float64)

print(array_float)

# [[55. 22. 11.]

#  [ 0.  0.  0.]]
```

### Array Information

```python
array = np.array([[1,2], [1,2], [3,4]])

print(array, type(array))

  

print(array.ndim) # 1 vector with 8 elements

print(array.shape) # (8,)  

print(array.size) # 8 elements

print(array.dtype)

print(array.itemsize)
```
### Array operations

```python
a = np.arange(10) # 0---9

b = np.arange(1,11) # 1---10

  

print(a + b)

print(a - b)

print(a * b)

print(a / b)

  

print(a+1)

  

# Apply square root function

print(np.sqrt(a))
```

### Array Functions

```python
# aggregate Functions

a = np.arange(1, 11)

c = np.array( [ [1 , 2 ],[3, 4 ],[5,6]])

  

print(a.sum())

print(a.min())

print(a.max())

print(a.mean())

  

# Advanced Sum

"""

axis = 0 -> columns

axis = 1 -> rows

"""

print(c)

print(c.sum())  # sum all contents across all dimensions

print(c.sum(axis = 0)) # column-wise sum  ! ! !

print(c.sum(axis = 1 )) # row-wise sum  ! ! !

  

# sorting in place

a = np.array([ 5, 60,9, 0,56, 700,4])

a.sort()

  

# # rounding

a = np.array ( [5, 12.98, 56.9876, 3.988])

print(a.round(decimals = 2))
```
### Save NumPy arrays as .npy

```python
big_rnd_array = np.random.uniform(1, 11, (10,2,2))

# print(big_rnd_array)

np.save('big_rnd_array', big_rnd_array)

  

array_loaded290524 = np.load('big_rnd_array.npy')

print(array_loaded290524.round(decimals=3))
```

### Array sclicing, subsetting & indexing

```python
# Start, stop, step

array = np.array([0, 1, 2, 3, 4, 5])

print(array[::])    # select all
```

```python
matrix1 = np.random.rand(3, 2)

print('Matrix 1\n', matrix1.round(2))

print('M1 Wert Aus 3. Reihe, 2. Spalte\n', matrix1[2,1].round(2)) # wie [2][1]

  

print('M1 rows 1-3 & col. 2\n', matrix1[0:3, 1].round(2))  # selecting rows 1 to 3 at column 2 in a new list

  

print('Größer als 0.5\n', matrix1[matrix1 > .5].round(2))    # selecting contents greater than 0.5

  

# Boolscher Vergleich

matrix2 = np.random.rand(3, 2)

print(matrix1 > matrix2)

  

# Matrix umkehren

print(matrix1[::-1].round(2))
```

```python
# Slice off a new array where() conditions are met

a = np.array([1,2,3,4,5])

b = np.array([1,3,2,4,5])

  

# the position where a == b

np.where(a == b) # index: [0, 3, 4]

c = a[np.where(a == b) ]

print(c)                # ([1, 4, 5]

  

# the position where a > b

np.where(a > b) # index: 2

d = a[np.where(a > b) ]

print(d)                # [3]
```

```python
# Initial entity to draw random samples out

array = np.array([0, 1, 2, 3, 4, 5])

  

single_sampled = np.random.choice(array, size=(1))

print(single_sampled)

  

# Draw samples into a matrix

m_sampled = np.random.choice(array, size=(3,3), replace=True)

print(m_sampled)    # with values of array, and replacement!

# [[3 5 4]

#  [2 1 2]

#  [4 0 5]]
```

### Copy NumPy arrays flat & deep

```python
array_og = np.array([0, 1, 2, 3, 4, 5])

array_copy = array_og   # der containers bleibt so derselbe (keine richtige Kopie)

  

# change original array --> both change, due to same memory address

array_og[0] = 100  

print('Array a:', array_og, 'Array B:', array_copy)

  

# --> Deep copy

array_deepcopy = array_og.copy()    # different IDs
```