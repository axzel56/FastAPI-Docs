## Context Manager

Context Manager is an object that defines the runtime context to be established when executing a `with` statement. The Context manager handles the entry into and exit from the desired runtime context for the execution of the block of code.

The uses of the context managers include:
- Saving and Restoring various kinds of global state, locking and unlocking resources, closing opened files etc.
- 

- The Context Manager `__enter__()` is loaded for later use.
- The context manger's `__exit__()` is loaded for later use.
- The Context manager's `__enter__()` method is invoked.

## Types of Context Managers

Python's with statement supports the context of a runtime context defined by a context manager. 

### `contextmanager.__enter__()`

Enter the runtime context and return either this object or another object related to the runtime context. The value returned by this method is bound to the identifier in the `as` clause of with statements using the context manager.

