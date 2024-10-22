___
[[functions]]
#built-in 
___
```python
help(print)

'''
print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.
'''
```

```python
abc = ['c','b','a']

help(abc.sort)

"""
Help on built-in function sort:

 sort(*, key=None, reverse=False) method of builtins.list instance
     Sort the list in ascending order and return None.

     The sort is in-place (i.e. the list itself is modified) and stable (i.e. the
     order of two equal elements is maintained).

     If a key function is given, apply it once to each list item and sort them,
     ascending or descending, according to their function values.

     The reverse flag can be set to sort in descending order.
"""
```

```python
def cube_function(a: float, b: float, c:float) -> float:
	'''Calculates volume based on three sides rectangular to each other.
	
	Parameter
	_________
	a -> length of side a, arbitrary positive float value
	b -> length of side b, arbitrary positive float value
	c -> length of side c, arbitrary positive float value

	Returns
	_______
	Volumetric product of the entered parameters as float
	'''
	return a*b*c

################

help(cube_function)

'''
Help on function cube in module __main__:


cube(a: float, b: float, c: float) -> float
    Calculates volume based on three sides rectangular to each other.

    Parameter
    _________
    a -> length of side a, arbitrary positive float value
    b -> length of side b, arbitrary positive float value
    c -> length of side c, arbitrary positive float value

    Returns
    _______
    Volumetric product of the entered parameters as float
'''
```
