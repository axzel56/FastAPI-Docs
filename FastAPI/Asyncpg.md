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
