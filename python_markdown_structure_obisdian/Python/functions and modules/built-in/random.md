___
[[modules]]
#built-in 
___
```python
import random
```


### Weighted choice(s)

Mit zurücklegen:
```python
weights = [50, 50, 10, 1]

my_choices = ['10oHearts', '10oClubs', 'AceoSpades', 'Joker']

  

weighted_choices = random.choices(my_choices,weights, k=11)
 

print(weighted_choices) # ['10oHearts', '10oClubs', '10oClubs', '10oClubs', '10oClubs', '10oHearts', '10oClubs', '10oHearts', '10oHearts', '10oHearts', '10oClubs']
```
