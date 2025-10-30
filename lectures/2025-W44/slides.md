  # Python Basics & Data Structures

  - Open Codespaces
  - https://github.com/codespaces/

notes:
- today we're deviating from our course
- while the CLI is foundational,
- you didn't have enough countext

    ---slide---

  ## The Python Interpreter: Your Playground

  **1. Interactive Mode (REPL - Read-Eval-Print-Loop)**
  ```bash
  $ python3
  >>> 2 + 2
  4
  >>> print("Hello, World!")
  Hello, World!
  ```

Notes:
- open your terminal and try this out
- this is your REPL
- try: type "pr" hit tab
- that's "completion" it also works for variables

    ---slide---

  ## Variables: Storing Information

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

notes:
- programs have variables
- not equality, but assignment
- there used to be a "let" statement

    ---slide---

  **Good practices:**
  ```python
  # Good - descriptive names
  patient_count = 150
  glucose_level = 95

  # Bad - unclear names
  pc = 150
  gl = 95
  ```

notes:
- remember that completion works w/variables
- so long names are fine

    ---slide---

  ## Python's Core Data Types

  ```
    |   numeric   | sequence |  other  |
    | ----------- | -------- | ------- |
    | int         | str      | boolean |
    | float       | list     | dict    |
    | complex     | tuple    | set     |
    | binary      | range    | none    |
    | hexadecimal | set      |         |
  ```
notes:
- these are some of python's built-in data types
    ---slide---

  ### Numbers
  **Bases**
  ```py
  1          # base 10
  0          # base 10
  01         # ambiguous
  00000000   # base 10
  00000000.1 # base 10
  0x11       # base 16
  0o11       # base 18
  0b11       # base 2
  ```

    ---slide---

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

    ---slide---

  **Complex**
  ```python
  vector = 3 + 4j
  vector.real # 3
  vector.imag # 4
  ```

    ---slide---

  **Basic math:**
  ```python
  # Addition
  10 + 5        # 15

  # Subtraction
  10 - 5        # 5

  # Multiplication
  10 * 5        # 50
  ```

    ---slide---

  ```python
  # Division (always returns float)
  10 / 5        # 2.0
  10 / 3        # 3.3333...
  # Integer division (no remainder)
  10 // 3       # 3
  # Remainder (modulo)
  10 % 3        # 1

  # Powers
  2 ** 3        # 8 (2 to the power of 3)
  ```
Notes:
- inter division truncates

    ---slide---

  ### Strings

  Strings are text - sequences of characters.

  ```python
  # Single or double quotes work the same
  name = "Alice"
  name = 'Alice'

  # Multi-line strings use triple quotes
  description = """This is a longer
  text that spans
  multiple lines."""
  ```
Notes:
- single quote and double quote are equivalent
- but it lets you use one inside the other
    ---slide---

  ```python
  # String concatenation
  first_name = "John"
  last_name = "Smith"
  full_name = first_name + " " + last_name  # "John Smith"

  # String formatting (modern way)
  age = 34
  message = f"Patient {full_name} is {age} years old"
  print(message)  # Patient John Smith is 34 years old
  ```
Notes:
- notice the use of a variable in `message`
    ---slide---

  **Common string operations:**
  ```python
  text = "Hello, World!"

  # Length
  len(text)           # 13

  # Case conversion
  text.upper()        # "HELLO, WORLD!"
  text.lower()        # "hello, world!"
  ```
Notes:
- strings are immutable
- so `text.upper()` does not change `text`
- it just returns the change
    ---slide---

  ```python
  # Check contents
  text.startswith("Hello")   # True
  text.endswith("!")         # True
  "World" in text           # True

  # Replace
  text.replace("World", "Python")  # "Hello, Python!"

  # Split into list
  text.split(", ")    # ["Hello", "World!"]
  ```

Notes:
- notice `in` is a keyword, returns a boolean
- `split` returns a list, which is another data structure
    ---slide---

  ### Booleans

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
  ```
Notes:
- notice the difference of assignment vs equality in `=`
- we will use comparisons in `if` statements
    ---slide---

  ```python
  # Logical operators
  True and False    # False
  True or False     # True
  not True          # False

  # Practical example
  age = 34
  is_adult = age >= 18           # True
  can_vote = age >= 18 and age < 120  # True
  ```
Notes:
- fun fact, booleans behave like integers
- and vs or combinations return the value not a bool

    ---vertical---

  Try this:
  ```py
  > (3 < 1) or 7 or 8 
  > (3 > 1) and 7 and 8 
  ```
    ---slide---

  ### Type Checking and Conversion

  ```python
  # Check type
  type(42)          # <class 'int'>
  type(3.14)        # <class 'float'>
  type("hello")     # <class 'str'>
  type(True)        # <class 'bool'>
  ```

    ---slide---
  ```python
  # Convert between types
  int("42")         # 42
  float("3.14")     # 3.14
  str(42)           # "42"
  bool(1)           # True
  bool(0)           # False
  ```
Notes:
- notice the conversion is from string
    ---slide---

  ## Try It Yourself: Basic Python

  Open Python and try these:

      ---vertical---
  ```python
    # 1. Create variables for yourself
    # 2. Print a formatted message
  your_name = "Your Name Here"
  your_age = 25
  your_field = "Your Field"
  print(f"Hi, I'm {your_name}, I'm {your_age}\
  , and I work in {your_field}")
    # 3. Do some calculations
  hours_per_week = 40
  weeks_per_year = 52
  total_hours = hours_per_week * weeks_per_year
  print(f"You work {total_hours} hours per year")
    # 4. Test some comparisons
  print(total_hours > 2000)
  print(your_age >= 18)
  ```
