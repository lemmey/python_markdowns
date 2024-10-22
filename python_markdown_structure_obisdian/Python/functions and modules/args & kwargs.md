___
[[functions]]
#decompose
___
Die Werte/Objekte, die in einer Funktion verarbeitet werden sind die Funktionsparameter. 
I.d.R. sind diese ausgeschrieben und werden so auch in der Funktion verwendet.
Der Standard-Parameter ist ein positioneller Parameter, da die Zuweisung der Parameter im Funktionsaufruf (call) auch der Reihenfolge der Parameter im Kopf der Funktion entspricht.

An dieser Stelle gibt es aber auch Alternativen, die zum Beispiel das Einbinden mehrerer Parameter einfacher machen. Schlüssel dazu ist der Python unpacking-Operator `*`. Das Zwischenprodukt eines entpackten Iterable ist ein Tuple.

## Unpacking with `*`
#decompose 
```python
a_string = 'Whabalabba-dub-dub'
print(*a_string) # W h a b a l a b b a - d u b - d u b

################ 

a_string = [*'Whabalabba-dub-dub']
print(a_string)
# ['W', 'h', 'a', 'b', 'a', 'l', 'a', 'b', 'b', 'a', '-', 'd', 'u', 'b', '-', 'd', 'u', 'b']
```

```python
numbers = [1, 2, 3]
print(*numbers) # 1 2 3
# The print() function takes every element of numbers as if they were single arguments

##############

def sum(a, b, c):
	print(a + b + c)


numbers = [1, 2, 3]

sum(*numbers) # 6

#############

def sum(*args):
    result = 0

    for arg in args:
        result += arg

    return result
  
  
nums1 = [1, 2, 3] # sum = 6
nums2 = [1, 2, 3] # sum = 6
nums3 = [1, 2, 3] # sum = 6

  
total = sum(*nums1, *nums2, *nums3)

print(total) # 18

############

a_list = [1, '2', 'what', 'oopsie', [5, 6]]
  

num, *strings, nums = a_list


print(num) # 1
print(strings) # '2' 'what' 'oopsie'
print(nums) # [5, 6]
```

## Arbitrary arguments (`*args`)
Einen asterisk vor eine argument variable in einer Funktion zu schreiben erlaubt es dieser Variablen einen beliebige Menge von positionellen Argumenten zuzuschreiben.

```python
def add(*nums):

	total = 0
	
	for num in nums:
		total += num
		
	return total


print(add(1, 2, 3, 4, 5, 6, 7, 8, 9)) # 45
print(add(*(x := i for i in range(10)))) # 45
```

```python
def pizza_order(size, *toppings):

    print("""You ordered a {} pizza with the toppings {}, {}.""".format(size, *toppings))

  
pizza_order("large", "pepperoni", "extra cheese")
# You ordered a large pizza with the toppings pepperoni, extra cheese.
```

## Keyword arguments (`**kwargs`)

Der `**kwargs` Placeholder steht für keyword-arguments. Wenn ausschließlich keywords übergeben werden, ist die positionelle Reihenfolge nicht mehr  wichtig. Im Hintergrund verhalten sich die `kwargs` wie ein Dictionary:

Note: `*args` , also positionelle Argumente müssen immer vor `**kwargs` stehen: sonst #SyntaxError 

```python
def f(*args, **kwargs):

    print(args) # Tuple

    print(kwargs) # Dictionary

  

f(1, 2, 3, a=1, b=2, c=3)

# args: (1, 2, 3)
# kwargs: {'a': 1, 'b': 2, 'c': 3}

##################################

def f(*args, **kwargs):

    for i, arg in enumerate(args):

        print(f'arg_{i}: {arg}') # Tuple

    for i, kwarg in enumerate(kwargs):

        print(f'kwarg_{i}: {kwarg}') # Dictionary

  

f(1, 2, 3, a=1, b=2, c=3)

# arg_0: 1
# arg_1: 2
# arg_2: 3
# kwarg_0: a
# kwarg_1: b
# kwarg_2: c
```