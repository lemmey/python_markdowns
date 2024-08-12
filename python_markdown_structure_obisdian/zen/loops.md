___
#condition
#logical 
___
Oder Loops, da Iteration durch die Elemente des sequentiellen Objekts.

Es gibt genau zwei Loops in Python:

# FOR Loops

Sammlungskontrollierte Schleife, 100 Elemente == 100  Iterationen.
 
```python
communitees = ["Britta", "Abed", "Troy", "Annie"]

for name in communitees:

    print(name)

print("for-loop end")
```
# WHILE Loops

  Bedingungskontrolliert, im Gegensatz zu einem FOR-Loop, der iterationsgesteuert ist, wiederholt sich der WHILE-Loop solange eine Bedingung `True` ist.
  
```python
# So können einfache Endlosschleifen programmiert werden

while True:

  print("They're taking the Hobbits to Isengard")

# Press Ctrl+C in console to interupt
```

```python
adventure = 1
ten_episodes_and_eight_seasons = 80


while Episode < Eight_Episodes_and_Nine_Seasons:

  print(Episode)
  Episode += 1

print("While-loop end")
```

### Loop Keywords

`Break`:  Um aus einem Loop auszubrechen, z.B. wenn eine bestimmte Bedingung erfüllt ist. Break beendet dabei nur den aktuellen Loop, also hier den inneren:

```python
for x in range(1_000_000):

    if x == 50:

        print(x)

        break

    print(".", end="")

# ..................................................50
```

`Continue`: unterbricht den aktuellen Loop, setzt aber anschließend beim nächsten iterierbaren Element wieder an:
```python
for number in range(10):

  if number == 5:

    print(" ", end="")

    continue  # "continue but skip"

  print(number, end="")

# 01234 6789
```

`for-else`:  Wie in einem if-Statement, kann auch in einem for-Loop das else-Keyword verwendet werden. Das 'else' spezifiziert dann einen Code, der ausgeführt wird wenn der gesamte (oder genestete) Loop gelaufen ist:

```python
for number in range(10):

  print(number)

else:

  print("-Finished!")

# 0123456789 Finished!

# Else does not get executed when the loop is ended by a break keyword
```