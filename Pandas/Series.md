`pandas.Series`

One-dimensional ndarray with axis labels (including time series)

Labels need not be unique but must be a hashable type. 
i.e.
A label (whether its an index entry or column name) must be a hashable type (immutable, can be used as a dictionary key)

Example of **hashable** types:
- `int` , `float`, `str`, `tuple` (if its elements are hashable)

Examples of **non-hashable** (invalid) types:
- `int`, `dict`, `set`, `list`

**Because:**
lists, dicts and sets can change after being created, so their hash value would be unstable

The object supports both integer and label-based indexing.

Operations between series (+, - , /, * , `**` `)`


## Parameters of Series

- data : array-like, iterable, dict, or scalar value: Contains data stored in Series. If data is a dict, argument order is maintained.
- index: array-like or Index(1d)
   Values must be hashable and have the same length as data. Non-unique index values are allowed. Will default to 

