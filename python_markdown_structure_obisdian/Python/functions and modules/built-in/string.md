___
[[modules]]
#built-in 
___

```python
import string
```

Contents:
```python

```

Applications:
```python
import string

# Generate lower case English letters
def letters(): # generator function
	for character in string.ascii_lowercase:
		yield character

lower_case_letters = letters()


for letter in lower_case_letters:
	print(letter, end=' ')

# a b c d e f g h i j k l m n o p q r s t u v w x y z 
```