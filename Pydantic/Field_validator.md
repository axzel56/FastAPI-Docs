
`field_validator` is a decorator used to define custom validation logic for specific fields within a `Pydantic` model.
It allows to perform checks. modify values, or raise `ValueError` exceptions if the data does not meet a certain criteria.

- Define a Pydantic Model
```python
class User(BaseModel):
	username : str
	age : int
	
```

- Create a validator function
-- Decorate a class method with `@field_validator('fieldname')`
-- The function takes the value of the field as the primary argument

-- Can also accept `info: FieldValidationInfo` to access additional validation

-- Perform validation logic within the function

-- Raise a `ValueError` if the validation fails

-- Return the validated value

```python

class User(BaseModel):
	username :str
	age: int
	
	@field_validator('username')
	@classmethod
	def validate_username(cls, v: str) -> str:
	
		if not v.isalpha():
			raise ValueError('User name must contain only alphabetical characters')
		return v.lower()
	
	@field_validator('age')
	@classmethod
	def validate_age(cls, v :int) -> int:
		if v < 0 or v > 120:
			raise ValueError('Age must be between 0 and 120')
		return v

```

Characteristic:

- Class methods: `field_validator` functions are defined as class methods, i.e. they can receive class `(cls)` as the first argument, not an instance. [Class Attribute VS Instance Attributes]
- Value argument: The value of the field being validated is passed as the second argument.
- Return value: The validator must return the validated value.
- Multiple fields: A single validator can apply to multiple fields by passing a comma-separated field names to the decorator e.g. `@field_validator('field1', 'field2')`.
- Modes: `field_validator` supports different modes `('before', 'after', 'plain', 'wrap')` to control when the validator runs relative to other validation steps. 'after' is default, running after Pydantic built-in type validation.


## Class Method `(@classmethod)`

- Has `cls` as the first parameter
- `cls` refers to the class itself,
- Can access :
	- class attribute
- Cannot directly access instance attributes
