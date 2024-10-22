___
[[List]]
[[Dictionary]]
[[Set]]
#condition 
#ZEN
___
List Comprehensions (Listen-Abstraktion) komprimieren Code auf wenige Zeilen, sind optional, generieren aber i.d.R. kürzeren Syntax. 

Comprehensions lassen sich auch auf Dictionaries und Sets anwenden.
## Some good comprehensions to know
___
### Fülle eine Liste mit Werten

```python
values = [value + 1 for value in range(10)]
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

################################

# This is e.g. well combined with the random module
from random import randint


def rand_even(_max: int):
	'''Returns a random even integer within a range'''
	x = randint(0,_max)
	if x % 2 == 0:
		return x

rand_even_nums = [rand_even(1000) for num in range(10)]

print(rand_even_nums)

############################# or even:
from random import sample


rand_even_nums = [num for num in sample(range(99), 10) if num % 2 == 0]

print(rand_even_nums) # e.g. [6, 728, 768, 638, 782, 66, 922]
```

```python
squares_100 = [x**2 for x in range(1, 101)]

# [1, 4, 9, 16 ..., 10000]
```

#bool
```python
categorical_even_odd = [
						'even' 
						if _ % 2 == 0 
						else 'odd' 
						for _ in range(1, 11)
						]

# ['even', 'odd', 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even', 'odd']
```
___
### Filter und Transform mit List comprehension

```python
mail_addresses = {
    'Josh': 'blabla@mail.com',
    'Sandra': 'mymail@expo.govt',
    'Linus': 'failedstate(a)home.xs',
}

  

checked_mail_addresses = [x for x in mail_addresses.values() if '@' in x]

  
print(checked_mail_addresses) # ['blabla@mail.com', 'mymail@expo.govt']
```

```python
USER_IDs = ['id2200', 'ID1100','iD0190','ID1900','ID290']

VALID_IDs = [
	id
	for id in USER_IDs
	if len(id) == 6
	if id[-2:] == '00'
]

print(VALID_IDs) # ['id2200', 'ID1100', 'ID1900']
```

Mehrere Werte filtern:
```python
movies = [('Citizen Kane', 1941), ('Spirited Away', 2001), ('Gattaca', 1997),
          ('No Country for Old Men', 2007),
              ('The Lord of the Rings: The Fellowship of the Ring', 2001),
              ('The Royal Tenenbaums', 2001),]


pre2k = [title for (title, year) in movies if year < 2000]

print(pre2k) # ['Citizen Kane', 'Gattaca']
```

Elemente aus #iterable geordnet zusammenfügen: (Cartesian Product)
```python
A = [1, 3, 5, 7, 9]

B = [2, 4, 6, 8, 10]
  

cartesian_product = [(a,b) for a in A for b in B if a+b >= 15]

  
print(cartesian_product) # [(5, 10), (7, 8), (7, 10), (9, 6), (9, 8), (9, 10)]
```
___
### String comprehension (not really)

```python
a_string = 'SameSameButDifferent'

the_same_string = ''.join([s if s.islower() else ' ' + s for s in a_string])[1:]

print(the_same_string) # Same Same But Different
```
___
### Dictionary comprehension

```python
pairs = [('elves', 3), ('dwarves', 7), ('men', 9)]

a_dict = {key:value for key, value in pairs}
# {'elves': 3, 'dwarves': 7, 'men': 9}
```
___
### Tuple comprehensions

```python
data1 = (1, 2)

data2 = (3, 4)

[print(sum(x)) for x in [data1 + data2]]  # 10

[print(sum(x)) for x in [(1, 2, 3, 4)]]   # 10

[print(sum(x)) for x in [(1, 2), (3, 4), (5, 6)]]  
# 3 
# 7
# 11
```
___
### Mit Set comprehension einzigartige Werte filtern

```python
various_nums = [100, 101, 99, 99, 101, 11000, 1011, 1011]

unique_nums = {num for num in various_nums}
# {99, 100, 101, 1011, 11000}
```
___
### Bonus: über Ziffern iterieren

#pymagic
```python
num = 123456 # eigentlich not iterable

digits = [int(digit) for digit in str(num)]

# Wenn wir die digits in string umwandeln und dann als integer in eine Liste packen ginge das schon!
```

___
### Generator expression (comprehension)

Nicht zu verwechseln mit Tuple comprehensions.
```python
import itertools

import sys

  

# Creating an infinite object in a generator

all_squares = (x**2 for x in itertools.count(1))
# all_squares = [x**2 for x in itertools.count(1)] # infinite bites
  

print(type(all_squares)) # <class 'generator'>

print(sys.getsizeof(all_squares)) # 104 bites


# for x in all_squares:

#     print(x) # memory breaking loop

#     if x > 10_000:

#         all_squares.close()
```

