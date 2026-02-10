Super() function is used to call methods from a parent (superclass) inside a child (subclass). It allows us to  *extend or override* inherited methods while still reusing the parent's functionality.

`super()` -> Returns a proxy object which represents the parent's class.

- Proxy object is an object that acts as a substitute or placeholder for another object, often called the *real or service* object.
- The proxy object controls the access to the real object, allowing us to add extra functionality, like security, logging or performance optimization, w/o changing the original object's code.

## Why use super()

- No need to hardcode parent class names
- Works with single, multiple and multilevel inheritance.
- Improves code reusability and maintainability.
- Prevents duplicate initialization in complex hierarchies.


```python
class Emp:
	def __init__(self, id, name):
		self.id = id
		self.name = name
		
class fun(Emp):
	def __init__(self, id, name, email):
		super().__init__(id,name)
		self.email = email

obj = fun(101, "Olivia", "olivia@email.com")
print(obj.id, obj.name, obj.email)

```

- Inheritance: By writing `class fun(Emp)`, we are telling Python that `fun` should have all the attributes and methods of `Emp`
- The super() Call: In the `fun` constructor `super().__init__(id, name)` jumps back to the `Emp` class to handle the `id and name` assignment.
```python
class Person:
    def __init__(self, name, id):
        self.name = name
        self.id = id

class Emp(Person):
    def __init__(self, name, id):
        self.name_ = name   # Forgot to call Person’s __init__

emp = Emp("Jack", 103)
print(emp.name)
```
