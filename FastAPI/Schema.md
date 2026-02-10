FastAPI generates a schema with all the API using the OpenAPI standard for defining APIs.

A schema is a definition or description of something. Not the code that implements it, but just an abstract description.

API Schema is a specification that dictates how to define a schema of your API.


Enum in Python

Enumerations or Enums is a set of symbolic names bound to unique values. It can be iterated over to return its canonical members in definition order.

Properties of Enum
- Enum can be displayed as string or `repr`
- Enums can be checked for their types using `type()`
- The "name" keyword is used to display the name do the enum member

```python

from enum import Enum
class Season(Enum):
	SPRING = 1
	SUMMER = 2
	AUTUMN = 3
	WINTER = 4
print(Season.SPRING)     # Season.Spring
print(Season.SPRING.name) # SPRING
print(Season.SPRING.value) # 1
print(type(Season.SPRING)) # <enum 'Season'>
print(repr(Season.SPRING)) # <Season.SPRING : 1>
print(list(Season)) # [<Season.SPRING: 1>, <Season.SUMMER: 2>, <Season.AUTUMN: 3>, <Season.WINTER: 4>]
```

Accessing with value:
`Season(2).name` # SUMMER

Accessing with name: 
`Season['AUTUMN']` # 3

Iterating:

``` python
for season in (Seasons):
	print(season.value, "-", season)
```

