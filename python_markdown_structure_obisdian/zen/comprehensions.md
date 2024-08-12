___
[[list]]
[[dictionary]]
[[set]]
[[if...else statements]]
#ZEN
___
List Comprehensions (Listen-Abstraktion). Comprehensions komprimieren Code auf eine Zeile, sind optional, generieren aber i.d.R. kürzeren Syntax. Comprehensions lassen sich auch auf Dictionaries und Sets anwenden.
## Some good comprehensions to know

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
categorical_even_odd = ['even' if value % 2 == 0 else 'odd' for value in range(10)]

# ['even', 'odd', 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even', 'odd']
```
### Bestimmte Strings in einer Liste filtern
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

### Dictionary comprehension
```python
pairs = [('elves', 3), ('dwarves', 7), ('men', 9)]

a_dict = {key:value for key, value in pairs}
# {'elves': 3, 'dwarves': 7, 'men': 9}
```
### Einzigartige Werte filtern mit Set comprehension
```python
various_nums = [100, 101, 99, 99, 101, 11000, 1011, 1011]

unique_nums = {num for num in various_nums}
# {99, 100, 101, 1011, 11000}
```

## Bonus: über Ziffern iterieren

```python
num = 123456 # eigentlich not iterable

digits = [int(digit) for digit in str(num)]

# Wenn wir die digits in string umwandeln und dann als integer in eine Liste packen ginge das schon!
```