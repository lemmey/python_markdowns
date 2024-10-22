___
[[comprehensions]]
#ZEN 
___
Der Assignment-Expression-Operator oder Walrus Operator (Py3.8) ist umstritten, da dieser unter Umständen die Lesbarkeit verringern kann. In manchen überschaubaren Fällen kann man mit dem `:=` Codezeilen sparen, da dieser die Zuweisung einer Variablen und deren komplexen Inhalt auf eine Zeile verkürzen kann.
Beispiel: In if-Statements wird die Variable (hier `UI_length`) direkt mit dem if-Code-Block assoziiert, das erhöht bei langen Skripten die Lesbarkeit.
```python
x = 3
print(x)

# same as

print(x := 3)
```

```python
UI: str = 'lemmey'
# UI_length = len(UI) # we save that line (if we strive for dynamic code)

if (UI_length := len(UI)) > 3 and UI.isalpha(): # Note the double brackets

    print(UI_length, 'Sign-up successfull!')

else:

    print(UI_length, 'Please enter a valid name')

# 6 Sign-up successfull!
```

Beispiel 2:
```python
def analyze_text(text: str) -> dict:
	# words = text.split() # we basically save that line

    details: dict = {'words': (words := text.split()), # returns list
                  'amount': len(words), # len of that list
                  'characters': len(''.join(words)) # count chars without spaces
                  }

    return details
  

t1 = '''One ring to rule them all,
one ring to find them,
One ring to bring them all
and in the darkness bind them.'''

t1_dict = analyze_text(t1)
print(t1_dict)

# {'words': ['One', 'ring', 'to', 'rule', 'them', 'all,', 'one', 'ring', 'to', 'find', 'them,', 'One', 'ring', 'to', 'bring', 'them', 'all', 'and', 'in', 'the', 'darkness', 'bind', 'them.'], 'amount': 23, 'characters': 85}
```

Beispiel 3:
#debug
```python
# Um zu checken, ob eine unübersichtliche Funktion einen Rückgabewert hat oder None

def func():
	return None


if re := func(): # currently False
	print('Returns', re)
else:
	print('No return value')

# 'No return value'
```

Beispiel 4: List comprehension &  function
```python
my_numbers = [3, 4, 5, 6, 7, 8, 199, 10_099]

def squared(num):
	return num**2


result = [squared(x) for x in my_numbers if squared(x) < 100]
# hier wird die Funktion `squared()` zweimal aufgerufen, bei komplexeren Funktionen ist das ein signifikanter Zeitverlust,so:

result = [intm_result for x in my_numbers if (intm_result := squared(x)) < 100]

print(result) # [9, 16, 25, 36, 49, 64]
```

Beispiel 5: Loop break mit User-Input
#pythonic
```python
leave = False

while not leave:

    UI = input('Please enter a command (or send q to quit):\n>>>')

    if UI == 'q':
        print('Good bye')
        leave = True # synthetic break

    else:
        print(f'Your command {UI} will be executed')

######### with :=

while (UI := input('Please enter a command (or send q to quit):\n>>>')) != 'q':
	print(f'Your command {UI} will be executed')



```