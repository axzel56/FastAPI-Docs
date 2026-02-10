
# SQL ORM


## Declarative Mapping

Declarative Mapping is the modern, primary method for defining both user-defined Python classes and their corresponding db table structures simultaneously in a single, cohesive definition.

- `ORM` : It is a core part of the SQLAlchemy ORM, used as gap between OOP Python classes and relational databases tables.
- `DeclarativeBase` : It involves creating a base class by subclassing `DeclarativeBase`. All mapped model classes then inherit from this base. (Maps classes to table)
- `Mapped` and `mapped_column()` : Type annotations using the `Mapped` generic type and the `mapped_column()` function are used to define columns and their properties (e.g. data type, primary key, nullability). 
- `MetaData` : The declarative base class has a `metadata` attribute, which is a collection that stores all the defined table schemas. This object is used to generate the actual database tables.

```python
from typing import List
from sqlalchemy import ForeignKey, String
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column, relationship

class Base(DeclarativeBase):
	pass
	
class User(Base):
	__tablename__ = "user_account"
	
```

# Session Object

`Session` object is the primary interface for Object-Relational Mapping(ORM) operations, acting as a workspace that manages persistence operation and tracks changes to objects within a single db transaction.

## Concepts and Functionality

- Unit of Work Pattern: The `Session` implements the unit of work pattern. It collects all pending changes (e.g. object additions, modifications, deletions) in memory and only flushes them to the db when explicitly commanded, typically via `session.commit()` or `session.flush()`. This ensures data integrity by treating a series of db actions as an atomic unit.
- Identity Map: The session maintains an identity map, a local cache that ensures a unique Python object instance corresponds to a specific database row within that session.
- Transaction Management: A `session` encapsulates a db connection and manages transactions. A transactions automatically begins when the session is first used and remains active until it is committed or rolled back.
- Object state management: The session tracks the state (pending, persistent, detached, deleted) of ORM-mapped objects, automatically generating the necessary SQL `INSERT`, `UPDATE`, or `DELETE` statements as needed.

# Sessionmaker

`sessionmaker` is a configurable factory used to generate `Session` objects. It's the standard, recommended way to create sessions in ORM-based applications as it allows configurable options (like the bound engine, autoflush settings, etc) to be defined in one place.

### Purpose and Usage

- Factory Pattern: `sessionMaker` follows the factory pattern, which centralizes the logic for creating new `Session` instances with a consistent configuration.
- Configuration: Instead of repeatedly passing configuration arguments (e.g. `bind, autocommit, expire_on_commit`) every time a session is created, you configure the `sessionmaker` once, typically at a global or module level in application's  setup.
- Thread Safety: While `session` objects are not thread-safe and should be local to a single request or function call, the `sessionmaker` factory is thread-safe and can be concurrently by multiple threads to create distinct `Session` objects.

```python
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker

# 1. Create an Engine (typically done once at the start of the application)
#    The engine manages the connection pool and dialect
engine = create_engine("sqlite:///mydb.db")

# 2. Create a sessionmaker factory, bound to the engine
# This is also typically done once at a global/module level
Session = sessionmaker(bind=engine)

# 3. Create and use a new Session object for a specific operation
# Each call to Session() creates a new, independent session
with Session() as session:
	# Add objects to the session
	# session.add(some_object)
	# Commit the transaction
	session.commit()
# The session is automatically closed upon exiting the 'with' block
```

### Key Methods

| Member Name   | Description                                                                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `__call__()`  | Produces a new `Session` object using the factory's configuration (e.g. `session = Session()`).                                                             |
| `begin()`     | A context manager that produces a new `Session` and automatically manages the transaction, committing upon success or rolling back in case of an exception. |
| `configure()` | Allows to reconfigure the arguments for an existing `sessionmaker` instance, such as binding it to a new `Engine` later in the application lifecycle.       |


- `options()` lets us control how column/relationships are loaded


# Note: scalars() turns row into objects; .all() puts them in a list
# Declarative vs Imperative Mapping

### Imperative Mapping

Imperative Mapping is procedural. 
Step-by-step instructions telling the machine how to move and transform the data.

```python
from sqlalchemy import Table, Column, Integer, String, MetaData
from sqlalchemy.orm import registry

reg = registry()
metadata = MetaData()

user_table = Table(
	"user_account",
	metadata,
	Column("id", Integer, primary_key=True)
	Column("name", String)
)

Class User:
	pass

reg.map_imperatively(User, user_table)

```

### Declarative Mapping

Declarative Mapping is functional. 
It defines the relationship between source and the target fields.

Declarative Mapping in `SQLAlchemy` allows to define python class and the database table metadata in one single place.

```python
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column

class Base(DeclarativeBase):
	pass

Class User(Base):
	__tablename__ = "user_account"
	
	id: Mapped[int] = mapped_column(primary_key=True)
	name: Mapped[str]
```

# Declarative Base

Declarative Base is a Master Template or Grand Blueprint.

Python speaks the language of Objects (a language of classes and variables.)
Declarative Base acts as a translator and organizer.

# Engine

Engine is a factory that can create a new database connections, also holds onto connections inside of a *Connection Pool* for fast reuse.

```python
from sqlalchemy import create_engine
engine = create_engine("url")

```

# Simple SELECT

