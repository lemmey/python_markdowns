___
[[errors]]
[[documentation]]
#debug 
___
Ein `try`-Block erlaubt das testen von Code parallel zu dessen Ausführung. Der dazugehörige `except`-Block definiert wie auf einen Error (eines bestimmten Typs) reagiert werden soll, sollte dieser auftreten.   

Note: Normalerweise stoppt ein Python-Programm wenn es auf einen Error stößt und gibt diesen dann in der Konsole aus.
Beim Handling mit exceptions wird der Error zwar adressiert, aber nachfolgender Code wird ebenfalls ausgeführt - cool!

```python
# x = 11

try:

    print(x)    # Das gäbe eigentlich einen NameError (da x auskommentiert)

except:

    print("Die Variable ist nicht definiert")

    # also: 'Die Variable ist nicht definiert' : Und kein Error!
```

Es können mehrere `exceptions` auf ein `try` folgen. Das mach z.B. Sinn wenn auf verschiedene Fehlertypen unterschiedlich reagiert werden soll, oder Fehler beim debugging zu identifizieren:
```python
try:

    print(x)

except NameError:

    print("NameError occured")  # NameError occured

except ValueError as e:

    print(e, type(e))

except:

    print("Something else went wrong")
```

Wenn auf ein Error-handling reagiert werden soll, in dem Fall, dass kein Fehler erhoben wurde, kann das `else`Keyword benutzt werden.
```python
try:

    print(10)

except:

    print("Something went wrong")

else:

    print("Well done, nothing went wrong")

# 10

# Well done, nothing went wrong
```

Und wenn in jedem Fall noch reagiert werden soll, ob mit oder ohne Fehler im Code, dann: `finally`.
Tipp: Das macht Sinn, etwa beim Öffnen und Schließen von Dateien mit `open()` und `finally:` `close()`.
```python
bye = "I just wanted to say: I love you guuuys!"

try:

    print(10)

except:

    print("Something went wrong")

else:

    print("Well done, nothing went wrong")

finally:

    print(bye)


# 10

# Well done, nothing went wrong

# I just wanted to say: I love you guuuys!
```