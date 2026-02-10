
Needed when we need or want to return some data that is not exactly what the type declares.

For Example:
We could want to return a dictionary or database object but declare it as a Pydantic Model.

```python

from fastAPI import FastAPI

app = FastAPI()

class Item(BaseModel):
	name: str
	description : str | None = None
	price : float
	tax : float | None = None
	tags : list[str] = []
	
	
@app.post("/items/", response_model=Item)
async def create_item(item: Item) -> Any:
	return item
	
@app.get("/items", response_model=list[Item])
async def read_items() -> Any:
	return [
		{"name" : "Sunglasses", "price": "FK15000"},
		{"name": "Another Sunglasses", "price": "1900"}
	]
```

`response_model` receiver the same type we would declare for a Pydantic model field, so it can be Pydantic Model, but it can also be `List` of pydantic model like` List[Item]`
