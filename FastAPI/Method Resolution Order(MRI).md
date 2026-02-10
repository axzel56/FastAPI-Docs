The sequence in which python searches for attributes or methods within a class hierarchy.
Particularly important in scenarios involving *Multiple Inheritance* , where the same method might be defined in several parent classes and MRO determines which one is used.

# The Core Principle of MRO

1. Child classes take precedence over their parent: The search starts in the class where the method is called and moves up the hierarchy.
2. Order of definition matters: Among sibling base classes, those listed first in the class definition have higher priority (L - R).
3. Each class appears only once. The MRO ensures no class is visited more than once.
4. Monotonicity: The relative order of classes is preserved in all subclasses.


`ClassName.mro()` - This method returns the MRO as a list.
`ClassName.__mro__` This attribute provides the MRO as a tuple.

