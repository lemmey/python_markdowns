___
[[assert]]
#bool
___
Das `in` #Keyword hat zwei Anwendungsbereiche. Zum einen wird es verwendet um zu überprüfen, ob ein Wert in einer #sequence enthalten ist, also in einer Liste, einem String einem Range-Objekt etc. und zum anderen wird es im for- #loop verwendet um durch die Werte einer Sequenz zu iterieren.

Zum Beispiel:
```python
my_list = [
    [1,2,3],
    [2,3,4],
    [3,4,5],
    ]

  
check = [1,2,3]

if check in my_list:

    print(f'Check on sequence: {check} successfull')
    
# Check on sequence: [1, 2, 3] successfull
```

```python
my_list = [
    [1,2,3],
    [2,3,4],
    [3,4,5],
    ]
  

check = [2,3,4]
 

if check in my_list:

    print(f'Check on sequence: {check} successful')

    for i in enumerate(my_list): #tuple

        if i[1] == check:

            print(f'Sequence found at index {i[0]}')

# Check on sequence: [2, 3, 4] successful
# Sequence found at index 1
```