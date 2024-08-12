___
[[functions]]
___

```python
from functools import partials
```

```python
def multiply(a: float, b: float, name: str | None = None) -> float:

    if name is not None:

        print(f"{name} a: {a} b: {b}")

  

    return a * b

  
# Normal function call
multiply(2.0, 2.0, '2by2') # 2by2 a: 2.0 b: 2.0

# with naming a partial()

KONST = 2

double = partial(multiply, KONST, name="Double")

print(double(10)) # Double a: 2 b: 10
				  # 20
```