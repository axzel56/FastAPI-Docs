`from fastapi import APIRouter`

```python
class fastapi.APIRouter(
)
```


`APIRouter` class used to group path operations, for example to structure an app in multiple files. 

```python
from fastapi import FastAPI
fastapi = FastAPI()
router = APIRouter()

@router.get("/users/", tags='["users"])
async def read_users():
	return ["username" : "Alicia", {"username": "Alice"}]
```

`tags` are used to organize and group related path operations (endpoints) in the automatically generated interactive API documentation, such as Swagger UI and Redoc.
- We can assign one or more tags to individual path operations using the `tags` parameter in the path operation decorator.
- On APIRouter -  When organizing application into multiple files using `APIRouter`, we can apply tags to the entire router, and these tags will be inherited by all path operations defined within that router.


Tags can be added in the path operation, pass the parameter `tags` with a list of str
```python
from fastapi import FASTAPI
from pydantic import BaseModel

app = FASTAPI()

class Item(BASEModel):
	name : str
	description : str | None = None
	price : float
	tax : float | None = None
	tags : set[str] = set()
	
@app.post("/items/", response_model=Item, tags= ["items"])
async def create_item(item: Item):
	return item

@app.get("/items/", tags=["items"])
async def read_items():
	return [{"name": "Foo", "price": 42}]
	
@app.get("/users/", tags["users"])
	return [{"username": "johndoe"}]
```

They will be added to the OpenAPI schema and used by the automatic documentation interfaces:
![[Pasted image 20251129222434.png]]

### Tags with Enums

```python
from enum import Enum
from fastapi import FastAPI

app = FastAPI()

class Tags(Enum):
	items = "items"
	users = "users"
	
@app.get("/items/", tags=[Tags.items])
async def get_items():
	return ["Portal gun", "Plumbus"]

@app.get("/users/", tags=[Tags.users])
	return ["Rick", "Morty"]
```

