
A decorator in Python is basically a function that makes another function as input, adds some extra behavior and then returns a new function

**i.e**
A decorator wraps another function to modify or extend its behavior without changing the original code.

We pass the base function as an argument to the decorator.



Decorators usually takes a parameter `func` . It is usually defined like a function.


Example of Decorators in Python:

`@requires_admin` Decorator

``` python
def required_admin(func):
	def wrapper(user, *args, **dargs)
		if user.get("role") != "admin":
		print(f"Access denied for the {user['name']}. Admin Only.")
		return None
		print(f"Access granted to {user['name']}.")
		return func(user, *args, **kwargs)
	return wrapper
```



Using the 