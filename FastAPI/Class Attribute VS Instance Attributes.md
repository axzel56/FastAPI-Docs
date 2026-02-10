
# Class Attributes

- Definition: Defined within the class body, outside of any methods (including `__init__`)
- Scope : Shared by all instances(objects ) of that class. Belongs to the class itself, not to individual instances.
- Access: Can be accessed using either the class name (e.g. `ClassName.attribute_name`) or an instance of the class (e.g. `instance_name.attribute_name`)
- Modification: Changes to a class attribute affect all instances of the class and when accessed directly through the class.

# Instance Attributes

- Definition: Defined within the `__init__` method  (the construtor) using the `self` keyword  (e.g. `self.attribute_name = value)
- Scope: Unique to each instances of the class. Each instance has its own copy of the instance attributes.
- Access: Can only be accessed using an instance of the class (e.g. `instance_name.attribute_name`)
- **Modification:** 
    Changes to an instance attribute only affect that specific instance. Modifying an instance attribute on one object will not impact other objects of the same class.
