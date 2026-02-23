### Core Components:

1. Postmaster (Server Process)
	  Manages client connections, starts backend processes, handles config and logging.
2. Backend processes
	  Each client connection gets its own backend process (unlike thread-based DBs)
3. Shared Buffers and Memory
		PostgreSQL caches frequently accessed data in shared memory to reduce disk reads
4. Write-Ahead Log (WAL)

### MVCC (Multiple-Version Concurrency Control)

- In a db, multiple clients can read and write at the same time.
- Traditional locking can cause: Readers blocking writers, writers blocking readers, deadlocks

#### How MVCC Works:
- Each transaction sees a consistent snapshot of the db at the start.

- Readers never block writers and writers never block readers.
- When a row is updates, a new version is created, old versions are kept for transactions tat still needs them.
- Old versions are cleaned up later via VACUUM.

- PostgreSQL supports multiple isolation levels:
		Read Committed, Repeatable Read, Serializable.

#### Each client gets its own backend process

When a client connects, PostgresSQL forks a separate process called a backend process to handle that connection.
Each backend process:
- manages all queries for that client.
- Maintains its own memory context.
- Communicates with shared memory for caching and WAL.
