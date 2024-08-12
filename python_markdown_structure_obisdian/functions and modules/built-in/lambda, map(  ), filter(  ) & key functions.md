___
[[functions]]
[[comprehensions]]
[[loops]]
#built-in 
#ZEN 
___
## Lambda

Lambda-Funktionen ergeben immer ein Funktionsobjekt, das eine Referenz UND einen  Rückgabewert beinhaltet, Sie können daher wie oben zu sehen direkt aufgerufen werden.

Die Idee hinter lambda-Funktionen ist es sie in Higher-Order Funktionen zu benutzen, wie z.B. `map()` oder `filter()`. Alleinstehende lambda-Funktionen sind nach PEP-8 zu vermeiden.
#lambda 
```python
numbers = [2, 48, 42, 16]

even = lambda x: x % 2 == 0 # logical  

result = [even(number) for number in numbers] # [Booleans]
  

if all(result):

    print('All numbers are even') # True
    
elif any(result):

    print('At least one even number')
    
else:

    print('No even numbers')
```
## Mapping

Mit `map()` kann man z.B. alle Werte eine Sequenz ändern, ohne einen Loop anzuwenden. Die  Funktion gibt dabei erstmal nur ein map-Objekt (noch ein Iterator) zurück.
#lambda
```python
# Example mapping of a built-in function to an iterable
animals = ['millipede', 'giraffe', 'coral snake']

animal_lengths = list(map(len, animals))

print(animal_lengths) # [9, 7, 11]

##################### lambda modifications

animals = list(map(lambda x: x + 's', animals))

# ['millipedes', 'giraffes', 'coral snakes']
```
## Filter

Mit `filter()` kann man z.B. alle Werte eine Sequenz filtern, ohne einen Loop anzuwenden.
Dabei können eingebaute und eigene Funktion, sowie lambda-Funktionen verwendet werden.
#lambda
```python
animals = ['millipede', 'giraffe', 'coral snake']

def longer_than_10(input: list[str]) -> bool:

    return len(input) > 10

  
animals_filtered = list(filter(longer_than_10, animals))

print(animals_filtered) #['coral snake']

####################### as lambda & without defining an explicit function

animals_filtered = list(filter(lambda x: len(x) > 10, animals))
```