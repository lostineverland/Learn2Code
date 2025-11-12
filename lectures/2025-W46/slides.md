  # Python Basics & Data Structures Part 3

  - Open Codespaces
  - https://github.com/codespaces/

notes:
- last week we talked about lists
- This week we're going to talk tuples & dicts

    ---slide---
  ## Tuples: Immutable Sequences

  - Tuples are like lists, but **cannot be changed** after creation.
  - We refer to them as "immutable"

    ---slide---
  ### Creating Tuples

  ```python
  # Parentheses (usually)
  point = (10, 20)
  rgb_color = (255, 128, 0)

  # Without parentheses (tuple packing)
  patient = "P001", "John Smith", 45
  ```
notes:
- use parentheses instead of brackets
- notice, however, that just adding commas also results in a tuple

    ---slide---
  ```python
  # Single item tuple (needs comma!)
  single = 42,        # Tuple
  single = (42,)      # Tuple
  not_tuple = (42)    # Just a number in parentheses

  # Empty tuple
  empty = ()
  ```
notes:
- notice not_tuple & empty

    ---slide---
  ### Tuple Operations

  ```python
  point = (10, 20, 30)

  # Indexing (same as lists)
  point[0]        # 10
  point[-1]       # 30

  # Slicing (same as lists)
  point[1:]       # (20, 30)

  # Length
  len(point)      # 3
  ```
notes:
- most operations are the same
- missing mutation operations of course
- tuples connote a "lazy" operation (vs. "eager")

    ---slide---
  ## Dictionaries: Key-Value Pairs

  - Dictionaries store data as key-value pairs
  - Think of an actual dictionary: word (key) → definition (value)
  - We refer to this as a "lookup"
  - an index is also a dictionary

    ---slide---
  ### Creating Dictionaries

  ```python
  # Empty dictionary
  patient = {}

  # Multi-line for readability
  patient = {
      "id": "P001",
      "name": "John Smith",
      "age": 45,
      "diagnosis": "Type 2 Diabetes",
  }
  ```
notes:
- notice the trailing commas

    ---slide---
  ```python
  project = dict([
      ('name', "Office Complex"),
      ('area', 45000),
      ('floors', 12),
      ('cost', 11250000),
  ])
  ```
notes:
- curly braces is the syntactic-sugar for dictionaries
- these are pairs
- notice that there is only one argument to this function
- a list of tuples

    ---slide---
  ```python
  project = dict(
      name="Office Complex",
      area=45000,
      floors=12,
      cost=11250000,
  )
  ```
notes:
- these are keyword arguments to the `dict` function
- in this form, the key part must be a string

    ---slide---
  ### Accessing Values

  ```python
  patient = {
      "id": "P001",
      "name": "John Smith",
      "age": 45
  }

  # Get value by key
  patient["name"]         # "John Smith"
  patient["age"]          # 45
  ```
notes:
- idiomatic way to access, just like lists or tuples

    ---slide---
  ```python
  # Safe access (won't error if key missing)
  patient.get("name")     # "John Smith"
  patient.get("email")    # None
  patient.get("email", "No email")  # "No email" (default value)
  ```

notes:
- the default value here is really useful
- it doesn't throw an error

    ---slide---
  ### Modifying Dictionaries

  ```python
  patient = {"id": "P001", "name": "John Smith"}

  # Add new key-value pair
  patient["age"] = 45
  patient["diagnosis"] = "Type 2 Diabetes"

  # Update existing value
  patient["age"] = 46

  # Update multiple items
  patient.update({"age": 46, "email": "john@example.com"})
  ```
notes:
- very much like lists
- these data structures are very much alike

    ---slide---
  ```python
  # Remove key-value pair
  del patient["email"]

  # Remove and return value
  age = patient.pop("age")

  # Remove and return last inserted item (Python 3.7+)
  last_item = patient.popitem()

  # Clear all items
  patient.clear()
  ```
notes:
- not much is new here

    ---slide---
  ### Dictionary Operations

  ```python
  patient = {
      "id": "P001",
      "name": "John Smith",
      "age": 45,
      "diagnosis": "Type 2 Diabetes"
  }

  # Check if key exists
  "name" in patient           # True
  "email" in patient          # False
  ```
notes:
- the keys behave like the items in a list
- we'll see that further when we start doing loops and iterations

    ---slide---
  ```python
  # Get all keys
  patient.keys()              # dict_keys(['id', 'name', 'age', 'diagnosis'])

  # Get all values
  patient.values()            # dict_values(['P001', 'John Smith', 45, 'Type 2 Diabetes'])

  # Get all key-value pairs
  patient.items()             # dict_items([('id', 'P001'), ('name', 'John Smith'), ...])

  # Number of items
  len(patient)                # 4
  ```
notes:
- order is preserved as of Python 3.6
- the order of keys() matches the order of values()

