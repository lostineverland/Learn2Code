# Python Basics & Data Structures

## Why Python? Why Now?

Python is one of the most popular programming languages in the world, and for good reason:

**Python is:**
- **Readable**: Looks almost like English
- **Practical**: Real results in minutes, not months
- **Powerful**: From simple scripts to AI systems
- **In-demand**: Top 3 most wanted programming skill

---

## Your First Python Program

Let's start with the tradition:

```python
print("Hello, World!")
```

That's it. Run this, and Python says hello back. No compilation, no ceremony, just results.

**Try it now:**
1. Open your terminal
2. Type `python3` (or `python`)
3. Type the line above
4. Press Enter

You just ran your first Python program!

**Exit the Python shell:**
```python
exit()
```

Or press `Ctrl+D` (Mac/Linux) or `Ctrl+Z` then Enter (Windows).

---

## Learning Objectives

By the end of this lecture, you'll be able to:
- Write and run Python programs
- Store data in variables
- Work with different data types (numbers, strings, booleans)
- Use lists to manage collections of data
- Use dictionaries to organize data with labels
- Choose the right data structure for your problem
- Apply these skills to real problems in your field

---

## The Python Interpreter: Your Playground

Python has two modes:

**1. Interactive Mode (REPL - Read-Eval-Print-Loop)**
```bash
$ python3
>>> 2 + 2
4
>>> print("I'm programming!")
I'm programming!
```

Perfect for:
- Testing ideas
- Quick calculations
- Learning and exploring

**2. Script Mode**
Save code in a file (e.g., `analysis.py`) and run it:
```bash
python3 analysis.py
```

Perfect for:
- Reusable programs
- Complex logic
- Sharing with others

We'll use both today!

---

## Python Fundamentals

### Variables: Storing Information

Variables are containers for data. Think of them as labeled boxes.

```python
# Assignment - putting data in a box
name = "Alice"
age = 34
temperature = 98.6
is_patient = True
```

**Rules for variable names:**
- Start with letter or underscore: `patient_id`, `_temp`
- Can contain letters, numbers, underscores: `patient_123`
- Case-sensitive: `Name` and `name` are different
- Can't use Python keywords: `if`, `for`, `while`, etc.

**Good practices:**
```python
# Good - descriptive names
patient_count = 150
glucose_level = 95

# Bad - unclear names
pc = 150
gl = 95
```

### Python's Core Data Types

#### Numbers

**Integers (whole numbers):**
```python
patients = 42
year = 2024
temperature = -5
```

**Floats (decimals):**
```python
price = 99.99
glucose = 95.5
pi = 3.14159
```

**Basic math:**
```python
# Addition
10 + 5        # 15

# Subtraction
10 - 5        # 5

# Multiplication
10 * 5        # 50

# Division (always returns float)
10 / 5        # 2.0
10 / 3        # 3.3333...

# Integer division (no remainder)
10 // 3       # 3

# Remainder (modulo)
10 % 3        # 1

# Exponentiation
2 ** 3        # 8 (2 to the power of 3)
```

#### Strings

Strings are text - sequences of characters.

```python
# Single or double quotes work the same
name = "Alice"
name = 'Alice'

# Multi-line strings use triple quotes
description = """This is a longer
text that spans
multiple lines."""

# String concatenation
first_name = "John"
last_name = "Smith"
full_name = first_name + " " + last_name  # "John Smith"

# String formatting (modern way)
age = 34
message = f"Patient {full_name} is {age} years old"
print(message)  # Patient John Smith is 34 years old
```

**Common string operations:**
```python
text = "Hello, World!"

# Length
len(text)           # 13

# Case conversion
text.upper()        # "HELLO, WORLD!"
text.lower()        # "hello, world!"

# Check contents
text.startswith("Hello")   # True
text.endswith("!")         # True
"World" in text           # True

# Replace
text.replace("World", "Python")  # "Hello, Python!"

# Split into list
text.split(", ")    # ["Hello", "World!"]
```

#### Booleans

True or False - that's it!

