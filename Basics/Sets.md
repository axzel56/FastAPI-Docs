A set in Python is an unordered collection of unique, immutable elements. 
### Characteristics

- Unordered: Elements in a set do not maintain a specific order.
- Unique Elements: Sets automatically remove duplicate elements; only one instance of each element is stored.
- Immutable Elements: Individual elements should be immutable (e.g. numbers, strings, tuples). Lists or dictionaries cant be directly elements of a sets because they are mutable.

#### Creating a set

Set can be created using curly braces `{}` or the `set()` constructor:

```python
my_set = {1,2,3,"apple"}

another_set = set([4,5,6, "banana", 4]) #Duplicates like 4 are removed

empty_set = set()
```

Common Set Operations and Methods

- Adding Elements - `add(element)`

Removing Elements:

- `remove(element)` : Removes a specified elements, Raises a `KeyError` if the element is not found.
- `discard(element)` : Removes a specified element. Does not raise an error if the element is not found.
- `pop()` : Removes and returns an arbitrary element from the set. Raises a `KeyError` if the set is empty.
- `clear()` : Removes all elements from the set.

- **Set Arithmetic (Mathematical Set Operations):**
    
    - `union(other_set)` or `set1 | set2`: Returns a new set containing all unique elements from both sets.
    - `intersection(other_set)` or `set1 & set2`: Returns a new set containing only the common elements between sets.
    - `difference(other_set)` or `set1 - set2`: Returns a new set containing elements present in `set1` but not in `set2`.
    - `symmetric_difference(other_set)` or `set1 ^ set2`: Returns a new set containing elements that are in either set, but not in both.

