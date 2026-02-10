
- int
- float
- bool
- bytes


# Generic Types

- dict
- list
- set 
- tuple  - unchangeable, allow duplicates, Ordered

### Optional Type

`Optional[x]` means:
This value can either be of type `X` or `None`.

```python 
def get_name(user_id : int) -> Optional[str]
# same as
def get_name(user_id: int) -> str | None
```

Both means the function might return a string "Alice" or might return None.

