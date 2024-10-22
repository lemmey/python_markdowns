___
[[Python]]
___
Packages/Libraries sind Sammlungen von Funktionsskripten. Ein Module ist ein Skript mit verschiedenen Funktionen. #double-check 

```python
import numpy

from numpy import random
```

Es ist good practice in Projekten einen try-Block um die abhängigen Imports zu legen:

```python
try:
	from ctypes import windll
except:
	pass

# Die importierte Funktion ist ausschließlich auf Windows verfügbar. So wird zum Beipiel ein Fehler im Skript übergangen wenn das Skript auf einem Betriebssystem anders als Windows verwendet wird
```
___
### Eigene Module

#### Settings Datei
Requirements:
`settings.py`

```python
from settings import *
```

___
## pip

Ein Paket mit pip installieren:
```
pip install [package_name]
```

Ein Paket mit pip updaten:
```
pip install [package_name] --upgrade
```