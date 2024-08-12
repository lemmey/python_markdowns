___
[[errors]]
#logical 
___
```python
x = 0

assert x   # AssertionError
```

Oder:
```python
IDS = {
	   "id1": "Ben", 
	   "id10": "Solid Snake",
	   }

UI_ID = "id0"

assert UI_ID in IDS, "Diese ID existiert nicht!"

# AssertionError: Diese ID existiert nicht!
```

```python
def start_program(data: dict):

    assert type(data) == dict, "Invalid data type!"

    assert data, "Your file is empty"

  
    print("Data loaded successfully")

  

if __name__ == '__main__':

    start_program(data={id0: 'Master Yoda'})

  
# Data loaded successfully
```
