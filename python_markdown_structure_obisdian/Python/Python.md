___

___
# In Python *everything is an object* & Markdown is the new readme.txt\

## Python Virtual Environments (VEnv)
#venv

Code wird als generelle Empfehlung in einem isolierten VEnv entwickelt. Dabei geht es in erster Linie um Abhängigkeiten (Dependencies). 
Abhängigkeiten - zum Beispiel von bestimmten Interpretern oder Modulversionen. 
Für bestimmte Projekte können so unabhängige spezifische Libraries verwendet werden.

Ziel: Die globale Python Installation bleibt unabhängig von Projekten und wird nicht zugemüllt.

Es ist dabei üblich, für jede VEnv, Projekt-Dependencies genau zu definieren (z.B. in einer readme.md), dies fördert die Wiederverwendbarkeit von Code - logisch.
___
## Python Variablen

Each variable points to a place in memory. Python is dynamic also in the sense that during creation of a variable no #datatype has to be determined.

Variables further:

* Dürfen keine Leerzeichen enthalten oder mit einer Ziffer beginnen.
* Variablen werden in `Snake-Case` geschrieben (lower_lower)
* Um den Datentyp eines Objekts zB einer Variable herauszufinden: use *type()* (z.B. during Debugging)\
* <class 'int', 'fl', 'str' oder 'bol'>\
* Weitere Datentypen: Complex (z.B. 12j, cnet library) and None\

* Komplexere #datatypes: lists, arrays, tuples, dictionaries, sets
## Anonyme variablen

#anonymous
```python

```
___
## (Alles ist ein) Objekt-ID

Eine eindeutige Objekt-ID wird erstellt in dem moment indem das Objekt im Code interpretiert wird und mit dem Zuweisungsoperator `=` zugewiesen wird.
Die `id()-Funktion` gibt, eine für diese IDE-Session einzigartige Objekt-Position im Speicher wieder #memory-address . Diese Position verhält sich verschieden für veränderbare und nicht veränderbare Objekte in Python und wird im Objektnamen of als hexadecimal angegeben.
  
```python
x = 5

print(id(x))
# 140724021355432 # unique for this VS-ode session
```

```python
x = ["apple", "banana", "cherry"]
y = ["apple", "banana", "cherry"]

print(x is y)  # False

# Both lists are identical but not the same object in memory
```
___
## Iterable & Iterator

Über einen Iterable - kann iteriert werden. Dazu muss die entsprechende Klasse die `__iter__()`.Methode implementieren, die wiederum einen Iterator liefert. 
Containers mit `__iter__()`: lists, tuples, dicts, strings, sets, bytes.

Note: Eine Sequenz = Ein Iterable + geordnete Elemente

Der Iterator (Objektfabrik, liefert immer das nächste Objekt). Ein Iterator implementiert die `__next__()`.Methode und ruft damit immer das nächste Objekt auf.

```python
for digit in 123456:

    print digit

# TypeError: 'int' object is not iterable

############
  
num = 123456 # genauso not iterable

digits = [int(digit) for digit in str(num)]

# Wenn wir die digits in string umwandeln und dann als integer in eine Liste packen ginge das schon!

```

```python

mystr = "banana"

myit = iter(mystr)


print(next(myit)) # B
print(next(myit)) # a
print(next(myit)) # n
print(next(myit)) # a
print(next(myit)) # n
print(next(myit)) # a
```

# Abstract Base Classes (ABC's)

```python
```
___
___
## 5 weitere Key-Konzepte in Python
___
### #PEP-8 - Style Guide for Python Code

https://peps.python.org/pep-0008/
___
### Don't repeat code - reuse code!
___
### Readability is key!

Daher z.B.: Variablen die eine Mehrzahl an Elementen enthalten auch so benennen (Singular/Plural).\
Schlüssiges  Beispiel:

```python
for city in cities:

    print(city)
```
### Gebrauche (list-)comprehension
#list #loop 
Wenn es Zeilen Code spart und die Lesbarkeit fördert natürlich.

Im Grunde ein *for-loop* der in einer Zeile eine neue Liste direkt bevölkern kann. 
Zum Beispiel:

```python
new_list_of_nums = [num for num in range(1, 11)] 
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# with condition
new_list_of_nums = [num for num in range(1, 11) if num % 2 == 0] 
# [2, 4, 6, 8, 10]
```

Zum erstellen einer Listen von Listen (Matrizen):
```python
mt5 = [[_num for _num in range(1,6)] for num in range(1,6)]
# [[1, 2, 3, 4, 5], 
# [1, 2, 3, 4, 5], 
# [1, 2, 3, 4, 5], 
# [1, 2, 3, 4, 5], 
# [1, 2, 3, 4, 5]]
```
___
### Function Arguments & Parameter Types

Parameter sind die Variablen, die in der Definition der Funktion aufgestellt werden.
Arguments werden gegeben wenn eine Funktion gecallt wird.

```python
# Positional arguments
def some_function(x: int, y: int) -> None:
	print(x, y)

some_function(10, 20) # 10 20

#############################

# Non-positional
def some_function(x: int, y: int) -> None:
	print(x, y)

some_function(y=20, x=10) # 10 20

############################

# Mixed
def some_function(x: int, y: int, z: int) -> None:
	print(x, y, z)

some_function(10, z=30, y=20) # 10 20 30

############################

# Default arguments
def some_function(x=10, y=20):
	print(x, y)

some_function() # 10 20

############################

def some_function(x: int, y: int, z=None) -> None:
	print(x, y, z)

some_function(10, 20) # 10 20
```

## `*args & **kwargs`

Der Entpackungs-Operator `*` (auch Decomposer #decompose) erlaubt die Verwendung von beliebig vielen positional- bzw. Keyword-Arguments.

```python
def some_function(*arguments, **keywordarguments):
	print(arguments, keywordarguments)

some_function(10, 20, 30, aa='whats', bb='up!')
# (10, 20, 30) {'aa': 'whats', 'bb': 'up!'}
```
___
## `if __name__ == "__main__": 'lets run this program'`

Die finales Zeilen eines Skripts. Mit der unten genannten Zeile wird sichergestellt, dass das Skript nur ausgeführt wird wenn selbiges offen und selbst direkt ausgeführt wird.

```python
if __name__ == "__main__":
	main() # Programm
```
