___
[[Python]]
___
Klassen in Python sind quasi ein Objekt-Konstruktor. Java und C# z.B. sind rein Objekt orientiert. 
Der Konstruktor kann als 'Blueprint' verwendet werden um unabhängige Klassen-Objekte zu erstellen.

Klassen-Objekte können dabei Dinge mit bestimmten Eigenschaften aus dem realen Leben repräsentieren um mit dies dynamisch zu programmieren.

In Python geht es auch komplett ohne OOP, und nicht in jeder Situation ist OOP (Klassen anlegen) angebracht.

```python
class Movie:

    info = """Not much happening here"""

  

a_boring_movie = Movie() # Here we create an objekt of the class: Movie

print(a_boring_movie.info) # Not much happening here
```

In Python wird eine Klasse durch die `__init__()` #built-in  #dunder Methode initialisiert. 
___
#### The initializer/constructor `__init__()`

Note: Die `__init__()` Funktion wird immer automatisch aufgerufen wenn ein neues Objekt der Klasse erstellt wird, aber hat keinen eigenen Rückgabewert #return . 
#mro 
```python
class Brains:

    def __init__(self) -> None:
        print(True)

  

class Smarts(Brains): # Child class
    pass


good_grades = Smarts() # True
# Once this instance is constructed __init__ is executed -> print(True)
# However if Smarts had a own __init__ function, this own would preceed that of the superclass
```
Eine Klasse  mit constructor muss als Parameter mindestens `self` haben. Dieses wird von Python selbst abgerufen.

Der Klasse können dann Attribute zugewiesen werden, die beim initialisieren neuer Instanzen der Klasse übergeben werden. Eine Klasse kann so im Prinzip eine unendliche Anzahl an Instanzen haben!

```python
class Movie:

    def __init__(self, title: str, year: str) -> None: # Parameter

        self.title = title # Attribute

        self.year = year

  

lotr = Movie("The Lord of the Rings", "2001") # Objekt
stwars = Movie("The Phantom Menace", "1999")

print(type(lotr))   # <class '__main__.Movie'>

  

# Alle Objekt-Attribute anzeigen

print(vars(lotr)) # {'title': 'The Lord of the Rings', 'year': '2001'}
print(vars(stwars)) # {'title': 'The Phantom Menace', 'year': '1999'}
```
___
### A class instance

Klasse = 'Blueprint'. 
Instanz = Spezifisches Objekt konstruiert mit dem 'Blueprint' 

```python
class Cookie:

    def __init__(self, topping: str):

        self.topping = topping

  
  

chocolate_cookie = Cookie('Chocolate butter cream') # 1. Instance

rainbow_cookie = Cookie('Rainbow sugar sprinkles') # 2. Instance
```

Die Erstellung einer Klasse hilft, die simultane Zuweisung mehrerer verschiedener Werte (Attribute), die mit einer spezifischen Instanz dieser Klasse assoziiert werden, einfacher zu gestalten. Denn die Alternative wäre: mehrere indizierte Listen zu jeweils einem Attribut, die aber eigentlich in Relation zu den unterschiedlichen Objekten stünden - wow!

```python
class Character:

    def __init__(self, health, damage, faith):

        self.health = health

        self.damage = damage

        self.faith = faith

  

    def lembas_bread(self):

        self.health += 20

        self.faith *= 2

  

mister_frodo = Character(80, 20, 50)    # Object, Instance of the class: Character

print(f"""Frodo attributes: 
H:{mister_frodo.health}, 
D:{mister_frodo.damage}, 
F:{mister_frodo.faith}
""")

# Frodo attributes: 
# H:80, 
# D:20, 
# F:50


mister_frodo.lembas_bread() # no self here

print(f"""Frodo attributes: 
H:{mister_frodo.health}, 
D:{mister_frodo.damage}, 
F:{mister_frodo.faith}
""")

# Frodo attributes: 
# H:100, 
# D:20, 
# F:100
```
___
## Vererbung

Python Klassen können Abkömmlinge haben, die Eigenschaften der Eltern-Klasse erben und gleichzeitig eigene einzigartige Attribute haben. 

```python
class A:
    pass


class B(A): # Child-Class
    pass
  

print(issubclass(B, A))  # True
```

