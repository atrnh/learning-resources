# Data structures cheatsheet
This cheatsheet is a "greatest hits" collection of the essential things you
need to know about the data structures available to you in Python (and in many
other languages!)

This is no substitute for reading the Python docs, so I highly encourage you
to give them a try. They might look intimidating at first, but you'll get used
to understanding them the more you practice reading them.

## Vocabulary
- **Collection:** Most data structures are *collections* of other data types.
  A collection can be ordered or unordered.
- **Sequence types:** Some data structures are *sequences*. This usually
  implies that the data structure is *orderly* and *indexable.*
  - **Index:** When something is *indexable*, it has indices. It is also
    inherently *ordered*.

    If you had an ordered collection called `cool_items` you could index it to
    get the element at that index, thusly: `cool_items[0]`

    You can refer to `cool_items[0]` in plain English as, "cool_items at 0"
- **Mapping types:** Data structures like dictionaries are a key-value pair,
  where the key maps to a value.

  If you had a dictionary called `fruit` which has a key called `banana`, you
  could reference the value at `banana` like so: `fruit['banana']`

  In plain English, you can refer to `fruit['banana']` as "fruit at banana"


## Lists
**Type:** mutable sequence  
**Fast:** adding & deleting items at the end  
**Slow:** adding & deleting items at the beginning, searching  

Example:
```python
>>> cool_items = ['atom', 'baseball', 'coin']
>>> cool_items[0]
'atom'
```

### Common usage
I need to iterate over a collection of items and I don't care what they are
exactly:
```python
>>> class User(object):
...     def __init__(self, name):
...             self.name = name
...     
...
>>> # I have a database of users and I want to see their names.
...
>>> users = [User('muffin'), User('florpflorp'), User('jellybean09')]
>>> for user in users:
...     print user.name
...
muffin
florpflorp
jellybean09
```

Order is important but I only care about adding/deleting items from the
end:
```python
>>> chess_history = []
>>> chess_history.append(('e4', 'e5'))  # adding moves when they occur
>>> chess_history.append(('f4', 'exf4'))
>>> chess_history
[('e4', 'e5'), ('f4', 'exf4')]
>>> chess_history[1]  # getting the second move
('f4', 'exf4')
>>> chess_history.append(('Bc4', 'Qh4+'))
>>> chess_history
[('e4', 'e5'), ('f4', 'exf4'), ('Bc4', 'Qh4+')]
>>> chess_history.pop()  # undoing a move
('Bc4', 'Qh4+')
>>> chess_history
[('e4', 'e5'), ('f4', 'exf4')]
```

### Reference
- [Python 2.7: More on
   Lists](https://docs.python.org/2/tutorial/datastructures.html#more-on-lists)
- [Python 3.6: More on
   Lists](https://docs.python.org/3.6/tutorial/datastructures.html#more-on-lists)


## Tuples
**Type:** immutable sequence  

Example:
```python
>>> paris_coordinates = ('48.864716', '2.349014')
>>> paris_coordinates[0]  # latitude
'48.864716'
>>> paris_coordinates[1]  # longitude
'2.349014'
```

### Common usage
The way my data is ordered is very meaningful and will rarely change:
```python
>>> slate_grey = (44, 62, 80)  # RGB values
>>> employee = ('005', 'Jane Doe', 32)  # ID, name, and age
```

I'll never want individual values by themselves, I need a discrete package
of information:
```python
>>> address = ('123', 'Sesame St.')  # house number and street name
>>> card = ('Queen', 'hearts')  # rank and suit of a card
```

### Reference
- [Python 2.7: Tuples and Sequences](https://docs.python.org/2.7/tutorial/datastructures.html#tuples-and-sequences)
- [Python 3.6: Tuples and Sequences](https://docs.python.org/3.6/tutorial/datastructures.html#tuples-and-sequences)


## Set
**Type:** set type  
**Fast:** searching

They're like dictionaries, but they only have keys.

Example:
```python
>>> states_visited = set(['Hawaii', 'California', 'Idaho'])
>>> states_visited
set(['California', 'Hawaii', 'Idaho'])
>>> states_visited.add('Arkansas')
>>> states_visited
set(['Arkansas', 'California', 'Hawaii', 'Idaho'])
>>> states_visited.add('Hawaii')  # we've gone to Hawaii twice!
>>> states_visited
set(['Arkansas', 'California', 'Hawaii', 'Idaho'])  # Hawaii only shows up once
>>> 'Idaho' in states_visited
True
>>> 'Kentucky' in states_visited
False
```

### Common usage
I want to see if something exists:
```python
>>> available_rooms = set(['Meeting Room 1', 'Meeting Room 2'])
>>> 'Meeting Room 1' in available_rooms
True
```

I want to ignore duplicates:
```python
>>> fun_word = 'expelliarmus'
>>> unique_letters = set(fun_word)
>>> unique_letters
set(['a', 'e', 'i', 'm', 'l', 'p', 's', 'r', 'u', 'x'])
```

### Reference
- [Python 2.7: Sets](https://docs.python.org/2.7/tutorial/datastructures.html#sets)
- [Python 3.6: Sets](https://docs.python.org/3.6/tutorial/datastructures.html#sets)
