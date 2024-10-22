___
[[modules]]
#built-in 
___
## Good to know iterators from the module

```python
import itertools
```

### `product()`

Building the product of two or more Iterables:
```python
from itertools import product
  

# Deck of playing cards

suits = ['Diamonds', 'Hearts', 'Spades', 'Clubs']

ranks = list(range(2,11)) + ['Jack', 'Queen', 'King', 'Ace']

  

deck = [card for card in product(ranks, suits)]

  
print(deck)
# [(2, 'Diamonds'), (2, 'Hearts'), ..., ('Ace', 'Hearts'), ('Ace', 'Spades'), ('Ace', 'Clubs')]
```

### `combinations()`

Sidenote: A deck of 52 cards has 2598960 different five-card combinations.

```python
from itertools import combinations

choose_two = ['bubble-maker', 
			  'spoon', 
			  'sack of pebbles', 
			  'old sock', 
			  'fish friend']

  
pairs = [pair for pair in combinations(choose_two, 2)]

  
print(f'*There are {len(pairs)} possible pairs:*\n', pairs)
# *There are 10 possible pairs:*
# [('bubble-maker', 'spoon'), ('bubble-maker', 'sack of pebbles'), ..., 'fish friend'), ('old sock', 'fish friend')]
```