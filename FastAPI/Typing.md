Typing is the practice of using type hints to indicate the expected data types of variables, function parameters and return values


### TypeVar

`TypeVar` is a tool used to create generic types, allowing functions, classes and methods to work with multiple types while maintaining type safety.
It acts as a placeholder for a specific type that is determined at the time the function is called or the class is instantiated.
```python
from typing import TypeVar

T = TypeVar('T')
def get_first(items: list[T]) -> T:
	return items[0]
	
num = get_first([1,2,3])

word = get_first(["hello", "world"])
```

### Key Features:

- Generics: `TypeVar` is fundamental for creating generic classes and functions.
- Consistency: It ensures that multiple usages of the same `TypeVar` in a function signature corresponds to the same actual type.
- 