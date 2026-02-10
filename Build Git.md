Implement fundamentals features like:
 - init
 - add
 - rm
 - status
 - commit
 - log

#### add
This command updates the index using the current content found in the working tree, to prepare the content staged for the next commit.
It adds the current content of the existing paths as a whole, but with some options it can also be used to add content with only part of the changes to the working tree file applied or remove paths that do not exist in the working tree anymore.

When we run `git add <file> ` , Git:
- Looks at the file in the working directory.
- Calculates a hash (SHA-1) of its content.
- Stores that content (called a blob) inside a special hidden directory. i.e. `.git/objects/`. 
- Updates an index file `(.git/index)` that tracks.
  - the file's path
  - the blob hash
  - and other metadata

### Git Refs and Git Head

Inside the `.git/` - the working folder outside is just a copy of what's stored here.

Two of the most important things inside `.git/` are:
- `.git/refs`
- `.git/HEAD`

They together tell Git "which commit we currently on" and where to write the next commit.

## 1. `.git/refs/` - References

refs are named pointers to commits.
Inside the `.git/refs/heads` we have one file per branch:
```
.git/refs/heads/main
.git/refs/heads/feature-x
```

Each of the file contains a commit hash
so, `refs/heads/main` points to the commit that currently the tip of the main branch.
`refs/tags/v1.0` could point to a commit tagged `v1.0`
**We need `refs/` because Git stores branches and tags as simple files containing commit hashes.**

## 2. `.git/HEAD` - What am I currently looking at?

`Head` is a special pointer - it tells Git what the currently working directory represents.

It usually contains a line like
`ref :refs/heads/main`
Means we are currently on the branch main

So when we commit, Git:
- Creates a new commit object.
- Updates the branch file `.git/refs/heads/main` with the new commit hash.
- Because `HEAD` points to that branch, the working directory now reflects that commit.

|File/Folder|Meaning|Example Contents|
|---|---|---|
|`.git/refs/heads/main`|Current commit hash for `main`|`a1b2c3d4e5f6...`|
|`.git/HEAD`|What you’re currently checked out on|`ref: refs/heads/main`|
|`.git/objects/`|The actual data blobs and commits|(compressed files)|

# Git HASH-OBJECT

It Reads the contents of file.txt.
Creates a header that says what type of object it is and how big it is.



## Hexdigest

Hexdigest is a method commonly found in cryptographic hashing libraries such as Python's `hashlib` module used to retrieve the hash value of data in a hexadecimal string format.

- Hashing Process: This function takes an input (e.g. a string, file content) and produces a fixed-size string of characters, known as hash or digest.


