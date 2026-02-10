Uvicorn is a fast python web server that runs ASGI application.

	Uvicorn is the program that listens for HTTP requests and passes them to the Python app, then sends responses back to the client.

### Why does Uvicorn exist?

Older Python web apps used WSGI (like Django + Gunicorn)

```chart
Browser / Client --(HTTP)-> Uvicorn --(ASGI) --> FastAPI / Starlette --> (Code base)
```

`Uvicorn` just accepts requests, manages event loops, calls the app and return responses.

Uvicorn Does the following:
1. Opens a socket (IP + port)
2. Accepts incoming connections
3. Parses HTTP requests
4. Runs an async event loop (via `asyncio / uvloop`)
5. Calls the ASGI app
```python
await app(scope, receive, send)
```
6. Sends the response back