Änderungen an der Eltern-Klasse sind somit automatisch bei allen Kind-Klassen (Child-Classes) anwendbar und wir müssen die Änderung nicht bei jeder Klasse einzeln vornehmen. Super!

```python
class Humanoid:
  
    alive = True

    def eat(self):

        print("This human is eating")

    def sleep(self):

        print("This human is sleeping")

  

class Citzen(Humanoid): # ist ein Kind der Humanoid-Klasse
    pass

class Wildling(Humanoid):
    pass

class Synth(Humanoid):

    alive = False

  

citizen = Citzen()
wildling = Wildling()
synthetic = Synth()
  

print(citizen.alive)    # True

print(synthetic.alive)  # False

print(wildling.eat())   # This human is eating

# Note: Klassenattribute, zum Beispiel eine Variable 'alive' wird im Scope von innen nach außen bei der ersten Möglichkeit abgerufen, sogesehen von spezifisch (Wildling) nach unspezifisch (Humanoid).
```
___
## Polymorphismus

Polymorphismus in Klassen wird benutzt um eine Methode (Funktion) mit unterschiedlichem Outputs in mehreren, auch unterschiedlichen Klassen-Objekten, gleichzeitig aufzurufen. 

Achtung, der Funktionsaufruf folgt dabei der #mro der Method-Resolution-Order. Das heißt wenn eine Kindsklasse in dieser Reihenfolge erstellt wird:
```python
class ParentX:
	pass

class ParentY:
	pass

class Child(ParentX, ParentY):
	pass
```
wird beim Aufruf einer Methode zuerst (und wenn erfolgreich nur) in der Elternklasse `ParentX` ausgeführt.

Wenn die Methode in allen Klassen gleich benannt ist, kann so durch Iteration, z.B. in einem for-loop durch alle Klassen-Objekte, ein gleicher Funktionsname ausgeführt werden (was die Funktion macht kann von Klasse zu Klasse unterschiedlich sein).

```python
class Elves:

    def __init__(self, rings_of_power) -> None:

        self.rop = rings_of_power

    def one_ring(self):

        print(f"{self.rop} den Elbenherrschern hoch im Licht")


  
  class Dwarves:

    def __init__(self, rings_of_power) -> None:

        self.rop = rings_of_power

    def one_ring(self):

        print(f"{self.rop} den Zwergen in ihren Hallen aus Stein")

  
  
class Humans:

    def __init__(self, rings_of_power) -> None:

        self.rop = rings_of_power

    def one_ring(self):

        print(f"Den Menschen ewig dem Tode verfallen - {self.rop}")

  
  

elves = Elves(3)
dwarves = Dwarves(7)
humans = Humans(9)


for ally in (elves, dwarves, humans):

    ally.one_ring()

print("One ring to rule them all")

  

# 3 den Elbenherrschern hoch im Licht

# 7 den Zwergen in ihren Hallen aus Stein

# Den Menschen ewig dem Tode verfallen - 9

# One ring to rule them all

```

Das Prinzip funktioniert auch bei Kind-Klassen. Und auch hier gilt von spezifisch nach unspezifisch. Also wird die Methode erst in den Kind-Klassen aufgerufen, wenn dort nicht vorhanden aber auch zusätzlich über die Super-Klasse - sollte der Methodenname gleich sein.

```python
class Order:

    def __init__(self, growthform):

        self.grofo = growthform

      def info(self):

        print("Accepted")

  
  
class Genus(Order):

    pass

    

class Species(Genus):

     def info(self):

        print("Extinct")

  

pocillopora = Genus(growthform="various")
p_meandrina = Species(growthform="encrusting")


for scope in (pocillopora, p_meandrina):

    scope.info()

    print(scope.grofo)

# Accepted
# various
# Extinct
# encrusting
```
___
### Super-Klassen

```python
class Brains:
    pass

  
class Smarts(Brains):
    pass

  
class Knowledge(Brains):
    pass

  
class MidiChlorians(Smarts, Knowledge):
    pass
  

print(MidiChlorians.__bases__)

# (<class '__main__.Smarts'>, <class '__main__.Knowledge'>)

# MidiChlorians has 2 direct superclasses

  

jedi = MidiChlorians()

print(isinstance(jedi, Brains)) # True

# Brains is an indirect superclass from MidiCholrians Class

# Therefore jedi is also an instance from Brains
```

