___
[[OOP]]
[[encapsulation]]

#abc
#pymagic
___
Funktionen innerhalb eines Objekt-Typs, oder einer eigenen Klasse, heißen auch Methoden und gehören dem Objekt dieser Klasse. Diese Special-Methods, die auf ein Objekt zutreffen können eingesehen werden und umfassen Standard und eigene Methoden/Eigenschaften.

Achtung: Einige dieser Methoden sind schon definiert, wenn also überschrieben - sollte darauf geachtet werden die ursprüngliche Funktionalität zu erhalten (wenn so gewünscht).
___
### The `dir()` function

```python
print(dir(__builtins__))

# ['Arithmetic Error', ... ..., 'zip']

# If called without an argument, return the names in the current scope.  
# Else, return an alphabetized list of names comprising (some of) the attributes  
# of the given object, and of attributes reachable from it.  

# If the object supplies a method named __dir__, it will be used; otherwise  
# the default dir() logic is used and returns:  

# for a module object: the module's attributes.  
# for a class object: its attributes, and recursively the attributes of its bases. # for any other object: its attributes, its class's attributes, and recursively the attributes of its class's base classes.

# To print out the built-in functions:

for i in dir(__builtins__):

    if i[0] != '_' and i[0].islower():

        print(i, end=', ')
# abs, all, any, ascii, bin, bool, breakpoint, bytearray, bytes, ... zip
```

```python
x = 'example' # <class 'str'>

print(dir(x))

# ['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', ... ]
```

```python
class Snowflake:

    pass
  

flake = Snowflake()

  
print(dir(flake))

# ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']

# E.g. the __eq__ function is called when the object is logically compared (==). The __doc__ when you want to inspect the docstring
```
___
## `__dict__` : Special attribute

#dictionary 
```python
class Ringbearer:
    pass

  

r2 = Ringbearer()

r2.first_name = 'Bilbo'
r2.last_name = 'Beggins'
  

print(r2.__dict__)

# {'first_name': 'Bilbo', 'last_name': 'Beggins'}
```

```python
class Ringbearer:

    """class Ringbearer: A hobbit-objekt to inherit the one ring."""

    def __init__(self, firstn, lastn) -> None: # dunder: constructor

        self.first_name = firstn

        self.last_name = lastn


print(Ringbearer.__doc__)
# class Ringbearer: A hobbit-objekt to inherit the one ring.


r3 = Ringbearer('Frodo', 'Beggins')

print(r3.__dict__)
# {'first_name': 'Frodo', 'last_name': 'Beggins'}

  
r3.age = 'Thirty-three'

print(r3.__dict__)
# {'first_name': 'Frodo', 'last_name': 'Beggins', 'age': 'Thirty-three'}
```
___
## `__getattr__ & __setattr__`

`__setattr__` wird aufgerufen sobald ein Klassen Attribut erstellt/umgestellt wird. #double-check 
Die Special-Method speichert die gesetzten Attribute auch automatisch in dem Klassen-Dictionary, sodass diese über `__dict__` aufgerufen werden können. 

`__getattr__` wird aufgerufen

```python
class Fellow:

    """class Fellow: A fellow of the fellowship of the ring."""

    def __init__(self, firstn, lastn) -> None:
        self.first_name = firstn # set attribute: name = value
        self.last_name = lastn


    def __setattr__(self, name, value) -> None:
        print(f'>>> Set {name} to {value}')
        self.__dict__[name] = value


    def __getattr__(self, name):
        print(f'>>> Get the "{name}" attribute' )

        if name == 'full_name':
            return f'{self.first_name} {self.last_name}'
        else:
            return AttributeError(f'No attribute named {name}')

  

f1 = Fellow('Frodo', 'Beggins')

# >>> Set first_name to Frodo
# >>> Set last_name to Beggins

# Bei der Erstellung des Klassen-Objekts wird automatisch die __setattr__
# Special-Method für zwei Attribute verwendet. Die zwei Argumente werden
# dabei positionell an die Attribute: first_name und last_name vergeben.

  

f2 = Fellow('Samwise', 'Gamgee')

# >>> Set first_name to Samwise
# >>> Set last_name to Gamgee

  

print(f'First name = {f2.first_name}')
print(f'Last name = {f2.last_name}')

# First name = Samwise
# Last name = Gamgee


print(getattr(f2, 'last_name')) 
# Gamgee
  

print(f2.full_name) # __getattribute__ != __getattr__

# >>> Get the "full_name" attribute
# Samwise Gamgee

  

print(f2.__dict__)

# {'first_name': 'Samwise', 'last_name': 'Gamgee'}
# full_name was not added in the eternal dictionary
```

### Anwendungsbeispiel: `__getattr__`

#app
```python
employees = {
    'Johnny': '000101',
    'Merry': '000110',
    'Sandra': '000099',
    'Lidolbert': '000111',
    'Samuela': '000100',
}
  

class Id(dict):

    def __getattr__(self, name):

        return self[name]

  

re_Id = Id(employees) # an <class 'Id' >, child of <class 'dict'>

# get me ...

print(re_Id.Merry) # 000110
```

___
## `__repr__` & `__str__` : Special method

Beide Funktionen dienen der String(`__str__`)-Representation(`__repr__`) eines (Klassen)-Objekts und spezifischer dessen zugewiesener Eigenschaften, wenn gefordert.

```python
class Waldläufer:

        def __init__(self, attr_a: int, attr_b: int) -> None:

                self.strength = attr_a

                self.dexterity= attr_b

        def x(self):

            return f"({self.strength}, {self.dexterity})"

        def __repr__(self) -> str:

               return f"({self.strength}, {self.dexterity})"

  

faramir = Waldläufer(12, 12)

faramir.dexterity += 1

  

print(faramir) # <__main__.Waldläufer object at 0x000001E85D5E0BE0>

# with __repr__() Method in function body (12, 13) - aha! Magic?

print(faramir.strength, faramir.dexterity) # 12 13

print(faramir.x()) # (12, 13)

print(faramir.__repr__) # <bound method Waldläufer.__repr__ of (12, 13)>

print(faramir.__repr__()) # (12, 13)
```