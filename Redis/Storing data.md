Redis is an in-memory data store, it stores data primarily in RAM for fast read and write operations.

It organizes data using key-value pairs, where keys are unique identifiers and values can be of various types such as strings, lists, sets, sorted sets, hashes, bitmaps and more.

Data in Redis is accessed by hashes, bitmaps and more.

# Data structures in Redis

Redis supports a wide range of data structures, making it a versatile data store. These data structures include:

- Strings: Basic key-value storage for text or binary data.
- Lists: Ordered collections of strings, allowing for operations like push, pop, and range retrieval.
- Sets for unordered collections of unique strings with set operations like union, intersection and difference.
- Sorted Sets: Sets with associated scores used for ranked data.
- Hashes: key-value pairs within a key, suitable for storing structured data.
- Bitmaps: Storing and Manipulating binary data.

## Partitioning in Redis
- Provides horizontal sharding for distributed data across multiple instances. Useful for handling large datasets and achieving high throughput.

# Database Sharding

Database sharding is a technique for horizontal scaling of databases, where the data is split across multiple database instances or shards to improve performance.

1. Key Based Sharding: Take the value of an entity such as customer ID, customer email, IP address of a client, zip code etc and use this value as an input of the hash function
2. Horizonal sharding
3. Vertical Sharding
4. Directory - Bases Shrading


# I/O Multiplexing

(apparent concurrency)

- Implementation of event loops

IO System calls are blocking.
e.g. reading from a socket - `read()` blocks until other person sends.
