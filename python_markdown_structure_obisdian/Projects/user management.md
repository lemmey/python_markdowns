___
[[python_projects]]
#project 
___

## With a UserClass

```python
import datetime
  

class User:

    """For members of the website. Storing only user name and birthday.

    ...

    Requires:

    module: datetime

    """

    def __init__(self, full_name: str, birthday:str) -> None:

        self.name = full_name

        self.bday = birthday    # yyyymmdd

        # Extract the name

        name_split = full_name.split(' ')

        self.first_name = name_split[0]

        self.last_name = name_split[-1]

    def age(self):

        """Returns user age in years by substracting current year from birth

        ...

        """

        today = datetime.date.today()

        u_yyyy = int(self.bday[0:4])

        u_mm = int(self.bday[4:6])

        u_dd = int(self.bday[6:])

        u_DateTimeObject = datetime.date(u_yyyy, u_mm, u_dd) # user dob

        age_in_days = (today - u_DateTimeObject).days

        age_in_years = age_in_days / 365

        return int(age_in_years)

add_user = User('Leonard Meyer', '19910511')

print(user.age()) #33
```

Add user instance data to a storage:
```python

```

#chatgpt 
```python
class DataManager:

    def __init__(self):
        # Initialize an empty list to store the data
        self.data = []

    # Method to add a new record
    def add_record(self, name, age):
        self.data.append({'name': name, 'age': age})

    # Method to update a record by name
    def update_record(self, name, new_age):
        for record in self.data:
            if record['name'] == name:
                record['age'] = new_age
                break

    # Method to remove a record by name
    def remove_record(self, name):
        self.data = [record for record in self.data if record['name'] != name]

    # Method to retrieve the entire data
    def get_all_data(self):
        return self.data

    # Method to find a specific record by name
    def find_record(self, name):
        for record in self.data:
            if record['name'] == name:
                return record
        return None

```

```python
# Create an instance of DataManager
manager = DataManager()

# Add records
manager.add_record('Alice', 30)
manager.add_record('Bob', 25)
manager.add_record('Charlie', 35)

# Display all data
print("Initial data:")
print(manager.get_all_data())

# Update a record
manager.update_record('Bob', 26)
print("\nData after updating Bob's age:")
print(manager.get_all_data())

# Remove a record
manager.remove_record('Charlie')
print("\nData after removing Charlie:")
print(manager.get_all_data())

# Find a specific record
record = manager.find_record('Alice')
print("\nSearch for Alice's record:")
print(record)
```