```python
is_valid = True
is_expired = False

# Comparison operators
5 > 3         # True
5 < 3         # False
5 == 5        # True (equal)
5 != 3        # True (not equal)
5 >= 5        # True (greater than or equal)

# Logical operators
True and False    # False
True or False     # True
not True          # False

# Practical example
age = 34
is_adult = age >= 18           # True
can_vote = age >= 18 and age < 120  # True
```

### Type Checking and Conversion

```python
# Check type
type(42)          # <class 'int'>
type(3.14)        # <class 'float'>
type("hello")     # <class 'str'>
type(True)        # <class 'bool'>

# Convert between types
int("42")         # 42
float("3.14")     # 3.14
str(42)           # "42"
bool(1)           # True
bool(0)           # False
```

---

<!-- Lecture 3 materials end here -->

## Domain-Specific Examples: Variables & Basic Types

### Medicine
```python
patient_id = "P12345"
systolic_bp = 120
diastolic_bp = 80
glucose_level = 95.5
is_diabetic = False
diagnosis = "Type 2 Diabetes"

# Blood pressure category
bp_high = systolic_bp >= 140 or diastolic_bp >= 90
print(f"Patient {patient_id} has high blood pressure: {bp_high}")
```

### Finance
```python
account_number = "ACC-1001"
balance = 12500.50
interest_rate = 0.025
transaction_count = 47
is_active = True

# Calculate interest
monthly_interest = balance * (interest_rate / 12)
print(f"Monthly interest: ${monthly_interest:.2f}")
```

### Architecture
```python
project_name = "Downtown Office Complex"
total_area = 45000  # square feet
floors = 12
cost_per_sqft = 250.00
is_residential = False

# Calculate total cost
total_cost = total_area * cost_per_sqft
print(f"Project {project_name} estimated cost: ${total_cost:,.2f}")
```

### Biology
```python
species_name = "Bald Eagle"
observation_count = 15
avg_wingspan = 2.1  # meters
is_endangered = False
habitat = "Coastal and inland waters"

# Scientific observation
print(f"Observed {observation_count} {species_name} individuals")
print(f"Average wingspan: {avg_wingspan}m")
```

---

## Try It Yourself: Basic Python

Open Python and try these:

```python
# 1. Create variables for yourself
your_name = "Your Name Here"
your_age = 25
your_field = "Your Field"

# 2. Print a formatted message
print(f"Hi, I'm {your_name}, I'm {your_age}, and I work in {your_field}")

# 3. Do some calculations
hours_per_week = 40
weeks_per_year = 52
total_hours = hours_per_week * weeks_per_year
print(f"You work {total_hours} hours per year")

# 4. Test some comparisons
print(total_hours > 2000)
print(your_age >= 18)
```

---

## Lists: Collections of Data

Lists are ordered collections that can hold multiple items. Think of them as a shopping list or a to-do list.

### Creating Lists

```python
# Empty list
patients = []

# List with data
ages = [25, 34, 45, 52, 61]
names = ["Alice", "Bob", "Carol", "David"]
mixed = [1, "hello", 3.14, True]  # Can mix types (but usually don't)

# Multi-line for readability
diagnoses = [
    "Type 2 Diabetes",
    "Hypertension",
    "Asthma",
    "COPD"
]
```

### Accessing List Items

```python
fruits = ["apple", "banana", "cherry", "date"]

# Indexing (starts at 0!)
fruits[0]      # "apple"
fruits[1]      # "banana"
fruits[3]      # "date"

# Negative indexing (from the end)
fruits[-1]     # "date" (last item)
fruits[-2]     # "cherry" (second to last)

# Length
len(fruits)    # 4
```

### Slicing: Getting Multiple Items

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Syntax: list[start:end]  (end is exclusive)
numbers[2:5]     # [2, 3, 4]
numbers[:3]      # [0, 1, 2] (start from beginning)
numbers[7:]      # [7, 8, 9] (go to end)
numbers[:]       # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] (copy entire list)

# Step
numbers[::2]     # [0, 2, 4, 6, 8] (every other item)
numbers[1::2]    # [1, 3, 5, 7, 9] (every other, starting at 1)
numbers[::-1]    # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0] (reverse!)
```

### Modifying Lists

```python
fruits = ["apple", "banana", "cherry"]

