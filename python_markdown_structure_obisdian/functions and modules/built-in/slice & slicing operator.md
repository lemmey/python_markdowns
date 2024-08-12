___
[[functions]]
#iterable
#built-in
___


## Das slice-Objekt
Mit mit der `slice()`-Funktion lässt sich ein dynamisches Slice-Objekt festlegen, welches dann als Proxy für die 'Schnittweite' und den Schritt, beim Schnitt durch einen Iterable angegeben werden kann:
```python
my_numbers: list[int] = list(range(0, 10))
my_text: str = 'Hello World'

slicer: slice = slice(None, None, -1) # start, stop, step


print(my_numbers[slicer]) # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

print(my_text[slicer]) # dlroW olleH

######################

slicer2: slice = slice(1, 6, None)

print(my_numbers[slicer2]) # [1, 2, 3, 4, 5]
```