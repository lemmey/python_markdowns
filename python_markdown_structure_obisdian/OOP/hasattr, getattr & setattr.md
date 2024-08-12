___
[[OOP]]
[[functions]]
#built-in 
#logical 
___
Die Funktionen `getattr()` und `setattr()` geben ein Klassen-Attribut aus bzw. ändern ein Klassen-Attribut. `hasattr` gibt einen Boolean zurück.
```python
class Wizard:

    def __init__(self, name, age, color) -> None:

        self.name = name

        self.age = age

        self.color = color

  
  

g_dog = Wizard(name='gandalf', age=2031, color='Gray')

print(g_dog.color) # Gray

print(hasattr(g_dog, 'name')) # True

setattr(g_dog, "color", "White") 

print(getattr(g_dog, "color")) # White

# delattr(Wizard, "age")
```