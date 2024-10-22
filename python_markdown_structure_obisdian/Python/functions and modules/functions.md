___
[[modules]]
#scope
___
Im besten Fall gilt: 
#### Wir schreiben ALLES in Funktionen! 
Da Funktionen die Qualität und Dynamik von Code erhöhen. 
Funktionen sind außerdem testbar - #debug . 
___
In Python ist alles ein Objekt. 
Eine Funktion kann nicht nur ausgeführt werden, sondern unter ihrem Namen (ohne Klammern) verbirgt sich auch eine Instanz/Referenz auf das Funktions-Objekt im Speicher:
```python
def add(x):

    return x + x

  

print(type(add)) # <class 'function'>

print(add) # <function add at 0x000001A0B5A904A0>
```

Eine Funktion besteht i.d.R. aus zwei Teilen. Dem Kopf:
`Der Name der Funktion und die Parameterliste` 

Und dem Funktionskörper:
`Die Anweisungen + Rückgabewert (return value)`
___
Sobald das Programm im Anweisungsblock auf ein #return #Keyword stößt, wird die Funktion verlassen. By default hat jede Funktion einen Rückgabewert, wenn nicht weiter spezifiziert ist dieser immer: `None`.
Mit `return` kann auch zum Beispiel innerhalb einer Funktion aus einem #loop oder einer #condition ausgebrochen werden, ohne `break` oder `quit/exit` zu benutzen.

```python
def f(x='Hello World') -> None: # Hier wird ein Default-Parameter vergeben

    print(x)
  
# Der Funktionsaufruf funktioniert daher auch ohne Argumente, der Default Parameter kann aber durch Neu-Bestimmung als Argument beim Funktionsaufruf überschrieben werden z.B. f('Goodbye') druckt Goodbye
f() # Hello World
```

Beachte, dass es positionelle- und Keyword-Argumente (`=`) gibt und dass positionelle Argumente ausschließlich **vor** Keyword-Argumenten stehen können!
#SyntaxError
```python
def f(x='Hello World', y) # Parameter
	print(x + y)


f(' I am here') # y:Argument
# SyntaxError
```

Hier wird der Rückgabewert als Typ Integer angestrebt, angegeben in type-hints:
```python
def calc_volume(a: int, b: int, c: int) -> int:

    r = a * b * c

    return r

  
r1 = calc_volume(1, 2, 3) # 6
```

```python
def _function(_print: str, amount: int) -> None:

    while amount > 0:

        print(_print)

        amount -= 1


_function('Whazzuup', 3)

"""
Whazzuup
Whazzuup
Whazzuup
"""
```
___
## Nested functions

#pymagic 
```python
def symphony(a, b, c) -> int:

    return a(b(c))

  
  

symphony(print, sum, (range(101))) # 5050
```

```python
import random


def f():

    def f1(x):

        return x**2

    def f2(x):

        return x**3

    def f3(x):

        return x**4

    fs = [f1, f2, f3] # nested functions

  

    return random.choice(fs) # choose one random nested function

    

for _ in range(3): # run 3x times

      p = f() # Funktions-Objekt

      print(p(3)) # call functions with value 3
```

___
### Rückgabewert #Keyword: return

Wie bei Variablen muss der return-Wert nicht im Datentyp definiert werden. 

Wenn in eine Funktion auf das return keyword stößt wird die Funktion verlassen - job done.

Jede Funktion sollte nur einen Datentyp als Rückgabe wert haben - #pythonic 
In einer verschachtelten Funktion, allerdings, können auch mehrere Rückgabewerte sinnvoll sein:

```python
def multiplier(value):

    ''' Rückgabewert: a, b '''

    def square(value):

        return value**2

    def cube(value):

        return value**3

  

    return square(value), cube(value) # return tuple (a, b)

  

result = multiplier(4)

print(result) # (16, 64) <class 'tuple'>
```
___
### Scope: global vs lokal

Der Anweisungs-Block einer Funktion ist unabhängig (lokal) vom Rest des Skripts (dem globalen Hauptprogramm). #UnboundLocalError
Mit den Funktionen `globals()` und `locals()` kann im jeweiligen Scope, jedes enthaltene Objekt im Terminal gedruckt werden. 

```python
num1 = 1
  

def func():

    # num1 = num1 + 3  # UnboundLocalError: ...

    print(num1)
  

'''num1 exists only in the global scope'''

num2 = 1
  

def func2():

    x = num2 + 3

    print(x)  # 4

  
'''num2 can be transferred into local scope but only while being processed into a local variable'''

  
num3 = 1
  

def func3():

    num3 = 3     # Shadows num3 from outer scope

    print(num3)  # 3

  
'''num3 here is simply redefined within the function'''
```

Verwendung von Funktionen im lokalen Scope anderer Funktionen:
#chatgpt
```python
# Function to add two numbers
def add_numbers(x, y):
    result = x + y
    return result

# Function to multiply two numbers
def multiply_numbers(x, y):
    result = x * y
    return result

# Function to perform a combined operation
def combined_operation(a, b, c):
    # First, add the first two numbers
    sum_result = add_numbers(a, b)
    
    # Then, multiply the sum with the third number
    final_result = multiply_numbers(sum_result, c)
    
    return final_result

# Main program
if __name__ == "__main__":
    # Example inputs
    num1 = 2
    num2 = 3
    num3 = 4
    
    # Perform the combined operation
    result = combined_operation(num1, num2, num3)
    
    # Output the result
    print(f"The result of adding {num1} and {num2}, then multiplying by {num3} is: {result}")

```
___
## Function Closures

