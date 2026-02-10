The` __init__` method is the initializer (not a constructor), the `__repr__` method customizes an object's string representation, the `__eq__` method customizes what it means for objects to be equal to one another.

## Equality and Hashability

| Operation | Dunder Method Call | Returns          |
| --------- | ------------------ | ---------------- |
| `x == y`  | `x.__eq__(y)`      | Typically `bool` |
| `x != y`  | `x.__ne__(y)`      | Typically `bool` |
| `hash(x)` | `x.__hash__()`     | `int`            |

| Operation | Dunder Method Call | Returns          |
| --------- | ------------------ | ---------------- |
| `<`       | `__lt__`           | Typically `bool` |
| `>`       | `__gt__`           | Typically `bool` |
| `<=`      | `__le__`           | Typically `bool` |
| `>=`      | `__ge__`           | Typically `bool` |
NotImplemented means "I don't Know"

Dunder methods that perfom an operation between two objects are expected to return NotImplemented when the first object doesn't know how to perform that operation on the second object.

# Initialization Vs Instantiation

Instantiation is the entire process (example building a house from the blueprint)

Initialization is the step in the building process.


## Instantiation

Instantiation is the act of creating a new object from a class. It is the process of making concrete instance of a blueprint.

Example, when calling a class like a function.

```python
my_object = MyClass()
```

Python performs the following steps to instantiate the object.
1. Creation: A new, empty object is created in memory.
2. Initialization: The object's `__init__` method is called to set its initial state.
3. Return: The newly created and initialized object is returned and assigned to a new variable.

### Object Creation `(__new__)`

Instantiation is the act of allocating memory and creating the physical object in the computer's memory.
This is handled by the special method `__new__()`.

When we call `MyClass()`. Python internal mechanism call 
`MyClass.__new__(cls, *args, **kwargs)` behind the scenes.




## Initialization


Provides the newly created object with its starting data or state.

Refers to the work done inside the `__init__` method. This method is automatically called after the new object is created.

The primary purpose of `__init__` is to:
- Assign value to the object's attributes.
- Perform any other setup required for the object to be ready for use




## `__new__` dunder

The `__new__` method is a special (dunder) static method responsible for creating and returning a new instance of a class.
It creates and allocates memory for the new instance.
Its is an actual constructor while the `__init__` is the new initializer.

- It Creates and returns a new object instance
- Called before `__init__`
- Takes a class as its first argument `(cls)`.
- Must return an instance of the class or another object entirely.

This dunder method is necessary for the scenarios:
- Subclassing Immutable Types: Must use `__new__` when creating subclasses of immutable built-in types `(str, int, float, tuple)` as their state cannot be modified after creation in `__init__`.
- Implementing Design Patterns: 


## `__init__` method

The `__new__`is used when we need to control the creation of a new instance while `__init__` is used when we need to control the initialization of  a new instance.

This method is only responsible for setting the state of the object. It just receives the values through the parameters and assigns them to the class attributes.

This method is only responsible for setting the state of the object.
It receives values through its params and assign them to the class attributes.




### `__name__` dunder

`__name__` is a special built in variable that is automatically defined within every module. Its value depends on how the module is being executed.

- When a script is run directly: If a python file is executed as the main program, the `__name__` variable within that script is set to the string literal `__main__`.
- When a module is imported: If a python file is imported as a module into another script, the `__name__` variable within the imported module is set to the name of the module itself


## Context Managers

A context manager is an object that can be used in a `with` block.

