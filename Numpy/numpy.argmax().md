
`numpy.argmax()` is used to return the indices of the maximum values along a specified axis of an array.

```python
numpy.argmax(array, axis=None ,out=None, keepdims = False)

```

## Parameters:

- array: The input or array-like structure (e.g. Python list).
- axis: An integer that specifies the dimension along which to find the maximum values. By default (`None`), the function flattens the array into a 1D array before finding the index.
- out: A location where the result is stored if provided.

## Examples:

#### 1D Array
```python
import numpy as np
arr_1d = np.array([1,5,2,9,4])
max_index = np.argmax(arr_1d)

print(f"The array: {arr_1D}")  # The array [1 5 3 4 9]
print(f"Index of maximum value: {max_index}")  # Index of maximum value: 3
print(f"Maximum value itself: {arr_1d[max_indesx]}")
# Maximum value itself: 9
```

#### 2D Array
For multi-dimensional arrays, the `axis` parameter dictates how the operation is performed.

```python
arr_2D = ```
```
arr_2D = np.array([[10, 17, 25], [15, 11, 22]])
```


### Axis 
Tells which direction to look

`axis -> 0` -> Column-Wise
`axis -> 1` -> Row-Wise
```python
b = np.array([1,5,2], [7,3,4])

```

