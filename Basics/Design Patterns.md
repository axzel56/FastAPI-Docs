Design patterns deal with object creation mechanisms, trying to create objects in manner suitable for the situation.

# Super
`super()` is a func used to call methods of a parent (super) class from a child class.

`super()`  lets a class delegate work to its parent class w/o hardcoding the parent's name.
- delegation is the process of assigning responsibility
- delegation is a design pattern where an object, known as the delegator, passes responsibility for a specific task or method call to another object, called the delegate. It reduces tight coupling between classes.
- 


# Most Common Creational design patterns:

# 1. Singleton

Singleton pattern ensures that a class has only one instance and provides a global point to access to it.
Useful when exactly one object is needed to coordinate actions across the system.

```python
class Singleton:
	_instance = None
	
	def __new__(cls):
		if cls._instance is None:
			cls._instance = super(Singleton, cls).__new__(cls)
		return cls._instance
		
# Usage
singleton1 = Singleton()
singleton2 = Singleton()

print(singleton1 is singleton2) # True
```

Here, the Singleton class overrides the `__new__` method to ensure only one instance is created. The `_instance` class variable is checked to see if it is None. 

# 2. Factory Method Pattern

The Factory Method pattern defines an interface for creating an object, but lets subclasses alter the type of objects that will be created.

