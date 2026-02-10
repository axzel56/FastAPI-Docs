```py
import os 

```


## OS- Module functions:

- Handling the Current Working Directory
- Creating a Directory
- Listing out Files and Directories with Python
- Deleting Directory or Files using Python
- File Permissions and Metadata

`os.getcwd()` -> Gets the location of the current working directory.

```python
import os
cwd = os.getcwd()
print("Current working directory", cwd)
```

- `os.chdir()` -> It takes the target target directory as its only argument and switches the context to that folder.
-  `os.mkdir()` -> It is used to create a directory named path with the specified numeric mode. 
   -  This method raises `FileExistError` 
- `os.listdir()` -> This lists all the files and directories in the root directory "/".
- `os.remove()` -> This method is used to remove or delete a file path. This method cannot remove or delete a directory.
- `os.rmdir()` -> This method is used to remove or delete an empty directory.
     - `OSError` will be raised if the specified path is not an empty directory.


## File Permissions and Metadata

For Scripting, administration and system-level tasks.
Three important methods are:
- `os.chmod()` - Change file or directory permissions 
- `os.chown()` - Change file owner and group
- `os.stat()` - Fetch metadata like file size, modification time, permissions etc.


### os.chmod()

`os.chmod()` method is used to change the permissions(read, write, execute) of a file or directory.
Permissions must be passed in octal format (e.g. 0o600).

```python
os.chmod("fileName", Permission i.e mode)
```
****Explanation: 0o600**** means:

- Owner: Read & write
- Group: No permission
- Others: No permission


`os.popen()` method opens a pipe to or from command.
The return value can be read or written depending on whether the mode is 'r' or 'w'.

```python
os.popen(command[.mode[,bufsize]])
```



## os.stat()

`os.stat()` method is used to retrieve metadata about a file such as its size, permissions and timestamps.

```python
import os

stats = os.stat("example.txt")

print("Size:", stats.st_size, "bytes")
print("Last modified:", stats.st_mtime)
print("Permissions:", oct(stats.st_mode)[-3:])
```


# The [-3:] syntax:

[-3:] is a slice, and it works on sequences - things like:
- strings ("hello")
- lists `([1,2,3,4])`
- tuples `((1,2,3,4))`

Its a built in syntax, not a function or a method.


The general form is:
```python
sequence[start:end]
```


start -> the index to begin from (inclusive)
end -> the index to stop before (exclusive)


Can also omit either sides:

- `[:end] `-> from the beginning to `end - 1`
- `[start:]` -> from start to the end
- `[:] ` -> the whole thing

Here:

- `oct(stats.st_mode)` returns a **string**, like `'0o100644'`
    
- `[-3:]` slices the **last 3 characters** → `'644'`


`exist_ok`
`exist_ok `parameter in `os.makedirs()` is a boolean argument that controls the behavior of the function when the target directory already exists.


This will raise a `FileExistsError`. This is a default behavior and ensures that we don\`t accidently overwrite or interact with an existing directory without explicit intent.



