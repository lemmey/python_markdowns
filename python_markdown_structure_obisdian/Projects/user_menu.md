___
[[python_projects]]
#project
#input
___
### Calculator example

Klassisch, mit infinite-while- & if-Block:
```python
# Make function choices

def add():

    num1, num2 = input('Please enter a number and one to add\n>').split()

    print(int(num1) + int(num2), '\n')

def substract():

    num1, num2 = input('Please enter a number and one to substract\n>').split()

    print(int(num1) - int(num2), '\n')

def multiply():

    num1, num2 = input('Please enter a number and one to multiply by\n>').split()

    print(int(num1) * int(num2), '\n')

def divide():

    num1, num2 = input('Please enter a number and one to divide by\n>').split()

    print(int(num1) / int(num2), '\n')

  

def menu():

    while True:

        print('''
            1. Add
            2. Substract
            3. Multiply
            4. Divide

            Or type 'x' to cancel

            ''')

        choice = input('Choose an option from them menu\n>')

        if choice == '1':
            add()

        elif choice == '2':
            substract()

        elif choice == '3':
            multiply()

        elif choice == '4':
            divide()

        elif choice.lower() == 'x':
            break

        else:
            print('Please enter a valid option')
            menu()

  

if __name__ == '__main__':
    menu()
```

### Wählbare User-Optionen aus einem Iterable

```python
def get_option(available_options: list[str], type_option: str):

    while True:

        print('Your Options:')

        for option in available_options:

            print('*', option)

        user_option = input(f'\nChoose a {type_option}\n>')

        if user_option in available_options:

            return user_option

        else:

            print('\nEnter a valid option\n')

  

fruits = ['Anapple', 'Banerry', 'Cocopear']

user_fruit = get_option(fruits, 'Fantastic fruit')

  
if user_fruit:

    print(f'\nYour {user_fruit} will arrive shortly')
```

### Snack Menu

```python
menu = {
        'Pizzza': 3.00,
        'Frizzle-sticks': 2.50,
        'Crackers Royale': 4.50,
        'Jolly Juice': 2.00,
        'Just Soda': 1.50,
}

  

shopping_cart = []

total = 0.0

  
print('------- M e n u --------')

for product, price in menu.items():

    print(f'{product:10}: €{price:.2f}')

print('------------------------')

  

while True:

    snack = input('select a snack (q to quit)')

    if snack.lower() == 'q':

        break

    elif menu.get(snack) is not None:

        shopping_cart.append(snack)

  

print('------ Your order ------')

for food in shopping_cart:

    total += menu.get(food)

    print(food, end=' ')

  

print(f'\nTotal is: €{total:.2f}')
```
### Andere Beispiele

```python
import time

# Setup continuous user menu

def get_menu_input():

    user_options = ('1', '2', '3')

    while True:

        print('#'*79)

        print('''  
            **User Menu**
            1 = print
            2 = save
            3 = exit
            ''')

        user_input = input('Please choose an option from the list\n>')

        if user_input in user_options:

            return user_input # return also breaks out of the loop/function

        else:

            print('\nOption not available')


# Processing UI

while True:

    user_input = get_menu_input()

    exit_options = ('exit', 'exit()',
                    'y', 'yes',
                    'q', 'quit', 'quit()',
                    'c', 'cancel')

    if user_input == '1':

        print('Printing...')

        time.sleep(5)

        print('**Results**\n')

    elif user_input == '2':

        print('Saving...')

        time.sleep(5)

        print('**Results**\n')

    elif user_input == '3':

        print('Exiting...')

        exiting = input('Please confirm\n')

        if exiting.lower() in exit_options:

            print('Confirmed\nExiting now...\n')

            time.sleep(5)

            exit()
```

