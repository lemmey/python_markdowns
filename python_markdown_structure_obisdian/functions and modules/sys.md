___
[[modules]]
#built-in 
___

### `sys.getrefcount`
```python
import sys


a = "Mine"
b = a
c = a
d = a

print(sys.getrefcount(a)) # 4
```