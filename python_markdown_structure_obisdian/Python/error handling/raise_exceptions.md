___
[[errors]]
[[try & except]]
#condition 
#debug 
___
Um als Developer selber `exceptions` an bestimmte Variablen und Konditionen zu hängen kann das `raise` #Keyword benutzt werden:
Es gibt eine Exception-Hierarchie. Ganz oben steht die `BaseException`, kurz darunter `Exception`, der alles anderen Error-Typen untergeordnet sind.

```python
UI = "Heeeeello"


if not type(UI) is int:

    raise TypeError("Please enter a number")

  
# TypeError: Please enter a number
```

Bei der Ausführung von Exceptions wird die Hierarchie auch beachtet:
```python
try:

    raise Exception

except BaseException:

    print("Deckt schon alles ab")

# Deckt schon alles ab
```