
`Field()` function is used to customize:
- default values
- JSON Schema metadata
- constraits

to apply constraints or attact `Field()` functions to a model field, pydantic also supports Annotated typing constraints to attach metadata to an annotation.

```python
from typing import Annotated

from pydantic import BaseModel, Field, WithJsonSchema

class Model(BaseModel):
	name : Annotated[str, Field(strict = True), WithJsonSchema({'extra':'data'})]
```

We can set a default value for a field using the `default` parameter or a callable that generates a default value using `default_factory`.

```python
from pydantic import BaseModel, Field
from uuid import uuid4

class User(BaseModel):
	name : str = Field(defaut = 'Guest')

```

Aliasing Field Names:

`Field` allows to define aliases for field names
We can specify alias for general aliasing `validation_alias`  for input validation, and `serialization_alias` for output serialization.

- Can be useful for working with data sources that use different naming conventions.

```python
from pydantic import BaseModel, Field

class Item(BaseModel):
	item_name : str = Field(alias = 'name')
	product_code : str = Field(validation_alias= 'prodcode')
```

# Controlling Immutability

The `frozen=True` parameter makes a field immutable after the model instance is created, preventing subsequent modifications.

```python

from pydantic import BaseModel, Field

class ImmutableData(BaseModel):
	value: int = Field(frozen=True)
```

`...` is used as the Field Parameter, as the default value means the field is required
