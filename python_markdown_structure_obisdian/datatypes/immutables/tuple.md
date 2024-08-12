___
[[datatypes]]
#immutable mutable
#iterable
#sequence 
___
Tuples sind ein sequentiellen Datentypen in Python. 
Die anderen sind list, dictionary, set und string.

	* 'List' - [ ordered & indexed and changeable ]
	
	* 'Dictionary' - { ordered (Py3.7), changeable, not indexed, 
	    no duplicates (as Key)! }
	
	* 'Tuple' - ( ordered & indexed but unchangeable )
	
	* 'Set' - unordered, mostly unchangeable and not indexed, 
	    no duplicates!, set('empty'), set_1 = {x, y}, set_2 = ([x, y])
	
		* 'Frozenset' - truly unchangeable set

___
Im Prinzip ähneln tuples einer unveränderlichen Liste (ohne `.append` oder `.pop`). 
Durch einen Tuple können Daten vor Veränderungen geschützt werden. Zum Beispiel als fester KEY für ein Dictionary - cool!

Tuple bestimmen:
```python
x = 1, 2    # Das ist ein Tuple mit zwei Elementen

x = (1, 2)  # Das auch. Die Klammern sind optional, es sei denn der Tuple ist leer

x = (1, ) # Tuple mit nur einem Element. (1) das wäre ein integer, () das wiederum ein tuple, verwirrend

# Die Umformung zum Datentyp: Tuple ist intuitiv

x = [1, 2, 3]

x_tuple = tuple(x)


x = "abc"

x_tuple = tuple(x)

# ('a', 'b', 'c') 
```

Klassisches Programmierproblem, das Vertauschen von Werten:
```python
a = 1

b = 2

# What works:
temp = a

a = b

b = temp

# In Pythonisch, mit tuple schreibweise
a, b = b, a   # Wowee
```

Tuples können ganz normal per Index angesprochen und auch gesliced werden:
```python
coordinates = (1, 2, 3)

# This works:
x = coordinates[0]

y = coordinates[1]

z = coordinates[2]

# Pythonisch (entpacken)
x, y, z = coordinates   # Hierbei muss nur die Reihenfolge beachtet werden
```

Bei längeren Sequenzen kann mit dem unpacking operator #decompose `*` eine Spanne von Werten bestimmt werden die einer Variablen zugeteilt werden sollen. In einer Anwendung könnte so z.B. User Input aufgeteilt - (String-Methode .split) und zugeteilt werden.
```python
gefährten = ("Frodo", "Sam", "Merry", "Pippin", "Aragorn", "Gandalf")

*hobbits, menschen, zauberer = gefährten

print(hobbits) # ['Frodo', 'Sam', 'Merry', 'Pippin']
```