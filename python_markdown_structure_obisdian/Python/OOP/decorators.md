___
[[functions]]
[[OOP]]
[[encapsulation]]
#pymagic 
#ZEN or syntactic sugar - yum!
___
Decorators are commands in python that start with an @ symbol. Decorators are used before
* regular functions (@function decorator), 
* classes (@class decorator)
* or class functions (methods) (@method decorator).

Function decorators add functionality to a function without modifying the base function.
More than one decorator can be added - or even the same decorator multiple times!
```python
import random


# create a function to decorate another function with

def get_lucky(func):

    def wrapper():

        print('*Hope you get lucky*')

        func()

    return wrapper

# A 'wrapper' function is necessary, otherwise the decorator will just execute the decorator function - but not the decorated.  


@get_lucky                         # decorator
def roll_dice():

    eyes = random.choices(range(1,7))

    for eye in eyes:

        print(f'\n*You rolled a {eye}*\n')

roll_dice() 

# *Hope you get lucky*

# *You rolled a 2*
```

Decorator functions with arguments - convention is to simply add `*args` & `**kwargs`:
```python
import random


# DECORATOR function

def get_lucky(func):

    def wrapper(*args, **kwargs):

        print('*Hope you get lucky*')

        func(*args, **kwargs)

    return wrapper

  

@get_lucky

def roll_dice(max_eyes):

    eyes = random.choices(range(1,max_eyes + 1))

    for eye in eyes:

        print(f'\n*You rolled a {eye}*\n')

  

roll_dice(20)
```

## Some good decorator functions to know

A `@timer`decorator function to add to a function to take its execution time:
```python
import time
 
  
# DECORATOR
def timer(func):

    def wrapper():

        t0 = time.time()

        func() # decorated function executed inbetween t0 and t1

        t1 = time.time()

        print(f'{func.__name__} took {t1-t0:.3f} seconds')

    return wrapper

  
  

@timer
def big_func():

    # Simulating running code...

    time.sleep(3.33) # seconds

  

big_func() # big_func took 3.340 seconds
```