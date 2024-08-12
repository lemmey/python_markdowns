___
[[documentation]]
#debug 
___
## Logging basics
Logging ist für zeitaufwendige Operationen z.B. Machine Learning Models essenziell, unteranderem zur Fehler Identifizierung.

## Logging levels

* CRITICAL = 50
* FATAL = CRITICAL
* ERROR = 40
* WARNING = 30
* WARN = WARNING
* INFO = 20
* DEBUG = 10
* NOTSET = 0

```python

```

```python
import logging

import os

from pathlib import Path

os.chdir(Path(__file__).parent)
```

```python
def add(x,y):

    total = x + y

    logging.debug(f' x-> {x}, y-> {y} -> zwischen Ergebniss :{total}')
    logging.info(f' x-> {x}, y-> {y} -> zwischen Ergebniss :{total}')

    return total

  

def main():
	# create / config Logging
    logging.basicConfig(filename= "app.log", level= logging.DEBUG,

                        format= "%(asctime)s  - %(filename)s - %(name)s - %(levelname)s - %(message)s ")

    logging.debug('This is a debug Message')
    logging.info('This is an info Message')
    logging.warning('This is a warning Message')
    logging.error('This is an error Message')
    logging.critical('This is an error Message')
    
    UIx = int(input('Please enter a digit:'))

    UIy = int(input('Please enter a digit to add:'))

    total = add(UIx,UIy)

    print(total)

  

if __name__ == '__main__':

	main()
```
  
