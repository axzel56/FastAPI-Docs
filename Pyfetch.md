A function within the Pyodide and PyScript environments used for making asynchronous HTTP requests in a web-browser.

`pyfetch()` in the `pyodide.http` module is a Python wrapper around the browser's native JS `fetch()` API.

It allows code running in the bowser to make non-blocking asynchronous network requests to fetch resources from the web.

It's an async function so it must be used with `async/await` syntax.

- It Leverages the browser's networking stack, supports streaming and request cancellation and returns a `FetchResponse` object with methods to convert the response body to Python types (e.g. `await response.bytes(), await response.json()`)

# Pyodide
#### Limitations:
Due to browsers security constraints and WebAssembly's sandboxed environment, standard Python networking libraries have several limitations.

- No raw socket access: Browser security prevents direct socket operations.
- CORS restrictions: Cross-origin requests are limited by browsers CORS policies.
- No synchronous networking in main thread: Traditional blocking HTTP calls can freeze the browser UI
- Limited protocol support: Only HTTP/HTTPS protocols are available, no TCP/UDP sockets.


