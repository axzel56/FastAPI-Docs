The `@staticmethod` is a built in decorator used to define a static method within a class.
Static methods are methods that belong to the class but does not operate on an instance of the class itself. 
Defined using `@staticmethod` decorator.

### Key Characteristics of Static Methods

- No implicit `self` or `cls` argument: Unlike instance methods (which receive `self`) or class methods (receives `cls`) static methods do not automatically receive the instance or the class as their first argument.
- Independent of instance and class state: Static methods cannot access or modify instance attributes directly, as they lack the `self` or `cls` reference.
- Called Directly on the class: Static methods can be invoked directly on the class itself without needing to create an instance of the class.

### Used When:

- Utility functions that logically belong to a class but do not require access to any instance-specific data or class-level data. They help in organizing related functionality within a class, even if that functionality is independent of the class's state.

