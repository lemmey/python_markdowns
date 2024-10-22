___
[[datatypes]]
#mutable
#iterable
#sequence
___
Dictionaries sind einer wichtigsten sequentiellen Datentypen in Python. Die anderen sind list, tuple, sets und strings.

	* 'List' - [ ordered & indexed and changeable ]
	
	* 'Dictionary' - { ordered (Py3.7), changeable, not indexed, 
	    no duplicates (as Key)! }
	
	* 'Tuple' - ( ordered & indexed but unchangeable )
	
	* 'Set' - unordered, mostly unchangeable and not indexed, 
	    no duplicates!, set('empty'), set_1 = {x, y}, set_2 = ([x, y])
	
		* 'Frozenset' - truly unchangeable set

Der offensichtlichste Unterschied zu den anderen Datentypen ist der Aufbau durch `Key-Value` Paare. Das heißt, jedes Element in dem Dictionary besteht aus zwei "Werten". In der Regel werden aber die KEYs angesprochen, wodurch die zugeordneten Values ausgegeben werden.

Tipp: Für schönere prints in der Konsole:
```python
from pprint import pprint

dictionary = {'key':'value'}
```

Wichtig: Duplizierte Keys werden durch den letzten Wert überschrieben:
```python
# Beispiel
dict = {

  "Menschen": 9,
  "Zwerge": 7,
  "Elben": 3,
  "Sauron": 1,
  "Sauron": 0

}

# {'Menschen': 9, 'Zwerge': 7, 'Elben': 3, 'Sauron': 0}
```

```python
# Dictionary-Literal
my_dict = {
  "Frodo": 1,
  "Sauron": 0,
}

# Mit Dictionary-Konstruktor ein Dicitonary updaten  
your_dict = {}

your_dict['Frodo'] = 1
your_dict['Sauron'] = 0

# {'Frodo': 1, 'Sauron': 0}
```

Achtung: In den `KEYs` können  nur unveränderliche Datentypen stehen inklusive Tuples! In den `Values` können allerdings auch veränderliche stehen, das macht Dictionaries zu einem echt starken Datentyp:
```python
hobbits = {

  "Info": {

    "Names": ["Frodo", "Merry", "Pippin", "Sam"],  # KEY= Names: Value = List

    "Ringtraeger": {  # KEY= Names: Value = Dict

      "Frodo": True,
      "Merry": False,
      "Pippin": False,
      "Sam": True

    }
  }
}
```
___
### Dictionary Inhalte (Werte) abrufen

Keys sind eindeutig, die ist auch der einzige Nachteil: der Key muss bekannt sein um auf einen Wert zugreifen zu können. (Ansonsten: #KeyError)
```python
if "Ringtraeger" in hobbits["Info"]:

    print(hobbits["Info"]["Ringtraeger"])

# {'Frodo': True, 'Merry': False, 'Pippin': False, 'Sam': True}
```

Mit `.get()`
```python
hobbitse = {

  "Team Mordor": ["Frodo", "Sam"],
  "Team Minas Tirith": ["Merry", "Pippin"],

}

print(hobbitse.get("Team Mordor")) # ['Frodo', 'Sam']
```
___
### Iteration durch ein Dictionary (keys & values)

Bei Iteration eines Dictionary wird in der Regel zuerst KEY angesprochen und ausgegeben:
```python
hobbitse = {'Rohan':'Merry', 'Gondor':'Pippin', 'Mordor':['Frodo','Sam']}

for key in hobbitse:

	print(key, end=' ') # Rohan Gondor Mordor
	
    print(hobbitse[key], end=' ') # Merry Pippin ['Frodo', 'Sam']
```

Um KEYs & Values gleichzeitig auszugeben .items():
```python
print(hobbitse.items())
# dict_items([('Rohan', 'Merry'), ('Gondor', 'Pippin'), ('Mordor', ['Frodo', 'Sam'])])

# Note: .items(), .keys(), .items() returns an iterable view object

#########

for key_value_tuple in hobbitse.items():
	print(key_value_tuple)

# ('Rohan', 'Merry')
# ('Gondor', 'Pippin')
# ('Mordor', ['Frodo', 'Sam'])

##############################

for key_value_tuple in hobbitse.items():
	print(*key_value_tuple)

# or

for key, value in hobbitse.items():
	print(key, value)
```

`.keys()` -> *view object* 
```python
print(hobbitse.keys()) # dict_keys(['Rohan', 'Gondor', 'Mordor'])
```

`.values()` -> *view object*
```python
print(hobbitse.values()) # dict_values(['Merry', 'Pippin', ['Frodo', 'Sam']])
```

Werte mit Iteration verändern:
```python
wizards = {'Gandalf':'good', 'Saruman': 'good', 'Sauron': 'evil'}

for name, ethos in wizards.items():

    if name == 'Saruman':

        wizards[name] = 'bad'

print(wizards) # {'Gandalf': 'good', 'Saruman': 'bad', 'Sauron': 'evil'}
```
___
### Dictionaries erweitern/verbinden/verkleinern

Erweitern:
```python
hobbitse = {"Team Minas Tirith": ["Merry", "Pippin"]}

hobbitse["Team Mordor"] = ["Frodo", "Sam"]

# {'Team Minas Tirith': ['Merry', 'Pippin'], 'Team Mordor': ['Frodo', 'Sam']}

#######################

hobbitse = {"Team Minas Tirith": ["Merry", "Pippin"]}

garstige_hobbits = {"Team Mordor": ["Frodo", "Sam"]}

hobbitse.update(garstige_hobbits)

# {'Team Minas Tirith': ['Merry', 'Pippin'], 'Team Mordor': ['Frodo', 'Sam']}

#######################

wizards = {
		   "Gandalf": 2000
		   }

hobbitse = {
			"Frodo": 33,
			"Sam": 34,
			}

# Since Py3.8: Like this, a new dicionary gets created

fellows = wizards | hobbitse  

print(fellows) #{'Gandalf': 2000, 'Frodo': 33, 'Sam': 34}
```

#decompose 
```python
wizards = {"Gandalf": 2000}
hobbitse = {
			"Frodo": 33,
			"Sam": 34,
			}

fellows = {**wizards, **hobbitse}
print(fellows)
# {'Gandalf': 2000, 'Frodo': 33, 'Sam': 34}
```

Verkleinern:
```python
wizards = {'Gandalf':'good', 'Saruman': 'good', 'Sauron': 'bad'}

for name in wizards.copy():

    if name == 'Sauron':

        del wizards[name]

# {'Gandalf': 'good', 'Saruman': 'good'}

#######################################

wizards.pop('Sauron') # pop removes specified key:value & returns the 'popped' value (not key), or a default value if the specified is not found in a second argument

print(wizards) # {'Gandalf': 'good', 'Saruman': 'good'}

################

wizards.popitem() # removes the last inserted item of the dictionary

```

