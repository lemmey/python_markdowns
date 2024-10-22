___
[[datatypes]]
#mutable 
#iterable
___
# String = Eine `sequentielle` und `unveränderliche` Zeichenkette

Jedes Platzzeichen in einem str-Objekt ist ein Element. String ist daher sequenzielles Objekt, jedes Element ist `indizierbar`. 
By default ist die Reihenfolge der Indizierung von links nach rechts.

Indiziert, auf einen Index zugegriffen wird wie folgt:

```python
example_string = "abc"

print(example_string[3])  

# <Index error: Out of range>
# as [0, 1, 2]
```

Strings und String-Elemente sind `UNVERÄNDERLICH`:

```python
example_string[1] = "B"  

# <TypeError: str does not support item assignment>
```

## Strings manipulieren

Ein String kann 'ADDIERT' und 'MULTIPLIZIERT' werden. Weiter können Zahlen in String-Format konvertiert werden: 

```python
x = 100.0
print(x, type(x)) # 100.0 <class float>

x = str(x)
print(x, type(x)) # 100.0 <class 'str'>

y = '10' + '10'
print(y, type(y)) # 1010 <class 'str'>

z = '10' * 10
print(z, type(z)) # 10101010101010101010 <class 'str'>
```

## String Methoden

String Methoden sind in der Regel `case-sensitive`.

```python
s = 'xyz äß'

s = s.title()
print(s)    # 'Xyz Äss'

s = s.capitalize()
print(s)    # 'Xyz äß'

s = s.upper()
print(s)    # 'XYZ ÄSS'

s = s.lower()
print(s)    # 'xyz äss'

s = s.casefold()
print(s)    # 'xyz äss'
```

### Splitting String
Bei Default wird ein String an Leerzeichen gesplittet.  Das Ergebnis der .split() Methode ist eine Komma-separierte Liste

```python
text = '0 1 2 3 4 5 6 7 8 9'

print(text.split())
# ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']

# with maxsplit argument
print(text.split(' ', 1)) # only 1 split from left to right
# ['0', '1 2 3 4 5 6 7 8 9']
```
### String dursuchen

```python
txt = "Hello, welcome to my world."  
  
x = txt.startswith("wel", 7, 20)  # also .endswith()
  
print(x) # True
```

```python
txt = 'See, same same but different'
count_x = txt.count('same') # 2

# count from index 10 to end
count_o = txt.count('same', 10) # 1
```

```python
txt = 'See, same same but different'

# Finds the first occurence
# Note: other than .index(), this method return -1 if nothing is found
count_x = txt.find('same') # 5
```

```python
txt = 'See, same same but different'

# Finds the first occurence!
where_txt = txt.find('saame', 5, 15)   

print(where_txt) # -1
```
### Replace String-Elements

```python
txt = 'See, same same but different, it\'s the same'
txt = txt.replace('same', 'different', 2)
print(txt) 

# 'See, different different but different, it\'s the same'
```
### Case: String-Normalisierung

Zum Beispiel für `Natural-Language-Processing` oder `User-Input-Processing`.

```python
UI = "2,345"
UI_clean = float(UI.replace(",", "."))
```

```python
# What is your favourite fruit?
UI = 'Hmm...banana ...'
UI_clean = UI.casefold().strip('hmm ...')

print(UI_clean) # banana
```
___
### Slicing String

Strings sind nach wie vor `unveränderlich`. Beim `String-Slicing` wird ein Teil herausgeschnitten. Der originale String bleibt aber bestehen.

Note: Beim slicing wird geschnitten `Von : Bis(not included) : in Schritten von`.

```python
text = '0123456789'

tx = text[::2] # 02468
et = text[1::2] # 13579
txet = text[::-1] # 9876543210
```

### String `index()`

#ValueError
```python
# Similar to find()

x = 'abc'

print(x.find('a')) # 0

print(x.find('d')) # ValueError
```
___
### `join()`

Syntax: `_string_.join(_iterable_)`

The `join()` method takes all items in an iterable and joins them into one string. A separator must be defined as string.

```python
ten_ducks = ('duck', 'duck', 'duck', 'duck', 'duck', 'duck', 'duck', 'duck', 'duck', 'duck')

ten_duckies = 'ies'.join(ten_ducks)

ten_duckies
```
___
### `split()`

Syntax:  `_string_.split(_separator, maxsplit_)`

Splits a string - returns a #list! By default the string is split  at whitespaces.

A number of splits can be defined as integer. Default is -1, for all occurrences. 
If I just split once, i get two list elements, separated by the first separator occurrence. Note that the separator (spliterator) is omitted.

```python
ten_duckies = 'duckiesduckiesduckiesduckiesduckiesduckiesduckiesduckiesduckiesduck'

ten_ducks = ten_duckies.split('ies')

ten_ducks # ['duck', 'duck', ...]
```