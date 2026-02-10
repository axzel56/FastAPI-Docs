The `argparse` module in Python is a standard library module designed to simplify the creation of user-friendly command-line interfaces (CLI). It allows us to define the arguments your program expects.


Creating a Parser:
We begin by creating an `ArgumentParser` object
```python
import argparse
parser =  argparse.ArgumentParser()
```

The Argument Parser store all the necessary information that has to be passed from the python command-line.
- Object for parsing command line strings into Python objects.

-prog -- The name of the program (default: `os.path.basename(sys.argv[0])`)
-description - A description of what the program does
-epilog -- Text following the argument descriptions
-parents -- Parses whose arguments should be copied into this one


## SubParsers:

A **subparser** is a component of `argparse` that lets a command-line program have **multiple subcommands**, each with its own arguments and help

`add_subparsers()` on the main parser object method returns a special action object that can be used to create individual subcommand parsers.

```python
subparsers = parser.add_subparsers(dest='subcommand', help='Available subcommands')
```

- `dest='subcommand'` specifies the attribute name where the name of the invoked subcommand will be stored in the parsed arguments.
- `help` provides a description for the `subparsers` in the help message.


### parse_args()

`parser.parse_args()` → reads **what the user typed in the terminal**.
`args = parser.parse_args()`

By default,` parse_args()` reads the command-line arguments from `sys.argv` (i.e., what you typed in the terminal).
