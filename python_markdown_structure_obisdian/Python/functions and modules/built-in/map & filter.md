___
[[functions]]
[[lambda]]
___
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
## Filtering

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