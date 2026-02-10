
Metaclasses control classes i.e. control structure and behavior of classes.

Metaclass is a class whose instances are other classes.

By default, the built-in `type` is the metaclass for all standard Python classes.

# How Metaclass Work:

When we define a class in Python, the interpreter uses the class's metaclass to construct the class object.

1. The class body is executed in a new namespace (a dictionary-like object).
2. The appropriate metaclass is determined.
3. The metaclass is called to create the new class object, typically by its `__new__` and `__init__` methods.

We can create a metaclass by defining a class that inherits from `type` and overriding its methods, primarily `__new__`, `__init__` or `__call__` to inject specific logic or behavior during class creation.


Use:
- Adding attributes/methods automatically
- Enforcing certain rules
- In complex projects, frameworks and libraries

Almost Everything in python is an object, which includes functions and as well as classes.
So, 
- the functions and classes can be passed as arguments
- can exist as an instance and so on.
- the concept of objects let the classes in generating other classes.

The classes that generate other classes are defined as metaclasses.


### Example a simple Custom Metaclass

```python
class CustomMeta(type):
	# __new__ is called before the class is created
	
	def __new__(cls, name, bases, dct):
	
	# cls - metaclass itself (CustomMeta)
	# name - The class name as a String ("MyClass")
	# bases - Tuple of base classes ((Base1, Base2))
	# namespace (dct) - Dictionary containing everyting written inside the class body
		dct['added_attributes'] = 'Hello from the metaclass'
		return super().__new__(cls,name, bases,dct)
		# Call the default type.__new__ to actually create the class

class MyClass(metaclass = CustomMeta):
# Internally
 """
 MyClass.__init__(
	 CustomMeta,
	 "MyClass",
	 (),
	 namespace
 )
 """
	pass

# The class 'MyClass' now has an attribute added by the metaclass
print(MyClass.added_attribute)
```
# type

A class defines the properties and available actions of its objects and also it act as a factory for object creation.

The exact class that is used for class instantiation is called type.

**Usual Class Implementation:**
``` python

class FoodType(object):
	def __init__(self, ftype):
		self.ftype = ftype
	
	def getFtype(self):
		return self.ftype
		
def main():
	ftype = FoodType(ftype = 'Non Veg')
	print(fType.getFtype())

```


**Using the `ftype` class:**
```python
def init(self, ftype)
	self.ftype = ftype
	
def getFtype(self)
	return self.ftype
	
FoodType = type('FoodType', (object, ), {
	'__init__' : init,
	'getFtype' : getFtype
	})
	
fType = FoodType(ftype = 'Non-Veg')
print(ftype.getFtype())

```

