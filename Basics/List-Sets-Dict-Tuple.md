
# List
List/arrays
List can hold elements of any data type.


- append() -> Adds an element at the end of the list.
- clear() -> Removes all the elements from the list
- copy() -> Returns a copy of the list
- count() -> Returns the number of elements with the specified value
- extend() -> Add the elements of a list (or any iterable), to the end of the current list
- index() -> Returns the index of the first element with the specified value
- insert() -> Adds an element at the specified position
- pop() -> Removes the element at the specified position
- remove() -> Removes the first item with the specified value
- reverse() -> Reverses the order of the list
- sort() -> Sorts the list

## Using Type Hints:

 ```python
 from typing import List
 
 int_list : List[int] = [1,2,3]
 
 int_list.append("some string")
 ```

# Sorted()

`sorted()` in Python returns a new sorted list from the elements of any iterable, such as list, tuple  
```python
a = [4,1,3,2]
b = sorted(a)
print(b) #[1,2,3,4]
```

## Parameters:

- itertable: The sequence to be sorted (list, tuple, set, string etc)
- key (Optional) : A function to customize the sort order.
- reverse (Optional) : If True, sorts in descending order
#### Sorting a list of dictionaries:

``` python
a = [
    {"name": "Harry", "score": 85},
    {"name": "Leo", "score": 91},
    {"name": "Eve", "score": 78}
]

b = sorted(a, key=lambda x: x['score'])
print(b)
```


# Set

Set are used to store multiple items in a single variable.

A set is a collection which is `unordered`, `unchageable`, and `unindexed`.

```python
thisset = {"apple", "banana", "cherry"}
print(thisset)
```


Note: True and 1 are considered as the same value in sets and are treated as duplicates.


# Set Items

	Set items are `unordered`, `unchageable` and do not allow duplicate values


Example:
```python

myset = {"apple", "banana", "cherry"}
print(type(myset)) # <class 'set'>
```

### The `set()` Constructor

```python

thisset = set(("apple", "banana", "cherry"))
# note the double round-brackets
print(thisset)
```


# Tuple

```python
mytuple = ("apple", "banana", "cherry")
```

Tuple items are indexed, the first item has index `[0]`, the second item has index `[1]` etc.

Tuple items are `ordered` , `unchangeable` and allow `duplicate` values.


# Dictionary

Dictionary is collection which is `ordered` and `changeable`. No duplicate members.

```python
thisdict = {
	"brand" : "Ford",
	"model" : "Mustang",
	"year"  : 1964
}
```


### Get Items

The `items()` method will return each item in a dictionary as tuple in a list.

#### Example:
```python
thisdict = {
	"brand" : "Ford",
	"model" : "Mustang",
	"year" : 1964
}
x = thisdict.items() 
# dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])
```

- `popitem()` method removes the last inserted item.
- `del` removes the item with the specified key name- can also delete the dictionary completely.

```python
thisdict = {
	"brand" : "ford",
	"model" : "Mustang",
	"year" : 1964
}
del thisdict["model"]

```

#### Nested Dictionaries

```python
myfamily = {  
  "child1" : {  
    "name" : "Emil",  
    "year" : 2004  
  },  
  "child2" : {  
    "name" : "Tobias",  
    "year" : 2007  
  },  
  "child3" : {  
    "name" : "Linus",  
    "year" : 2011  
  }  
}
```

Access items in a nested dict:
```python
print(myfamily["child2"]["name"])
```

|Method|Description|
|---|---|
|[clear()](https://www.w3schools.com/python/ref_dictionary_clear.asp)|Removes all the elements from the dictionary|
|[copy()](https://www.w3schools.com/python/ref_dictionary_copy.asp)|Returns a copy of the dictionary|
|[fromkeys()](https://www.w3schools.com/python/ref_dictionary_fromkeys.asp)|Returns a dictionary with the specified keys and value|
|[get()](https://www.w3schools.com/python/ref_dictionary_get.asp)|Returns the value of the specified key|
|[items()](https://www.w3schools.com/python/ref_dictionary_items.asp)|Returns a list containing a tuple for each key value pair|
|[keys()](https://www.w3schools.com/python/ref_dictionary_keys.asp)|Returns a list containing the dictionary's keys|
|[pop()](https://www.w3schools.com/python/ref_dictionary_pop.asp)|Removes the element with the specified key|
|[popitem()](https://www.w3schools.com/python/ref_dictionary_popitem.asp)|Removes the last inserted key-value pair|
|[setdefault()](https://www.w3schools.com/python/ref_dictionary_setdefault.asp)|Returns the value of the specified key. If the key does not exist: insert the key, with the specified value|
|[update()](https://www.w3schools.com/python/ref_dictionary_update.asp)|Updates the dictionary with the specified key-value pairs|
|[values()](https://www.w3schools.com/python/ref_dictionary_values.asp)|Returns a list of all the values in the dictionary|
`**` is called Dictionary Unpacking Operator.
It takes key-value pairs inside a dictionary and unpacks them as keyword arguments into a function of a class constructor.

Sample:
```python
user_data = {"username": "alice", "email": "some@example.com"}

```

#### Without the **

Needs to manually map every single field.
Bad when the phone number is updated.

```python
obj = User(username=user_data["username"], email=user_data["email"])
```
#### With **

`**` automatically turns the dictionary into arguments.
```python
obj = User(**user_data)
# Python translates this internally to
# obj = User(username = "alice", email="some@example.com")
```
