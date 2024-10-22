___
[[comprehensions]]
#built-in 
#anonymous
#ZEN 
___
Lambda Funktionen sind anonyme Funktionen, sie können daher **ohne** individuelles Funktions-Objekt erstellt und ausgeführt werden - z.B. wenn die Funktion nicht wiederverwendet wird!
#project
```python
# Example user management
fn = 'benjamin' # input a
ln = 'BLümchen' # input b

# lambda function-object
full_name = lambda firstname, lastname: firstname.strip().title() + ' ' + lastname.strip().title()

print(full_name(fn, ln)) # Benjamin Blümchen
```
Lambda-Funktionen ergeben immer ein Funktionsobjekt, das eine Referenz UND einen  Rückgabewert beinhaltet. 
```python
lambda inputX, inputY: 'a single expression as the return value'
```
Sie können so direkt aufgerufen werden oder als Funktionsschlüssel in anderen Funktionen verwendet werden. Die Idee hinter lambda-Funktionen ist es sie in Higher-Order Funktionen zu benutzen, wie z.B. `map()` oder `filter()`. 

Alleinstehende lambda-Funktionen sind nach #PEP-8 zu vermeiden. #

#lambda 
```python
numbers = [2, 48, 42, 16]

even = lambda x: x % 2 == 0 # logical  

result = [even(number) for number in numbers] # [Booleans]
  

if all(result): # ... are True

    print('All numbers are even') # True
    
elif any(result): # ... is True

    print('At least one even number')
    
else: # ... non is True 

    print('No even numbers')
```
___
### Mapping

Mit `map()` können z.B. alle Werte eine Sequenz geändert werden, ohne einen Loop anzuwenden.

Die  Funktion gibt dabei erstmal nur ein map-Objekt (noch ein Iterator) zurück.

```python
nums = [1, 2, 3, 4, 5]

squares = list(map(lambda num: num**2, nums))

print(squares) # [1, 4, 9, 16, 25]
```

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
___
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