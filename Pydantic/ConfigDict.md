A `TypeDict` for configuration `Pydantic` behaviour.


By default, Pydantic expects data in the form of dictionary. However when we fetch data using ORM like SQLAlchemy, we get Python Object
### title
`title: str | None`

The title for the generated JSON schema, defaults to the model's name

- `ignore` : providing extra data is ignored(the default)

```python

class User(BaseModel):
	model_config = ConfigDict(extra='ignore')
	name = str
	
user = User(name='Jane Doe', age = 30)
print(user)
```

- `forbid` Providing extra data is not permitted and a `ValidationError` will be raised if this is the case


### `from_attributes = True`

Allows to read data from an object (e.g. `user.email` instead of just a dict `user["email"]`)
