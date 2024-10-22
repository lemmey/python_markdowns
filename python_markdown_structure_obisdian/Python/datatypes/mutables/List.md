___
[[datatypes]]
#mutable
#iterable
#sequence
___
Listen sind einer wichtigsten sequentiellen Datentypen in Python. Die anderen sind tuple, dictionaries, sets und strings.

	* 'List' - [ ordered & indexed and changeable ]
	
	* 'Dictionary' - { ordered (Py3.7), changeable, not indexed, 
	    no duplicates (as Key)! }
	
	* 'Tuple' - ( ordered & indexed but unchangeable )
	
	* 'Set' - unordered, mostly unchangeable and not indexed, 
	    no duplicates!, set('empty'), set_1 = {x, y}, set_2 = ([x, y])
	
		* 'Frozenset' - truly unchangeable set

Der #datatype von Listeninhalten ist beliebig. Eine Liste kann Duplikate enthalten, da die Elemente indiziert sind.

Note: Durch Erhaltung der #memory-address sind Listen äußerst Speicher effektiv, besonders wenn die Anzahl der Elemente steigt.

## Listen manipulieren

#### Listen erweitern

```python
community = ["Britta", "Abed", "Troy"]
print(id(community)) # 2583997076288

community.append("Annie")
print(community)
# ['Britta', 'Abed', 'Troy', 'Annie']
print(id(community)) # 2583997076288

#################################### also:

community.insert(3, "Annie")
# Hint: instead of index use length of list to append always at the end

####################################

community = ["Britta", "Abed", "Troy", "Annie"] # id 2583997076288
more_community = ["Shirley", "Pierce", "Jeff"]

community = community + more_community # id 2218909559040
# ["Britta", "Abed", "Troy", "Annie", "Shirley", "Pierce", "Jeff"]

#################################### also:

community.extend(more_community)
```

#decompose
```python
community = ["Britta", "Abed", "Troy", "Annie"]
more_community = ["Shirley", "Pierce", "Jeff"]

community = [*community, *more_community]
# ['Britta', 'Abed', 'Troy', 'Annie', 'Shirley', 'Pierce', 'Jeff']
```
___
#### Listen verkleinern

```python
community.remove("Pierce")

# OR

del community[5] # an Index 5
```
___
### Listen Sortierung

Mit `list.sort()`:

```python
community = ["Britta", "Abed", "Troy"]
community.sort() # reverse=False, key=None

print(community)
# ['Abed', 'Britta', 'Troy']

############################

# A powerful arguement of the sort()-function is the key parameter
# The key parameter can take another function
community = ["Britta Perry", "Abed Nadir", "Troy Barnes"]
community.sort(key=lambda full_name: full_name.split()[-1])

print(community)
# ['Troy Barnes', 'Abed Nadir', 'Britta Perry']
```

Mit` sorted(list)`:

```python
community = ["Britta", "Abed", "Troy"]

print(sorted(community))
# ['Abed', 'Britta', 'Troy']
```
___
### Andere Listen Methoden

```python
community = ["Britta", "Abed", "Troy"]
print(community.index("Abed")) # 1

##################################

print(community.reverse())
# ["Troy", "Abed", "Britta"]
```
### List `index()`

Note that only the index position of the first occurrence in the list is returned!

```python
# List index method - what is the index position of value x

my_list = [0.05, 0.10, 0.00]

x = 0

x_pos = my_list.index(x)

print(x_pos) # 2
```

### Listen kopieren

```python
# NOT a isolated copy
fruits = ["apple", "cherry", "banana"]

fruits_new = fruits  

# Like this, with lists we only copy the memory address

print(fruits, "id:", id(fruits))          # 2371000161088
print(fruits_neu, "id:", id(fruits_neu))  # 2371000161088

# The name fruits_new cursors to the same physical memory location, like this when we manipulate one of the lists we do so for both

fruits_neu.append("Melon")
print(fruits)  # ['apple', 'cherry', 'banana', 'Melon']
```

```python
# real flat copies
fruits = ["apple", "cherry", "banana"]
fruits_fresh = fruits[:]

print(id(fruits)) # 1420849961216
print(id(fruits_fresh)) # 1420850132096

# better choice ...
fruits_fresh = fruits.copy()
```

```python
# deep copies
from copy import deepcopy

fruits = ["apple", "cherry", ["banana"]]
fruits_fresh = fruits[:]

# Now, if we append the nested list normally it still appends related lists
fruits[2].append("dragonfruit")
print(fruits_fresh) # ['apple', 'cherry', ['banana', 'dragonfruit']]

# To be safe user deepcopy() as:
fruits_fresh = deepcopy(fruits)
```
___
### Mit Listen-Elementen arbeiten

```python
UI = "Merry"

hobbitse = ["Frodo", "Merry", "Pippin", "Sam"]

time = [320, 120, 150, 305]

# enumerate() erstellt einen Tuple aus zwei ELementen, fuer jedes Element in 'hobbitse'. Dadurch koennen beide Werte (num, str) angepeilt werden (index, hobbit). Da die Indexe standardisiert sind (0,1,etc) und wir in den gleichen Schritten loopen ist der Index in hobbitse, time und dem tuple index kongruent.  

for index, hobbit in enumerate(hobbitse):
	# (0, 'Frodo')
	# (1, 'Merry')
	# (2, 'Pippin')
	# (3, 'Sam')
    if hobbit == UI:

        print(f"Screentime {hobbit}: {time[index]}")

# Screentime Merry: 120
```