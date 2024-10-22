___
[[itertools]]
[[dunder_methods]]
#abc
___
### What makes an python object an Iterable? 

Note, a sequence is an Iterable + an order - e.g. an indexed list. Each element in a sequence has a relative position to all other elements in that sequence. There are un-ordered iterables.

#TypeError 
```python
for x in something:
	pass

# 'something' in this case can only be an Iterable ...
# as the for-loop will be iterating over its elements. Otherwise TypeError
```
___

The key to iteration lies in two Special-Methods #dunder 

* `__iter__` for the Iterable.
* `__next__` the Iterator that inherits from the Iterable.

#StopIteration Exception
```python
greetings = 'Hello'
  

my_iterator =  greetings.__iter__()
  

print(my_iterator.__next__()) # H
print(my_iterator.__next__()) # e
print(my_iterator.__next__()) # l
print(my_iterator.__next__()) # l
print(my_iterator.__next__()) # o
# print(my_iterator.__next__()) # StopIteration
```
___
### The mechanics of iteration or how to appreciate the for-loop!

#loop 
```python
fellows = ('Gandalf', 'Aragorn', 'Legolas')

# for fellow in fellows:
# 	 print(fellow)


# as Raw-Iterable - uff
iterable = iter(fellows)

while True:
	try:
		fellow = next(iterable)
		print(fellow)
	except StopIteration:
		break

# Gandalf
# Aragorn
# Legolas
```
