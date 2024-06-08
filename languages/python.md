# 📖 Python Basics
Python is a high-level programming language known for its simplicity and readability. It supports multiple programming paradigms, including procedural, object-oriented, and functional programming.

## 🚀 Data Types in Python
1. **Numeric Types**: Integers, floating-point numbers, and complex numbers.
```python
int_var = 10
float_var = 3.14
complex_var = 3 + 4j
```
2. Sequence Types: Lists, tuples, and range objects.

```python

list_var = [1, 2, 3, 4, 5]
tuple_var = (1, 2, 3, 4, 5)
range_var = range(0, 10, 2)  # Range from 0 to 10 (exclusive) with step 2
```
3. Mapping Type: Dictionary.

```python
dict_var = {'a': 1, 'b': 2, 'c': 3}
```
4. Set Types: Sets and frozen sets.
```python
set_var = {1, 2, 3, 4, 5}
frozenset_var = frozenset({1, 2, 3, 4, 5})

```
5. Boolean Type: Represents True or False.
```python
bool_var = True
```
Python provides built-in collections and methods to work with them effectively.
6. Text Type: Strings.

```python
my_list = [1, 2, 3, 4, 5]
```
```scss
append(x)
extend(iterable)
insert(i, x)
remove(x)
pop([i])
clear()
count(x)
index(x[, start[, end]])
sort(key=None, reverse=False)
reverse()
copy()
```
7. Dictionary

```python
my_dict = {'a': 1, 'b': 2, 'c': 3}
```
```scss
clear()
copy()
fromkeys(seq[, value])
get(key[, default])
items()
keys()
pop(key[, default])
popitem()
setdefault(key[, default])
update([other])
values()
```

7. Set

```python
my_set = {1, 2, 3, 4, 5}
```
```scss
add(elem)
clear()
copy()
difference(*others)
difference_update(*others)
discard(elem)
intersection(*others)
intersection_update(*others)
isdisjoint(other)
issubset(other)
issuperset(other)
pop()
remove(elem)
symmetric_difference(other)
symmetric_difference_update(other)
union(*others)
update(*others)
```
8. Tuple

```python
my_tuple = (1, 2, 3, 4, 5)
```
```scss
count(value)
index(value[, start[, stop]])
```

9. String

```python
my_string = "Hello, World!"
```
```scss
capitalize()
casefold()
center(width[, fillchar])
count(sub[, start[, end]])
encode(encoding="utf-8", errors="strict")
endswith(suffix[, start[, end]])
expandtabs(tabsize=8)
find(sub[, start[, end]])
format(*args, **kwargs)
format_map(mapping)
index(sub[, start[, end]])
isalnum()
isalpha()
isascii()
isdecimal()
isdigit()
isidentifier()
islower()
isnumeric()
isprintable()
isspace()
istitle()
isupper()
join(iterable)
ljust(width[, fillchar])
lower()
lstrip([chars])
partition(sep)
replace(old, new[, count])
rfind(sub[, start[, end]])
rindex(sub[, start[, end]])
rjust(width[, fillchar])
rpartition(sep)
rsplit(sep=None, maxsplit=-1)
rstrip([chars])
split(sep=None, maxsplit=-1)
splitlines([keepends])
startswith(prefix[, start[, end]])
strip([chars])
swapcase()
title()
translate(table)
upper()
zfill(width)
```

- Python's collections and methods offer versatile tools for data manipulation and processing.

## 🚀 Access Modifiers in Python

Python does not have traditional access modifiers like Java. Instead, it uses naming conventions and language features to indicate member visibility.

    Public: No special notation. All members are public by default.
    Protected: Conventionally, members prefixed with a single underscore _ are considered protected.
    Private: Conventionally, members prefixed with a double underscore __ are considered private.

```python

class MyClass:
    def __init__(self):
        self.public_var = 10
        self._protected_var = 20
        self.__private_var = 30

    def public_method(self):
        print("This is a public method.")

    def _protected_method(self):
        print("This is a protected method.")

    def __private_method(self):
        print("This is a private method.")

obj = MyClass()
print(obj.public_var)  # Accessible
print(obj._protected_var)  # Accessible but discouraged
# print(obj.__private_var)  # Error: AttributeError
obj.public_method()  # Accessible
obj._protected_method()  # Accessible but discouraged
# obj.__private_method()  # Error: AttributeError
```

Although Python does not enforce access restrictions, following conventions helps maintain code readability and understandability.
