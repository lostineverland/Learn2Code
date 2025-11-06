  # Python Basics & Data Structures Part 2

  - Open Codespaces
  - https://github.com/codespaces/

notes:
- last week we talked about
  - numbers (float, int)
  - strings
  - booleans
- This week we're going to talk about
  - lists

    ---slide---

  ## Lists: Collections of Data

  - Lists are ordered collections 
  - hold multiple items

    ---slide---
  ### Creating Lists

  ```python
  # Empty list
  patients = []

  # List with data
  ages = [25, 34, 45, 52, 61]
  names = ["Alice", "Bob", "Carol", "David"]
  mixed = [1, "hello", 3.14, True]
  ```
notes:
- lists can have any kind of value
- but usually don't

    ---slide---

  ```python

  # Multi-line for readability
  diagnoses = [
        "Type 2 Diabetes",
        "Hypertension",
        "Asthma",
        "COPD",
  ]
  ```
notes:
- in lists trailing commas are encouraged
- notice the indentation

    ---slide---

  ### Accessing List Items

  ```python
  fruits = ["apple", "banana", "cherry", "date"]

  # Indexing (starts at 0!)
  fruits[0]      # "apple"
  fruits[1]      # "banana"
  fruits[3]      # "date"
  ```

    ---slide---

  ```python
  # Negative indexing (from the end)
  fruits[-1]     # "date" (last item)
  fruits[-2]     # "cherry" (second to last)

  # Length
  len(fruits)    # 4
  ```

    ---slide---

  ### Slicing: Getting Multiple Items

  ```python
  numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  # Syntax: list[start:end]  (end is exclusive)
  numbers[2:5]     # [2, 3, 4]
  numbers[:3]      # [0, 1, 2] (start from beginning)
  numbers[7:]      # [7, 8, 9] (go to end)
  numbers[:]       # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] (copy entire list)
  ```
notes:
- please create this list and try it
- think of the comma as the selector
- it selects the item on the right of the comma
- the 0th comma is not present

    ---slide---
  ```python
  # Step

  numbers[::2]     # [0, 2, 4, 6, 8] (every other item)

  numbers[1::2]    # [1, 3, 5, 7, 9] (every other, starting at 1)

  numbers[::-1]    # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0] (reverse!)
  ```
notes:
- steps just skip
- reverse works just fine (nobody uses it!)

    ---slide---

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
  ```
notes:
- use your `numbers` list to see the methods available
    ---slide---

  ```python
  # Insert at specific position
  fruits.insert(1, "apricot")
  # ["apple", "apricot", "blueberry", "cherry", "date", "elderberry", "fig"]

  # Remove by value
  fruits.remove("blueberry")

  # Remove by index
  del fruits[0]

  # reverse
  reversed(fruits)
  ```
notes:
- notice the last 2 are functions as opposed to methods

    ---slide---

  ```python
  # Remove and return last item
  last = fruits.pop()

  # Remove and return item at index
  second = fruits.pop(1)

  # Clear entire list
  fruits.clear()
  ```

notes:
- here's a few more methods

    ---slide---

  ### Useful List Operations

  ```python
  numbers = [3, 1, 4, 1, 5, 9, 2, 6]

  numbers.sort()
  # numbers is now [1, 1, 2, 3, 4, 5, 6, 9]

  # Sort descending
  numbers.sort(reverse=True)

  # Get sorted copy (doesn't modify original)
  sorted_nums = sorted(numbers)
  ```
notes:
- some more operations

    ---slide---

  ```python
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
