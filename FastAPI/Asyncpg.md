`Asyncpg` is a high-performance, asynchronous PostgreSQL client library for Python.
Specifically designed to work into Python's `asyncio` framework, enabling non-blocking database operations and enhancing application responsiveness, high concurrency and low latency.

```python

import asyncio
import asyncpg

async def main():
	conn = await asyncpg.connect(user='postgres', password='password', database='mydatabase', host='localhost')
	
	try:
		rows = await conn.fetch('SELECT id, name FROM users WHERE age > $1', 25)
		
```


### `async def` 

It makes the function asynchronous.

`async def get_weather(city)`

This means:
- The function returns a coroutine
- Must call it with await
- It can use `await` inside
It does not manage resources.

### `async with` 

It Manages async resources safely
`async with httpx.AsyncClient() as client:`

It ensures:
- Connections are opened properly.
- Connections are closed properly.
- Cleanup happens even if errors occur
- Connection pooling works correctly
