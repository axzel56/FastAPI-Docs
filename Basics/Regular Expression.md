A Built in package which can be used to work with Regular Expressions.


### RegEx Functions:

The `re` module offers a set of functions that allows to search a string for a match.

- `findall` - Returns a list containing all matches
- `search` - Returns a `Match Object` if there is a match anywhere in the string
- `split` - Returns a list where the string has been split at each match
- `sub` - Replaces one or many matches with a string

A Match Object is an object containing information about the search and the result.

If there is no match, the value `None` will be returned, instead of the Match Object.

Example:

```python
import re
txt = "The rain in Spain"
x = re.search('ai', txt)
print(x) #prints an object
```

The match object has properties and methods used to retrieve information about the search and the results.

- `.span()` returns a tuple containing the start and the end positions of the match.
- `.string()` returns the string passed into the function
- `.group()` returns the part of the string where there was a match

something and a optional string like `-?` matches an optional minus sign.
? means 0 or 1 times
This allows negative numbers but not positive sign

\d+ 
Matches one or more digits
Ensures there is atleast one digit before any decimal point.

`(\.\d+)?`
This entire group id optional
`\.` literal decimal point
This matches a fractional part such as:
`.5` but only if preceded by digits

#excalidraw 


