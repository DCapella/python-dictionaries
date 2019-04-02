# Python Dictionaries and Maps

#### [HackerRank](www.hackerrank.com)

## Problem

> Given N names and phone numbers, assemble a phone book that maps friends' names to their respective phone numbers. You will then be given an unknown number of names to query your phone book for. For each name queried, print the associated entry from your phone book on a new line in the form name=phoneNumber; if an entry for name is not found, print Not found instead.

## Template

```python
"""Loads a dictionary and then looks for people based on STDIN"""
import fileinput

def address_book(items):
  pass

items = fileinput.input()

address_book(items)

```

## Pseudo Code

```python
# Declare empty dict
# Declare threshold (to know when to start searching instead of adding)
# loop through items (do not have to skip first because it was already read when declaring threshold)
  # if i less than threshold
    # unpack item split into name, num
    # load into dict, strip num (strip because it might have a \n)
  # else (once we pass threshold)
    # declare name from item
    # get number from dict, else 0
    # print name=num if name exists (not 0) else print not found
```

## Code

#### Declare Empty Dict
#### Declare Threshold
#### Loop Through Items

```python
address_book = {}
threshold = int(items[0])
for i, item in enumerate(items):
```

#### If I Less Than Threshold
#### Unpack Item Split Into Name, Num
#### Load Into Dict, Strip Num

```python
if i < threshold:
  name, num = item.split(' ')
  address_book[name] = num.strip()
```

#### Else
#### Declare Name from Item
#### Get Number from Dict, Else 0
#### Print if not 0 else Not Found

```python
else:
  name = item.strip()
  num = address_book.get(name, 0)
  print(f"{name}={num}" if num else "Not found")
```

## Full Solution

```python
"""Loads a dictionary and then looks for people based on STDIN"""
import fileinput

def address_book(items):
  """Fills an address book and looks for requested people.
  
  Parameters
  ----------
  items: fileinput obj
    Can also be a list.
    First element is an int telling how many people to load into dict.
    Each person must be one string with a single name, space, phone number.

  Returns
  -------
  None: None
    Prints person's name and phone number else not found.

  """
  address_book = {}
  threshold = int(items[0])
  for i, item in enumerate(items):
    if i < threshold:
      name, num = item.split(' ')
      address_book[name] = num.strip()
    else:
      name = item.strip()
      num = address_book.get(name, 0)
      print(f"{name}={num}" if num else "Not found")
    

items = fileinput.input()

address_book(items)
```

## Conclusion
Learning more about unpacking from fileinput in such that once you grab the next item from it, you do not need to skip it.
