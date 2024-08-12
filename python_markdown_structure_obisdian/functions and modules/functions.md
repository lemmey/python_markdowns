___
[[modules]]
#scope
___
Im besten Fall gilt: Wir schreiben ALLES in Funktionen!
Da Funktionen die Qualität und Dynamik von Code erhöhen. 
Funktionen sind außerdem testbar - #debug . 

In Python ist alles ein Objekt. 
Eine Funktion kann nicht nur ausgeführt werden, sondern unter ihrem Namen (ohne Klammern) verbirgt sich auch eine Instanz/Referenz:
```python
def add(x):

    return x + x

  

print(type(add)) # <class 'function'>

print(add) # <function add at 0x000001A0B5A904A0>
```

Eine Funktion besteht i.d.R. aus zwei Teilen, dem Kopf:
Der Name der Funktion und die Parameterliste 

und dem Funktionskörper:
Die Anweisungen und der Rückgabewert - #return value.

Sobald das Programm im Anweisungsblock auf ein Return-Keyword stößt, wird die Funktion verlassen. Note: By default hat jede Funktion einen Rückgabewert, wenn nicht weiter spezifiziert ist dieser immer: `None`.
```python
def f(x='Hello World') -> None: # Hier wird ein Default-Parameter vergeben

    print(x)
  
# Der Funktionsaufruf funktioniert daher auch ohne Argumente
f() # Hello World
```

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

### Globaler vs lokaler Scope

Tipp: Mit den Funktionen `globals()` und `locals()` kann im jeweiligen Arbeitsbereich jedes enthaltenes Objekt im Terminal gedruckt werden. Der Anweisungs-Block ist unabhängig (lokal) vom Rest des Skripts (dem globalen Hauptprogramm):
```python
num1 = 1
  

def func():

    # num1 = num1 + 3  # UnboundLocalError: ...

    print(num1)
  

'''num exists only in the global scope'''

num2 = 1
  

def func2():

    x = num2 + 3

    print(x)  # 4

  
'''num2 can be transferred into local scope but only while being processed into a local variable'''

  
num3 = 1
  

def func3():

    num3 = 3     # Shadows num3 from outer scope

    print(num3)  # 3

  
'''num3 here is just redefined within the function'''
```

## Function closures
Ein Closure ist ein Funktionsobjekt, dass Werte im enclosing Scope beibehält, auch wenn diese nicht mehr im Speicher sind. Closures entstehen wenn verschachtelte Funktionen auf Variablen im übergeordneten Funktions-Scope zugreifen.
```python
def outer_func():

    message = "Ahoi"

    def inner_func():

        print(message)  


    return inner_func()


outer_func()    # Ahoi
# Invoking 'outer_func' ohne Parameter führt somit den 'print' aus dem inneren Scope aus

#########

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

## Function purity

Um als '`pure`' zu gelten muss eine Funktion:

* Bei gleichem Input IMMER den selben Output geben
* Keine 'side-effects' ( ... druckt nichts im Terminal, oder greift auf den globalen Scope zu, z.B. auf eine Variable und oder verändert diese)
```python
# Pure, alle Argumente werden im Funktions-Call übergeben

def summe(a: int, b: int) -> int:

    return a + b


summe(2, 2) # erzeugt IMMER 4 als Rückgabewert

###########

def filter_values(values: float, threshold: float) -> float:

    # HIER: Threshold wird bei Call übergeben und keine Variable aus dem globalen      Scope eingefügt

    return [value for value in values if value > threshold]
```
## Return

Wie bei Variablen muss der return-Wert nicht im Datentyp definiert werden. Allerdings, jede Funktion sollte nur einen Datentyp als Rückgabe wert haben - keep it tidy!

In einer verschachtelten Funktion können mehrere Rückgabewerte sinnvoll sein:
```python
def multiplier(value):

    ''' Rückgabewert: a, b
    '''

    def square(value):

        return value**2

    def cube(value):

        return value**3

  

    return square(value), cube(value) # return tuple (a, b)

  

result = multiplier(4)

print(result) # (16, 64) <class 'tuple'>
```

### Some functions to know

Handling a classic in functions: #double-check

Das `global` Keyword erkennt eine Variable, die lokal definiert wurde im globalen Scope. Oder definiert eine Variable als ausschließlich global, auch im lokalen Scope. Zwischen den Arbeitsbereichen global und local kann navigiert werden, bzw. die Isolation von Variablen und Objekten aufgehoben werden. In der Praxis werden die Keywords dafür aber selten verwendet:
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

Einen threshold definieren:
```python
def filter_values(values: float, threshold: float) -> float:

    return [value for value in values if value > threshold] # oder <
```

Einen numerischen Iterable nach Nähe zu x sortieren:
```python
def closeness(values: list[int], centroid:int) -> list[int]:

    dist = [centroid - abs(value) for value in values]

    return dist

  
  
dist_to_mid = closeness([1,2,3,-13], 12)

print(dist_to_mid)
```