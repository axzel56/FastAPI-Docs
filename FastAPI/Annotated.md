
"Annotated" is a way to indicate the intended data types of variables, function parameters, and function return values. While Python is dynamically typed and does not enforce annotations at runtime, they serve as valuable metadata for several purposes:

- **Readability and Maintainability:** Type annotations make code easier to understand by explicitly stating the expected types, improving clarity for other developers and your future self.

## Annotated With Depends

`Annotated` from the `typing` module is used in conjunction with `Depends` to declare and manage dependencies in a clear and type-safe manner.

``` python
from typing import Annotated
from fastapi import Depends, FastAPI, Header

app = FastAPI()
def get_current_user_id(authorization: Annotated[str, Header()]) -> int:
	if authorization = "Valid Bearer token":
	return "userID"

#Reusable dependency tye alias
UserIDDep = Annotated[Int, Depends(get_current_user_id)]

@app.get("/items/")
async def read_items(user_id: UserIDDep):
	return {me}
	
```

1. `Annotated` for Metadata: 
	- Allows to attach metadata to a type.
	- The first argument to `Annotated` is the actual type and subsequent arguments are metadata.

 