# Change an item
fruits[1] = "blueberry"
# fruits is now ["apple", "blueberry", "cherry"]

# Add to end
fruits.append("date")
# ["apple", "blueberry", "cherry", "date"]

# Add multiple items
fruits.extend(["elderberry", "fig"])
# ["apple", "blueberry", "cherry", "date", "elderberry", "fig"]

# Insert at specific position
fruits.insert(1, "apricot")
# ["apple", "apricot", "blueberry", "cherry", "date", "elderberry", "fig"]

# Remove by value
fruits.remove("blueberry")

# Remove by index
del fruits[0]

# Remove and return last item
last = fruits.pop()

# Remove and return item at index
second = fruits.pop(1)

# Clear entire list
fruits.clear()
```

### Useful List Operations

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]

# Sort (modifies original)
numbers.sort()
# numbers is now [1, 1, 2, 3, 4, 5, 6, 9]

# Sort descending
numbers.sort(reverse=True)

# Get sorted copy (doesn't modify original)
sorted_nums = sorted(numbers)

# Reverse
numbers.reverse()

# Count occurrences
numbers.count(1)      # 2

# Find index
numbers.index(5)      # 4 (position of 5)

# Check if item exists
5 in numbers          # True
10 in numbers         # False
```
<!-- Lecture 4 materials end here -->

### List Comprehensions (Quick List Creation)

A powerful Python feature for creating lists:

```python
# Traditional way
squares = []
for i in range(10):
    squares.append(i ** 2)

# List comprehension way
squares = [i ** 2 for i in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
even_squares = [i ** 2 for i in range(10) if i % 2 == 0]
# [0, 4, 16, 36, 64]

# Convert temperatures from C to F
celsius = [0, 10, 20, 30, 40]
fahrenheit = [(temp * 9/5) + 32 for temp in celsius]
# [32.0, 50.0, 68.0, 86.0, 104.0]
```

---

## Domain Examples: Lists

### Medicine - Patient Ages
```python
patient_ages = [34, 45, 28, 52, 61, 39, 48, 55]

# Statistics
average_age = sum(patient_ages) / len(patient_ages)
print(f"Average patient age: {average_age:.1f}")

# Find patients over 50
elderly = [age for age in patient_ages if age > 50]
print(f"Patients over 50: {len(elderly)}")

# Sort by age
patient_ages.sort()
print(f"Youngest: {patient_ages[0]}, Oldest: {patient_ages[-1]}")
```

### Finance - Transaction Amounts
```python
transactions = [1500.50, -50.00, 2500.00, -125.75, 3000.00, -200.00]

# Separate credits and debits
credits = [t for t in transactions if t > 0]
debits = [t for t in transactions if t < 0]

# Totals
total_credits = sum(credits)
total_debits = sum(debits)
net = total_credits + total_debits

print(f"Total credits: ${total_credits:.2f}")
print(f"Total debits: ${abs(total_debits):.2f}")
print(f"Net: ${net:.2f}")
```

### Biology - Species Observations
```python
observations = [15, 8, 22, 19, 31, 12, 27, 18]

# Analysis
total_observed = sum(observations)
max_count = max(observations)
min_count = min(observations)
avg_count = sum(observations) / len(observations)

print(f"Total observations: {total_observed}")
print(f"Peak observation: {max_count}")
print(f"Average per day: {avg_count:.1f}")
```

---

## Tuples: Immutable Sequences

Tuples are like lists, but **cannot be changed** after creation. Use them for data that shouldn't be modified.

### Creating Tuples

```python
# Parentheses (usually)
point = (10, 20)
rgb_color = (255, 128, 0)

# Without parentheses (tuple packing)
patient = "P001", "John Smith", 45

# Single item tuple (needs comma!)
single = (42,)      # Tuple
not_tuple = (42)    # Just a number in parentheses

# Empty tuple
empty = ()
```

### Why Use Tuples?

**1. Data Integrity**
```python
# Coordinates shouldn't change
location = (40.7128, -74.0060)  # NYC latitude, longitude
# location[0] = 50  # ERROR! Can't modify tuple
```

**2. Return Multiple Values from Functions**
```python
def get_patient_info():
    return "P001", "John Smith", 45

patient_id, name, age = get_patient_info()  # Tuple unpacking
```

