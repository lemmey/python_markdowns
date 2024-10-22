___
[[Python]]
[[Markdown (.md)]]
#ZEN 
___
### Program structure

How to build a program/project: #tbc
```python
KONS_Vars = 1

def fn():

    print("fn")

  
  

def fn2(value):

    print("fn2")

  
  

def main():

    x = fn()

    y = fn2(x)

  
  
if __name__ == '__main__':
	main() # Hier wird das gesamte Projekt ausgeführt
```
___
### Type hints

Type hints können die Lesbarkeit für Code Edits oder beim debuggen stark erhöhen. Type hints werfen auch einen Syntaxfehler im Editor, wenn z.B. der Variablentyp vom 'Soll' abweicht.
```python
# anstatt
X: int = 10

###########

def divide(x: int, y:int) -> float:
	return x/y

##############

def f(numbers: list[int]) -> None:
	for num in numbers:
		print(num)

##################

users: dict[int, str] = {
	1: 'pawnstar69',
	2: 'twinkle666'
}
```
___
### Doc-String

Das verfassen von Document-String unterliegt i.d.R. verschiedenen Formatierungsvorgaben. Dies kann von Unternehmen zu Arbeitgeber unterschiedlich sein.  Der Doc-String wird auch angezeigt, wenn die `help()-`Funktion auf eine selbst geschriebene Funktion angewandt wird.

Für Maschinelles Lernen, könnte ein standardisierter Doc-String so aussehen:
```python
def unidentfied_numpy_function():
    """ Summary line
    Beschreibung: Berechnet dies und das


    Parameters
    ----------

    filename :

    copy :

    dtype :

    etc.

  
    Returns
    -------
  

    Raises
    ------

    """
```