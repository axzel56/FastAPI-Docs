Namespace is a mapping from names to objects. It functions like a dictionary where keys are the name (identifiers) and values are the corresponding objects (variables, functions, classes, modules, etc.). Namespaces are crucial for organizing and managing identifiers, preventing naming conflicts and defining the scope of variables.


#### Built-in Namespaces: 
This namespaces contains all the built-in functions and exceptions that are always available when Python runs, such as `len()`, `print()`, `str()`, `int()` etc.

#### Global Namespace:
This namespace is created when a module is loaded and exists for the duration of the program's execution. It contains all the names defined at the module level.

#### Non-Local Namespace:
This applies to nested function. If a function is defined within another function, the outer function's namespace becomes the enclosing namespace for the inner function.

#### Local Namespace:
This namespace is created when a function is called and is specific to that function's execution. It contains the names defined within the function, including its parameters and local variables. This namespace is deleted when the function finishes executing.


```python

x = 10

def outer_function():
	y = 20
	def inner_function():
		z = 30
		print(f"Inside inner_function: z {z}")
```

