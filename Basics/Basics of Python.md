with statement in Python simplifies resource management y automatically handling setup and cleanup tasks.


Commonly used in:
- File management
- Database connection
- Network Connections

## With Statement

- simplifies resource management: with statement ensures that resources are properly acquired and released, reducing the likelihood of resource leaks.
- Replaces the Try-Except-Finally Blocks: 
- Enhances Readability.


**Without 'with'**

``` python
file = open("example.txt", "r")
try :
	content = file.read()
	print(content)
finally:
	file.close()
```

**With 'with'**

``` python

with open("example.txt", "r") as file:
	content = file.read()
	print(content)
```

**Explanation:**

with ``open(...)`` statement reads and prints file's content while automatically closing it, ensuring efficient resource management without a finally block.


3. Context Managers and 'with' statement

The with statement relies on context managers, which manage resource allocation and deallocation using two special methods:
- `__enter__()` : Acquire the resource and returns it.
- ` __exit__()` :  Releases the resource when the block exits.

Example:

``` python
class FileManager:
	def __init__(self, filename, mode):
		self.filename = filename
		self.mode = mode

	def __enter__(self):
		self.file = open(self.filename, self.mode)
		return self.file

	def __exit__(self, exc_type, exc_value, traceback):
		self.file.close()

```

## Pass in Python

Pass Statement in Python is a null operation meaning it does nothing. It serves as a placeholder when a statement is syntactically required but no code needs to be executed.


When to use pass:
- Empty functions or method definitions


PASS vs Return

`pass` Statement

`pass` statement is a null operation; it does nothing.
It is used as a placeholder when a statement is syntactically required but no action is desired.


`return` Statement:

- `return` exits the current function and optionally sends a value back to the caller.
- When a `return` statement is executed, the function's execution terminates, and control returns to the point where the function was called.
- If a value is specified after `return`, that value becomes the result of the function call. If no value is specified, `None` is returned implicitly.

# Namespace

A namespace is simply a container (a mapping) that holds names -> objects.

In Python terms:

`namespace = dictionary of identifiers`

Example:

```python

x = 10
y = 20

# Behind the scenes, Python is:
globals() == {
	'x' : 10,
	'y' : 20
}
```

That dictionary is the global namespace

## Types of Namespaces

### 1. Built in Namespace:

Available everywhere

```python
len("abc")

__builtins__ = {
    'len': <built-in function>,
    'print': <built-in function>,
    ...
}
```

### 2.  Global Namespace

Defined at the module level: Available anywhere in the file.

```python
a = 5
```

### 3. Local Namespace

Inside a function

```python
def foo() {
	b = 10
	print(b)
}

locals() = {
	'b' : 10
}
```

### 4. Class Namespace

This dictionary is the class namespace.

```python
class MyClass:
	x = 100
	def hello(self) : pass
	
{
	'x' : 100,
	'hello' : <function>
}
```

### 5. Namespace + Metaclasses

```python
class MyClass(metaclass = CustomMeta)
	pass
	
#BTS
namespace = {}
CustomMeta.__new__(
	CustomMeta,
	"MyClass",
	(),
	namespace
)


```


# Lambda Function 

Lambda Function is a small, anonymous function defined with the `lambda` keyword that can take any number of arguments but has only one expression.

The result of the expression is automatically returned, w/o needing a return statement.

```python
lambda arguments : expression
```

- `lambda` : The keyword to define the anonymous function.
- `arguments` : A comma-separated list of input parameters (can be zero or more)
- `expression` : A single expression that is evaluated and returned when the lambda is called.


# isInstance

Instance is used in reference to a class (e.g. "42 is an instance of the `int` class"), while "object" is a more general term for any entity in python code.

Python provides a built-in function called `isinstance()` to check if an object is an instance of a specified class or any of its subclasses.

### Syntax:
```python
isinstance(object, classinfo)
```

- `object` :  The value or variable to check.
- `classinfo` : The class, type or a tuple of classes and types to check against.

#### Examples:

``` python
x = 5
print(isinstance(x, int))  # Output: True
print(isinstance(x, str))  # Output: False
```

