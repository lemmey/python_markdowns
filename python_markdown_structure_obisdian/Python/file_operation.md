___
[[Python]]
#readandwrite
#export
___

```python
import os
from pathlib import Path
```

Was ist das Working Directory?
```python
print("Aktuelles Working Directory:", Path.cwd())

# Aktuelles Working Directory: C:\Users\olean\Documents\VSC_Project\Python
```

Wo ist die aktuelle Skript-Datei (*das Programm*) abgelegt?
```python
  print("File location:", __file__)

  # File location: c:\Users\olean\Documents\VSC_Project\Python\py\test.py
```

Wo sind die Daten (Datendatei) abgelegt?
Hier bietet sich an einen Dateien Ordner mit einer Python-Konstanten zu verknüpfen. Z.B.:
```python
DATA_DIR = Path(__file__).parent/"data"

# Hier ist der Daten-Ordner im Über-Verzeichnis zum Pythonskript angeordnet

print(Path(__file__).parent/"data")
# c:\Users\olean\Documents\VSC_Project\Python\py\data
```

Zur Verarbeitung von Dateien über Skript, also zum Lesen und Schreiben, wird generell ein Kontext-Manager empfohlen, da diese Funktion Fehler verhindern kann und geöffnete Dateien automatisch schließt.  Zur Systempflege: Dateien IMMER schließen. Der Inhalt der Datei ist ja schließlich schon in 'content' gespeichert und weiterhin verfügbar.

```python
# READ OHNE Kontext-Manager
DATA_DIR = Path(__file__).parent/"data"

f = open(DATA_DIR/"test.txt", mode="r", encoding="utf-8")

print(f)  # <_io.TextIOWrapper name='C:/Users/olean/Documents/VSC_Project/Python/data/word_count_mirco.txt' mode='r' encoding='utf-8'>

content = f.read()

print(content)  # Hier würde der gesamte Inhalt der .txt-Datei ausgespuckt

f.close()
```

## Kontext-Manager

```python
import os

from pathlib import Path

  
  
with open(DATA_DIR / "0_test.txt", mode="r", encoding="utf-8") as f:

    content = f.read()

    print(content)

```

## .csv Dateien

```python
from pathlib import Path

import csv
```

```python
data_rows = [

    [1, 2, 3, 4],

    ["a", "b", "c", "d"],

    [4, 3, 2, 1]

]

# Kontext-Manager, modus="w"

with open(DATA_DIR / "data_new.csv", mode="w", newline="") as f:

    writer = csv.writer(f, delimiter=",")

    writer.writerow(["id", "x", "y", "zora"]) # Eine Headerzeile schreiben

    writer.writerows(data_rows) # Write new data
```