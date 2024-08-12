___
[[functions]]
[[list]]
[[loops]]
#built-in
#iterable
#sequence 
___
Die Range Funktion erstellt eine Sequenz nach den Eingabewerten:
```python
r = range(100)

print(r) # range(0, 100) # Range object
```

  Um ein Range-Objekt in eine Liste umzuwandeln kann die`list( )`-Funktion verwendet werden:
```python
r_list = list(r)

print(r_list)

# [0, 1, 2, 3, 4, ..., 99]

##########################

rng = range(50, -60, -10)

print(list(rng)) # [50, 40, 30, 20, 10, 0, -10, -20, -30, -40, -50]
  ```


  Range wird gerne als Loop-Objekt verwendet zum Beispiel:
```python
for number in range(0, 101, 10):

    print(number, end= ' ') # 0 10 20 30 40 50 60 70 80 90 100 

# Reverse Range

for i in range (10, 0, -1):

    print(i) # 10 9 8 7 6 5 4 3 2 1 

# Best practice: Remove Laufindex, if not referred to!

for _ in range (3):

    print("Bravo!")

# Bravo! 
# Bravo!
# Bravo!
```