to create a simple select object, which we then invoke using a `Session`.
This method is useful for querying for ORM objects.

`Session.scalars()` method returns a `ScalarResult` object that will iterate through the ORM objects  we've selected.

```python
from sqlalchemy import select
session = Session(engine)
stmt = select(User).where(User.name.in_(["sandy", "sandy"]))

for user in session.scalars(stmt):
	print(user)
```

- Output:
```
User(id=1, name='spongebob', fullname='Spongebob Squarepants')
User(id=2, name='sandy', fullname='Sandy Cheeks')
```

`ColumnOperator.in_()` method is like SQL IN Operator.


----------------------------------------------------

# `SQLAlchemy Core VS SQLAlchemy ORM`

1. `SQLAlchemy Core (The Engine Room)`
`SQLAlchemy` Core is centered around the SQL Expression Language. 
Provides pythonic way to write SQL queries without writing raw strings, but still follows the logic of relational databases (tables, rows and columns).

- Logic - Interact with the Table objects.
- Result - Queries return `Row` objects which behave like tuple or dictionaries.
- Key Components: Table, Column, select()

2. `SQLAlchemy ORM(The Object Mapper)`
	ORM sits on top of Core. It allows to map database tables to Python classes. Instead of thinking about "rows" we think about "objects"
	 (e.g. a `User` object).

- Logic: We interact with Python classes and instances.
- Result: Queries return instances of the classes (e.g. `[User(id=1, name='Alice')]`)
- Key Components: `declarative_base, Session` classes


# ORM

## Relationships

ORM relationships define connections between mapped Python classes, allowing us to work with related data using object attributes instead of writing complex SQL joins. These relationships are established using the `relationship()` function and rely on underlying database foreign keys for data integrity.

- `relationship() function`: This is the core function used in the ORM to declare a linkage between two classes (models). It tells `SQLAlchemy` how to automatically fetch associated objects.
- `ForeignKey`: `ForeignKey` constraints is used at the database schema level to enforce the link between tables
- `back_populates / backref` : These parameters create a bidirectional relationship, allowing us to access related objects from both sides of the association. It is the modern approach and requires defining the relationship on both classes, specifying the name of the attribute on the other side.


### Types:

- One to One: A single object in one class is linked to a single object in another class. This is achieved by adding a unique constraint on the foreign key column and setting `uselist=False` in the `relationship()` definition on the `"one"` side.
	 a record in Table A can have only one matching record in Table B, and vice versa.
	 Usually the primary key of one table is also a foreign key in the other, or they share the same primary key.

- One to Many: A record in Table A can be associated with Multiple records in Table B, but a record in Table B is associated with only one record in the Table A.
		A Customer and their orders- A customer can place many orders, but each order is tied to only one specific customer.
		We place the Foreign Key on the Many side (e.g. `Order` table contains a `customer_id`)

- Many to Many: A record in Table A can relate to many records in Table B, and a record in Table A
		Student and classes. A student can enroll in many classes and a class can contain many students.
		We cannot link these 2 tables, we must use a Junction Table (also called a Mapping or Associative Table) that sits betn and holds foreign keys for both.

|**Relationship**|**Table A**|**Table B**|**Common Solution**|
|---|---|---|---|
|**One-to-One**|1 instance|1 instance|Shared Primary Key or Unique Foreign Key|
|**One-to-Many**|1 instance|Multiple instances|Foreign Key in Table B|
|**Many-to-Many**|Multiple instances|Multiple instances|Junction Table (A_B_Mapping)|

#### `back_populates`
With `back_populates`, `SQLAlchemy` keeps both sides in sync.
- If we set `item.owner = my_user`, then `my_user.items` will automatically include that item.
- If we append an item to `my_user.items.append(new_item)`, then `new_item.owner` is automatically set to `my_user`.

```python
class User(Base):
	__tablename__ = "users"
	id = Column(Integer, primary_key=True)
	# items refers to the attributes in the Item class
	items = relationship("Item", back_populates="owner")
	
class Item(Base):
	__tabelname__ = "items"
	id = Column(Integer, primary_key=True)
	# owner refers to the attribute in the User class
	owner = relationship("Users", back_populates="items")
```


Example:

- One to Many relationships using User and Posts relationship

```python
from sqlalchemy import Column, Integer, String, ForeignKey from sqlalchemy.orm import relationship, declarative_base Base = declarative_base()

class User(Base):
	__tablename__ = "users"
	id = Column(Integer, primary_key=True)
	username = Column(String)
	
	#Says: Find the 'author' attribute in the Post class
	posts = relationship("Post", back_populates= "author")
	
class Post(Base):
	__tablename__ = "posts"
	id = Column(Integer, primary_key=True)
	title = Column(String)
	user_id = Column(Integer, ForeignKey("users.id"))
	
	# Says: Find the 'posts' attribute in the User class
	author = relationship("User", back_populates = "posts")
```


## `offset`

`offset()` method on a query object or `select()` statement to skip a specified number of rows in the results.
Typically used in combination with `limit()` for pagination.

```python
stmt = select(User).order_by(User.id).offset(10).limit(5)
# or

db.query(self.model).offset(skip).limit(limit).all()
# select users, skip the first 10, then take the next 5
```
- limit tells the db the max number of records to return in a single request.
- 