Ein Closure ist ein Funktionsobjekt, dass Werte im enclosing Scope beibehält, auch wenn diese nicht mehr im Speicher sind. Closures entstehen wenn verschachtelte Funktionen auf Variablen im übergeordneten Funktions-Scope zugreifen.

```python
def outer_func():       # Outer

    message = "Ahoi"    # Outer

    def inner_func():       # Inner

        print(message)      # Inner


    return inner_func() # Outer


outer_func()    # Ahoi
# Invoking 'outer_func()' mit einem Funktions(objekt)aufruf im Rückgabewert -> 
# Verlässt die Funktion, führt aber die inner_func() aus und bereitet den Inhalt  # als Rückgabewert auf.
# Daher, führt hier den inneren 'print' einer freien Variablen aus dem äußeren Scope aus! 

############

def outer_func():

    message = "Hi"

    def inner_func():

        print(message)


    return inner_func     # Nur die Funktionsreferenz

  
 
my_func = outer_func()

print(my_func.__name__) # inner_func (0x00000187040E8900)

# nichtsdestotrotz

my_func()   # Hi

# Die getrennte innere Funktion, wenn invoked, hat immer noch Zugriff auf Variablen aus dem enclosing Scope in dem sie geboren wurde!
```
___
## Function purity

Um als 'pure' zu gelten muss eine Funktion:

* Bei gleichem Input - IMMER den selben Output geben.
* Keine 'side-effects' haben. Das heißt, weder druckt die Funktion etwas im Terminal,  noch greift sie auf den globalen Scope zu (z.B. auf eine Variable und/oder verändert diese)

```python
def summe(a: int, b: int) -> int:

    return a + b


summe(2, 2) # mit a,b definiert als int: 2 -> summe() erzeugt IMMER 4

###########

def filter_values(values: float, threshold: float) -> float:

    return [value for value in values if value > threshold]
    
# Achtung: filter_values() ist nur pure wenn Threshold beim Call übergeben - und keine Variable aus dem globalen Scope eingefügt wird
```
___
## Generator functions (Generators)
### #Keyword: yield

The `yield` keyword is used to return an on-demand #iterable  of values from a function as a generator object. Note, that like this an otherwise memory-breaking size of an object can be generated and processed on-demand #pymagic ! #g2k #bigdata 

Unlike the `return` keyword which stops further execution of the function, the `yield` keyword continues to the end of the function. 

When you iterate through a function with `yield` keyword(s), the generator object returns always the `__next__` value until all yields are exhausted. #dunder

```python
def f():

    yield 'a'
    yield 'b'
    yield 'c'


yield_from_f = f()

  
print(f) # <function f at 0x000001381F193E20>
print(f()) # <generator object f at 0x000001381F271F50>
print(yield_from_f) # <generator object f at 0x000001381F271F50>

  

for y in yield_from_f: # or even f()

    print(y)

# a
# b
# c
```

#dunder #StopIteration 
```python
def square_numbers(nums: list):

    for num in nums:

        yield num**2

  
  
my_nums = [11, 22, 33, 44, 55]

  

print(type(square_numbers)) # <class 'function'>

print(type(square_numbers(my_nums))) # <class 'generator'>

  

my_squares = square_numbers(my_nums)

print(type(my_squares)) # # <class 'generator'>

  

print(next(my_squares)) # 121
print(next(my_squares)) # 484
print(next(my_squares)) # 1089
print(next(my_squares)) # 1936
print(next(my_squares)) # 3025
# print(next(my_squares)) # StopIteration Error

```
___
___
### Some functions to know

#### #Keyword global and local
Das `global` Keyword erkennt eine Variable, die lokal definiert wurde im globalen Scope. 
Oder definiert eine Variable als ausschließlich global, auch im lokalen Scope. 
Zwischen den Arbeitsbereichen global und local kann navigiert werden, bzw. die Isolation von Variablen und Objekten aufgehoben werden. In der Praxis werden die Keywords dafür aber selten verwendet.

Handling a classic in functions: #double-check
Counter:
```python
counter = 0 # global
 

def update_counter():

    global counter # Bezug auf die Variable counter im globalen Scope
	# Nachteil: Potentiell geringere Lesbarkeit von Code wenn das Skript und die       Bezüge undurchsichtiger werden.
    counter += 1
  

update_counter()

################

def better_counter(c):

    c += 1

    return c


better_counter(counter)
```
___
Einen threshold definieren und Werte dementsprechend filtern:
```python
def filter_values(values: float, threshold: float) -> float:

    return [value for value in values if value > threshold] # oder <
```
___
Einen numerischen Iterable nach Nähe zu x sortieren:
```python
def closeness(values: list[int], centroid:int) -> list[int]:

    dist = [centroid - abs(value) for value in values]

    return dist

  
  
dist_to_mid = closeness([1,2,3,-13], 12)

print(dist_to_mid)
```
___
Ein semi-random event initiieren:
```python
import random

def random
```