**3. Dictionary Keys (lists can't be keys, tuples can)**
```python
# Map coordinates to locations
locations = {
    (40.7128, -74.0060): "New York",
    (34.0522, -118.2437): "Los Angeles"
}
```

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

# Check membership
20 in point     # True

# Count and index
point.count(20)     # 1
point.index(30)     # 2

# Unpacking
x, y, z = point
print(f"x={x}, y={y}, z={z}")
```

### Tuple vs List: When to Use What

| Use List When | Use Tuple When |
|---------------|----------------|
| Data might change | Data is fixed |
| Adding/removing items | Size is constant |
| Similar items (all ages, all names) | Related but different items (name, age, id) |
| Order matters and changes | Order represents structure |

**Examples:**
```python
# List - collection of similar items
patient_ages = [34, 45, 28, 52]  # Might add more ages

# Tuple - fixed structure
patient_record = ("P001", "John Smith", 45, "Type 2 Diabetes")
```

---

## Dictionaries: Key-Value Pairs

Dictionaries store data as key-value pairs. Think of an actual dictionary: word (key) → definition (value).

### Creating Dictionaries

```python
# Empty dictionary
patient = {}

# With data
patient = {
    "id": "P001",
    "name": "John Smith",
    "age": 45,
    "diagnosis": "Type 2 Diabetes"
}

# Multi-line for readability
project = {
    "name": "Office Complex",
    "area": 45000,
    "floors": 12,
    "cost": 11250000
}
```

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

# Safe access (won't error if key missing)
patient.get("name")     # "John Smith"
patient.get("email")    # None
patient.get("email", "No email")  # "No email" (default value)
```

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

# Remove key-value pair
del patient["email"]

# Remove and return value
age = patient.pop("age")

# Remove and return last inserted item (Python 3.7+)
last_item = patient.popitem()

# Clear all items
patient.clear()
```

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

# Get all keys
patient.keys()              # dict_keys(['id', 'name', 'age', 'diagnosis'])

# Get all values
patient.values()            # dict_values(['P001', 'John Smith', 45, 'Type 2 Diabetes'])

# Get all key-value pairs
patient.items()             # dict_items([('id', 'P001'), ('name', 'John Smith'), ...])

# Number of items
len(patient)                # 4

# Loop through dictionary
for key in patient:
    print(f"{key}: {patient[key]}")

# Better way to loop
for key, value in patient.items():
    print(f"{key}: {value}")
```

### Nested Dictionaries

```python
# Dictionary of patients
patients = {
    "P001": {
        "name": "John Smith",
        "age": 45,
        "diagnosis": "Type 2 Diabetes"
    },
    "P002": {
        "name": "Mary Johnson",
        "age": 67,
        "diagnosis": "Hypertension"
    }
}

# Access nested data
patients["P001"]["name"]        # "John Smith"
patients["P002"]["age"]         # 67

# Add new patient
patients["P003"] = {
    "name": "Bob Williams",
    "age": 34,
    "diagnosis": "Asthma"
}
```

---

## Domain Examples: Dictionaries

### Medicine - Patient Record
```python
patient = {
    "id": "P001",
    "name": "John Smith",
    "age": 45,
    "blood_pressure": {"systolic": 120, "diastolic": 80},
    "glucose": 95.5,
    "medications": ["Metformin", "Lisinopril"],
    "is_diabetic": True
}

# Access nested data
print(f"Patient: {patient['name']}, Age: {patient['age']}")
print(f"BP: {patient['blood_pressure']['systolic']}/{patient['blood_pressure']['diastolic']}")
print(f"Medications: {', '.join(patient['medications'])}")
```

### Finance - Account Information
```python
account = {
    "account_number": "ACC-1001",
    "holder": "Jane Doe",
    "balance": 12500.50,
    "interest_rate": 0.025,
    "type": "Savings",
    "transactions": [
        {"date": "2024-01-15", "amount": 1000, "type": "deposit"},
        {"date": "2024-01-20", "amount": -250, "type": "withdrawal"}
    ]
}

# Calculate interest
monthly_interest = account["balance"] * (account["interest_rate"] / 12)
print(f"Account {account['account_number']}: ${account['balance']:.2f}")
print(f"Monthly interest: ${monthly_interest:.2f}")
```

### Architecture - Project Details
```python
project = {
    "id": "PRJ001",
    "name": "Downtown Office Complex",
    "client": "Tech Corp",
    "specs": {
        "area": 45000,
        "floors": 12,
        "cost_per_sqft": 250
    },
    "status": "In Progress",
    "team": ["Sarah Chen", "Mike Rodriguez"]
}

# Calculate total cost
total_cost = project["specs"]["area"] * project["specs"]["cost_per_sqft"]
print(f"Project: {project['name']}")
print(f"Total estimated cost: ${total_cost:,.2f}")
print(f"Project team: {', '.join(project['team'])}")
```

<!-- Lecture 5 materials end here -->
---

## Sets: Unique Collections

Sets are unordered collections of **unique** items. No duplicates allowed! Great for membership testing and removing duplicates.

### Creating Sets

```python
# Empty set (must use set(), not {})
empty = set()

# With data
unique_ages = {25, 34, 45, 52, 61}
diagnoses = {"Diabetes", "Hypertension", "Asthma"}

# From a list (automatically removes duplicates)
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique_numbers = set(numbers)  # {1, 2, 3, 4}
```

### Set Operations

```python
fruits = {"apple", "banana", "cherry"}

# Add item
fruits.add("date")

# Add multiple items
fruits.update(["elderberry", "fig"])

# Remove item (error if not found)
fruits.remove("banana")

# Remove item (no error if not found)
fruits.discard("banana")

# Remove and return arbitrary item
item = fruits.pop()

# Clear all items
fruits.clear()

# Length
len(fruits)

# Check membership (VERY FAST)
"apple" in fruits      # True
"zebra" in fruits      # False
```

### Set Mathematics

```python
# Two sets of patients
diabetic = {"P001", "P004", "P007", "P015"}
hypertensive = {"P002", "P004", "P008", "P015", "P017"}

# Union (all patients with either condition)
either = diabetic | hypertensive
# or: diabetic.union(hypertensive)
# {"P001", "P002", "P004", "P007", "P008", "P015", "P017"}

# Intersection (patients with BOTH conditions)
both = diabetic & hypertensive
# or: diabetic.intersection(hypertensive)
# {"P004", "P015"}

# Difference (diabetic but not hypertensive)
only_diabetic = diabetic - hypertensive
# or: diabetic.difference(hypertensive)
# {"P001", "P007"}

# Symmetric difference (one condition but not both)
only_one = diabetic ^ hypertensive
# or: diabetic.symmetric_difference(hypertensive)
# {"P001", "P002", "P007", "P008", "P017"}

# Subset check
small_set = {"P001", "P004"}
small_set.issubset(diabetic)    # True

# Superset check
diabetic.issuperset(small_set)  # True
```

### Common Use Cases

**1. Remove duplicates:**
```python
observations = [15, 8, 22, 15, 19, 8, 31, 12, 22, 27, 18]
unique_counts = set(observations)
print(f"Unique observation counts: {sorted(unique_counts)}")
```

**2. Fast membership testing:**
```python
# List: slow for large collections
valid_ids = ["P001", "P002", ..., "P9999"]  # 10,000 items
"P5000" in valid_ids  # Checks every item (slow)

# Set: very fast
valid_ids = {"P001", "P002", ..., "P9999"}  # 10,000 items
"P5000" in valid_ids  # Instant lookup (fast)
```

**3. Find common/unique elements:**
```python
site_a_species = {"Bald Eagle", "Red Fox", "Deer"}
site_b_species = {"Red Fox", "Wolf", "Bear", "Deer"}

# Species at both sites
common = site_a_species & site_b_species
# {"Red Fox", "Deer"}

# Species only at site A
unique_a = site_a_species - site_b_species
# {"Bald Eagle"}
```

---

## Choosing the Right Data Structure

| Data Structure | Use When | Example |
|----------------|----------|---------|
| **List** | Order matters, duplicates OK, need to modify | Patient ages: [34, 45, 28, 52] |
| **Tuple** | Fixed structure, shouldn't change | Patient record: ("P001", "John", 45) |
| **Dictionary** | Need key-value lookup | Patient info: {"id": "P001", "name": "John"} |
| **Set** | Need unique items, fast membership test | Unique diagnoses: {"Diabetes", "Hypertension"} |

### Decision Flowchart

```
Need to store data?
│
├─ Single value? → Variable (name = "John")
│
└─ Multiple values?
   │
   ├─ Need key-value pairs? → Dictionary
   │
   └─ Just values?
      │
      ├─ Only unique values? → Set
      │
      └─ Can have duplicates?
         │
         ├─ Can modify? → List
         │
         └─ Fixed? → Tuple
```

---

## Common Pitfalls and How to Avoid Them

### 1. List Index Out of Range

```python
ages = [25, 34, 45]

# Wrong
ages[3]  # ERROR! Only indices 0, 1, 2 exist

# Right - check length first
if len(ages) > 3:
    print(ages[3])
else:
    print("Index doesn't exist")
```

### 2. Modifying Lists While Iterating

```python
numbers = [1, 2, 3, 4, 5]

# Wrong
for num in numbers:
    if num % 2 == 0:
        numbers.remove(num)  # Causes skipping!

# Right - iterate over a copy
for num in numbers[:]:  # [:] creates a copy
    if num % 2 == 0:
        numbers.remove(num)

# Better - use list comprehension
numbers = [num for num in numbers if num % 2 != 0]
```

### 3. Dictionary KeyError

```python
patient = {"id": "P001", "name": "John"}

# Wrong
print(patient["age"])  # ERROR! Key doesn't exist

# Right
print(patient.get("age", "Age not recorded"))
```

### 4. Mutable Default Arguments

```python
# Wrong
def add_patient(patients=[]):
    patients.append("P001")
    return patients

# This has surprising behavior!
add_patient()  # ["P001"]
add_patient()  # ["P001", "P001"]  # Oops!

# Right
def add_patient(patients=None):
    if patients is None:
        patients = []
    patients.append("P001")
    return patients
```

### 5. String vs Number Confusion

```python
# Wrong
age = "45"
next_year = age + 1  # ERROR! Can't add number to string

# Right
age = int("45")
next_year = age + 1  # 46

# Or
age = "45"
next_year = int(age) + 1  # 46
```

### 6. Forgetting List Methods Modify In-Place

```python
numbers = [3, 1, 4, 1, 5]

# Wrong expectation
sorted_nums = numbers.sort()
print(sorted_nums)  # None (sort() returns None!)

# Right
numbers.sort()  # Modifies numbers in place
print(numbers)  # [1, 1, 3, 4, 5]

# Or use sorted() for a new list
sorted_nums = sorted(numbers)
```

---

## Hands-On Exercises

### Exercise 1: Patient Management

Create a program to manage patient data:

```python
# Create list of patient ages
ages = [34, 45, 28, 52, 61, 39, 48, 55, 67, 44]

# 1. Calculate average age
# 2. Find youngest and oldest
# 3. Count patients over 50
# 4. Create list of "Adult" or "Senior" (50+ is senior)

# Your code here
```

<details>
<summary>Solution</summary>

```python
ages = [34, 45, 28, 52, 61, 39, 48, 55, 67, 44]

# 1. Average
average = sum(ages) / len(ages)
print(f"Average age: {average:.1f}")

# 2. Youngest and oldest
youngest = min(ages)
oldest = max(ages)
print(f"Youngest: {youngest}, Oldest: {oldest}")

# 3. Count over 50
over_50 = len([age for age in ages if age > 50])
print(f"Patients over 50: {over_50}")

# 4. Categorize
categories = ["Senior" if age >= 50 else "Adult" for age in ages]
print(categories)
```
</details>

### Exercise 2: Transaction Analysis

Analyze financial transactions:

```python
transactions = [
    {"date": "2024-01-15", "amount": 1000, "type": "deposit"},
    {"date": "2024-01-16", "amount": -250, "type": "withdrawal"},
    {"date": "2024-01-17", "amount": 1500, "type": "deposit"},
    {"date": "2024-01-18", "amount": -100, "type": "withdrawal"},
    {"date": "2024-01-19", "amount": 2000, "type": "deposit"}
]

# 1. Calculate total deposits
# 2. Calculate total withdrawals
# 3. Find largest transaction (by absolute amount)
# 4. Count number of each transaction type

# Your code here
```

<details>
<summary>Solution</summary>

```python
transactions = [
    {"date": "2024-01-15", "amount": 1000, "type": "deposit"},
    {"date": "2024-01-16", "amount": -250, "type": "withdrawal"},
    {"date": "2024-01-17", "amount": 1500, "type": "deposit"},
    {"date": "2024-01-18", "amount": -100, "type": "withdrawal"},
    {"date": "2024-01-19", "amount": 2000, "type": "deposit"}
]

# 1. Total deposits
deposits = [t["amount"] for t in transactions if t["amount"] > 0]
total_deposits = sum(deposits)
print(f"Total deposits: ${total_deposits}")

# 2. Total withdrawals
withdrawals = [t["amount"] for t in transactions if t["amount"] < 0]
total_withdrawals = sum(withdrawals)
print(f"Total withdrawals: ${abs(total_withdrawals)}")

# 3. Largest transaction
amounts = [abs(t["amount"]) for t in transactions]
largest = max(amounts)
print(f"Largest transaction: ${largest}")

# 4. Count types
deposit_count = len([t for t in transactions if t["type"] == "deposit"])
withdrawal_count = len([t for t in transactions if t["type"] == "withdrawal"])
print(f"Deposits: {deposit_count}, Withdrawals: {withdrawal_count}")
```
</details>

### Exercise 3: Species Tracking

Track wildlife observations:

```python
observations = [
    "Bald Eagle", "Red Fox", "Deer", "Bald Eagle",
    "Wolf", "Red Fox", "Deer", "Bear", "Bald Eagle",
    "Deer", "Red Fox", "Wolf"
]

# 1. Find unique species
# 2. Count how many times each species was observed
# 3. Find most frequently observed species

# Your code here
```

<details>
<summary>Solution</summary>

```python
observations = [
    "Bald Eagle", "Red Fox", "Deer", "Bald Eagle",
    "Wolf", "Red Fox", "Deer", "Bear", "Bald Eagle",
    "Deer", "Red Fox", "Wolf"
]

# 1. Unique species
unique_species = set(observations)
print(f"Unique species: {unique_species}")

# 2. Count each species
counts = {}
for species in observations:
    counts[species] = counts.get(species, 0) + 1
print(f"Counts: {counts}")

# 3. Most frequent
most_common = max(counts, key=counts.get)
print(f"Most observed: {most_common} ({counts[most_common]} times)")
```
</details>

---

## Quick Reference

### Lists
```python
my_list = [1, 2, 3]
my_list.append(4)        # Add to end
my_list[0]               # Access by index
my_list[1:3]             # Slice
len(my_list)             # Length
```

### Dictionaries
```python
my_dict = {"key": "value"}
my_dict["key"]           # Access by key
my_dict.get("key")       # Safe access
my_dict["new"] = "value" # Add/update
"key" in my_dict         # Check existence
```

### Sets
```python
my_set = {1, 2, 3}
my_set.add(4)            # Add item
my_set.remove(2)         # Remove item
1 in my_set              # Fast membership test
set1 & set2              # Intersection
```

### Tuples
```python
my_tuple = (1, 2, 3)
my_tuple[0]              # Access by index
a, b, c = my_tuple       # Unpack
# Can't modify!
```

---

## What's Next?

You've learned Python's fundamental data structures! Next topics:
- **Conditionals** (if/else) - Making decisions
- **Loops** (for/while) - Repeating actions
- **Functions** - Reusable code blocks
- **File I/O** - Reading and writing files
- **Libraries** - Using powerful tools

Practice these concepts, and you'll be ready to write real programs that solve real problems in your field!

---

## Additional Resources

- **Python Official Tutorial**: docs.python.org/3/tutorial
- **Real Python**: realpython.com (excellent tutorials)
- **Python Tutor**: pythontutor.com (visualize code execution)
- **Practice**: leetcode.com, hackerrank.com

Remember: Programming is learned by doing. Write code every day, even if just for 15 minutes!

