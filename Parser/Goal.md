To create a JSON Parser in Python to understand parsing, tokenization and data structures.

## JSON Syntax:

- Objects - `{key: value, ...}`
- Arrays - `[value, ...]`
- Values - string, number, object, array, boolean, null

## 2 Steps Approach

- Tokenization: Convert the JSON string into meaningful symbols like `{, }, strings, numbers` etc.
- Parsing: Recursively convert tokens into Python data structures.


1. Overview - Understanding JSON Parsing goal and structure.
2. Tokenizer - Build a scanner that converts text into tokens
3. Parser Core - Convert tokens into Python objects recursively.
4. Error Handling - Handle whitespace, unicode and escape sequences.
5. Testing

## Escape Sequence in JSON

These sequences begin with a backslash `\` and are used to ensure that the JSON data remains valid and can be correctly parsed, even when it contains characters that would otherwise break the structure (like double quotes or backslashes themselves).

- `\"`  : Represents a double quote character.
- `\\` : Represents a backslash character `(\)
- `\/` : Represents a forward slash character `(/)` 
- `\b`: Represents a backspace character
- `\f`: Represents a form feed character
- `\n`: Represents a newline character
- `\r`: Represents a carriage return character
- `\t`: Represents a tab character


#excalidraw 