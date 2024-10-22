___
[[functions]]
#built-in 
#lambda 
___

Bei default sind beide Funktionen auf ausschließlich alphabetische oder numerische Sortierung eingestellt. Komplexere Sortierungen lassen sich mit dem key-Argument steuern, z.B. nach `len()`.
___
#### `.sort()`
Das ist eine #in-place Sortierung, daher möglicherweise speichereffizient. Syntax:
`list.sort(reverse=True|False, key=myFunc)`
```python

my_sorted_list.sort(reverse=True)  

print(my_sorted_list)

  
# objektgebunden und OHNE return!

# rabbit = rabbits.sort()  # None
```
___
#### `sorted()`
Eine generelle built-in function mit mehreren Anwendungsbereichen, die das ursprüngliche Objekt nicht verändert.  Syntax:
`sorted(iterable, key=key, reverse=reverse)`
```python 
my_list = ['z', 'dd', 'a']

  
my_sorted_list = sorted(my_list)

  
print(my_sorted_list) # ['a', 'dd', 'z']

# Sorted returns eine neue Liste!

# Kann nur exklusiv alphabetisch ODER numerisch sortieren!
```

#### String sortieren? Ja!
String is an #iterable , note however that the a resulting list contains special characters and capital characters first.
```python
raw_string = 'Some string'

new_string = sorted(raw_string)

print(new_string)

# [' ', 'S', 'e', 'g', 'i', 'm', 'n', 'o', 'r', 's', 't']
```
#### Tuple sortieren? Ja!
Note that a `sorted()` tuple returns a list object.
```python
my_data = ('bb', 'ab', 'ba', 'aa', 'ia') # immutable tuple

new_data = sorted(my_data)

print(new_data)
# ['aa', 'ab', 'ba', 'bb', 'ia']         # Result is a list!
# works with numerical data
```
#### Sortierung mit `key`-argument

```python
# format := (name, radius, density, distance to Sun)
planets = [
		   ('Mercury', 2440, 5.43, 0.395),
		   ('Venus', 6052, 5.24, 0.723),
		   ('Earth', 6378, 5.52, 1.000),
		   ('Mars', 3396, 3.93, 1.530),
		   ('Jupiter', 71492, 1.33, 5.210),
		   ('Saturn', 60268, 0.69, 9.551),
]

name = lambda planet: planet[0] 
size = lambda planet: planet[1]

# In-place sort with name and .sort()  

planets.sort(key=name)

print(planets)

# New sorted() list by size

planets_size = sorted(planets, key=size)

print(planets_size)
```