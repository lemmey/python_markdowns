___
[[python_main]]
[[OOP]]
#pymagic
___
Funktionen innerhalb einer Klasse heißen auch Methoden und gehören den Objekten dieser Klasse.

## `__repr__` & `__str__`

Beide Funktionen dienen der String-Representation eines (Klassen)-Objekts und spezifischer dessen zugewiesener Eigenschaften.

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