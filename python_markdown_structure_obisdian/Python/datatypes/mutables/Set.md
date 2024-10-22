___
[[datatypes]]
#mutable
#iterable 
___
Sets sind ein ungeordneter, nicht-sequentieller Datentypen in Python:

	* 'List' - [ ordered & indexed and changeable ]
	
	* 'Dictionary' - { ordered (Py3.7), changeable, not indexed, 
	    no duplicates (as Key)! }
	
	* 'Tuple' - ( ordered & indexed but unchangeable )
	
	* 'Set' - unordered, *mostly unchangeable and not indexed, 
	    no duplicates!, set('empty'), set_1 = {x, y}, set_2 = ([x, y])
	
		* 'Frozenset' - truly unchangeable set, no *adding or removing items

```python
x = set()   # empty set

x = {1, 2, "3", 4.0, (5,)} # a set-literal

x = ([1, 2, "3", 4.0, (5,)]) # set-constructor
```

Der Datentyp Set erzeugt immer eine eindeutige Menge. Dadurch werden doppelte Werte automatisch gelöscht. Das gilt auch für True und 1, in Sets gelten dies als Duplikat - genauso wie False und 0. Dies kann genutzt werden um zum Beispiel: Duplikate in Datensets zu verhindern.

```python
s1 = {1, 2, 3, 4, 5, 1, 2, 3}

print(s1) # {1, 2, 3, 4, 5}
```

Note: Die Reihenfolge der Elemente in einem Set ist willkürlich. Eine Operation auf ein Set auszuführen, die nicht die Gesamtheit des Inhalts betrifft, ist demnach auch willkürlich. Beim Zugriff auf Sets wird nur der Hashwert geprüft, daher ist die Zugriffszeit auch bei sehr großen Sets immer gleich - cool!

### Sets erweitern
Ein Set kann mit mehreren verschiedenen Datensätzen gleichzeitig erweitert werden und nimmt jeden Datentyp auf:
```python
a = set()

b = {55, 66, 77}

c = [111]

d = "abc"

a.update(b, c, d) # .add() works for single values

print(a) # {66, 'b', 'c', 77, 111, 'a', 55}
# unordered
print(a) # {'c', 66, 77, 111, 55, 'a', 'b'}

######## or when combining sets

set1: set[int] = {1, 2, 3, 4}

set2: set[int] = {4, 5, 6}


set0: set[int] = set1 | set2 # bam! pipe-combine

print(set0) # {1, 2, 3, 4, 5, 6}
```

### Sets verkleinern
```python
s1 = {1, 2, 3, 4, 5}

s1.remove(6) # KeyError

s1.discard(5) # {1, 2, 3, 4} - also no KeyError

#############

set1: set[int] = {1, 2, 3, 4}

set2: set[int] = {4, 5, 6}


set0: set[int] = set1 - set2 

print(set0) # {1, 2, 3}
```

Sets finden i.d.R. weniger Anwendung als Listen oder Dictionaries, wo sie sich aber hervorragend verwenden lassen sind Mengenoperationen. Die Mengen-Operatoren lassen zum Beispiel prüfen, ob eine Menge eine Untermenge/Obermenge einer anderen ist. 
```python

num_set1 = {10, 11, 12, 13, 15}

num_set2 = {14, 11, 12, 13, 14}

# Find values present in all sets
print(num_set1 & num_set2) # AND, Intersection/Schnittmenge

# {11, 12, 13}

print(num_set1 - num_set2) # DIFFERENCE (reihenfolgenspezifisch)

# {10, 15}

print(num_set1 | num_set2) # UNION. Gemeinsame Menge

# {10, 11, 12, 13, 14, 15}

print(num_set1 ^ num_set2) # Symmetric difference, alle Werte die exklusiv für beide Mengen gegenüber der jeweils anderen sind (eindeutige Elemente)

# {10, 14, 15}

```
### Anwendungsbeispiele

Duplikate verhindern:
```python
l1 = [0.1, 0.5, 0.99, 0.1, 0.5, 0.99]
list_no_dupes = list(set(l1)) # [0.1, 0.5, 0.99]
```

Prüfen ob Inhalte in einer Sequenz enthalten sind:
```python
names = ["bob", "trudy"]

students = ["bob", "trudy", "mallory"]

in_both = set(names).intersection(students)

print(in_both) # {'trudy', 'bob'}

######################## or

if set(names) <= set(students):

    print(f"{names} are already in {students}")

# ['bob', 'trudy'] are already in ['bob', 'trudy', 'mallory']
```

Eine Schnittmenge finden, Werte die in allen Sets enthalten sind:
```python
s1 = {1999, 2000, 2022, 1991}
s2 = {2002, 1991, 2022, 1998}
s3 = {1991, 2000, 2016, 2022}

si = s1.intersection(s2, s3) # {2022, 1991}
# or
print(s1 & s2 & s3) # {2022, 1991}
```