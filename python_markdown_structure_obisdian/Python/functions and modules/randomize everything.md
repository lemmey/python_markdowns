___
[[random]]
#project 
#g2k
#seed
___

Pseudozufallszahlen aus dem Modul random sind KEINE richtigen Zufallszahlen. Deshalb nicht zum Verschlüsseln von sensiblen Daten verwenden. Der Initialwert (seed) bestimmt den weiteren Verlauf der Zufallszahlen, welche dadurch vorherbestimmbar sind.

```python
import random

# Jede Sitzung in Verwendung von 'random' beginnt mit einem 'seed'

random.seed(111) # Initialwert für random


# Ganzzahlen

rnd_integer = random.randint(1, 10)

print(rnd_integer) # 7


# Float

rnd_float = random.uniform(99, 100)

print(round(rnd_float, 3) # 99.36


# 0 - 1

rnd_value = random.random()

print(round(rnd_value, 3) # 0.819


# Anwendungsbeispiel

for _ in range(10):

    rnd_int = random.randint(100, 1000)

    print(rnd_int, end='-') # 505 643 117 287 706 550 883 295 412 889

```

Einen ein-dimensionalen string pseudo-randomisieren.

```python
import random

import string

  
random_string = ''.join(random.choices(string.ascii_lowercase, k=5))

print(random_string) # ksdjj
```

### Sampling mit random

```python
hobbits = ["Frodo", "Samwise", "Merry", "Pippin"]


print(random.choice(hobbits)) # Pippin
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


    fs = [f1, f2, f3]

    return random.choice(fs)

  
  

for _ in range(3):

    p = f()

    print(p(3))
```