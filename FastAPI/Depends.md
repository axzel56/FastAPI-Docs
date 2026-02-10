Fast API has a very powerful  Dependency Inject system
It is designed to be very simple to use, and to make it easier for any dev to integrate other components with FASTAPI.

**Dependency Injection** means that there is a way for the code to declare things that it requires to work and use: "dependencies".

Dependencies Injection is a design pattern where a component declares its requirements(dependencies), and an external system (FastAPI) is responsible for providing those dependencies. Instead of a function creating its own dependencies, they are injected into it.

And then FastAPI will take care of doing whatever is needed to provide the code with those needed dependencies ("inject" the dependencies).

### Depends()

Dependencies are handled mainly with the special function `Depends()` that takes a callable.

## Declare Dependencies

We define functions or classes that represent the dependencies. These can handle tasks like fetching user data, establishing database connections, or performing authentication.

Example:
```python
from typing import Annotated
from fastapi import Depends, FastAPI

app = FastAPI()

async def common_parameters(q: str | None = None, skip: int = 0, limit : int = 100):
	return {"q" : q, "skip": skip, "limit" : limit}
	
@app.get("/items/")
async def read_items(commons : Annotated[dict, Depends(common_parameters)]):
	return commons
```

