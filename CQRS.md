CQRS Stands for - Command Query Responsibility Segregation, a design pattern that separates the models for reading data (queries) from models for writing data (commands).

- Used in event-driven architectures.

## Working

- Commands Service- These are requests to change the state of the system and do not return a value.
- Queries Service - These are the requests to read data from the system and do not change its state. They are sent to the "query side", which can use optimized read models.
- Segregation: The idea is to have 2 distinct models that can be optimized separately for their specific needs.
	-  For Example: A Write model focusing on data integrity and business logic, while read model could be a denormalized view optimized for fast queries.


Separating the methods for reading and publishing data is the primary goal of the CQRS architecture. 

Command Service (Command Model) ---> Writes Storage <- |
Query Service (Query Model) <-------------> Reads Storage<-|

CQRS provides distinct read and write operations.

- The write requests (commands) and read requests(queries) are processed independently.

# Basic Architecture

### Commands

- Commands are instructions that indicate a desired change in the state of an entity. These commands execute operations such as insert, update and delete.
- They do not return data but instead change the application server's state.
- Each command is an object containing the name of the operation along with the necessary data to perform the operations.
### CommandHandlers

- Command Handlers interpret the commands and return an event. This event can be a successful event or a failure event depending on the outcome of the command.

## Queries

- Query object returns data. Data retrieval techniques will only be comprised of queries.
- They are used to read data from the db and return it to the client for display in the user interface.
- The QueryHandlers interpret the queries and return query values.


# Sync Databases that follows CQRS pattern:


Client -> writes command using ui ->  that writes Databases (tables or Event Sourcing) -> Eventbus (Eventual Consistency) -> Read Database (Materialized View)

Client - Queries - Read Database

### Step 1. Write to the Command Databases:
- When making changes(create, update, delete) they are first saved in the command database. This database is optimized for handling write operations.
### Step 2: Generate Events:
- After the write operation, the system generated events that describes what changed. These events serve as notifications about the updates.

### Step 3: Update the Query Database:
- The read database, listens for these events and applies the changes to its own copy of the data. This way, the query db gets updated  with latest information

### Step 4: Eventual Consistency:
- The idea is that the query db doesnot have to update immediately. There can be a delay but eventually both db will sync.



# Scenario Example

Suppose a customer initiates a transaction
The System may check:
- Compliance checks
- FX and Fee Calculations
- Receiver Validation
- Payment Mode Availability
- Ledger Posting
- KYC/AML rules

These operations usually require multiple microservices communicating with each other.

That’s where **CQRS + Event-Driven Architecture** becomes powerful.

|Action|Description|
|---|---|
|Command|`CreateRemittanceTransaction`|
|Command Model|`Transaction` aggregate maintains business rules|
|Database|Normalized SQL (e.g., Postgres/SQL Server) optimized for writes|

# 2. Event Generation

`TransactionCreated` event is published
This event is placed into an event broker like:
- kafka
- RabbitMQ
- AWS SNS/SQS
- Azure Service Bus

Multiple microservices subscribe to these events:

Compliance Service        Validates AML/KYC rules
FX Engine                        Lock FX rate
Ledger Service                Prepare debit entry
Notification Service        Push alert to sender
Query DB Update           Updates Reporting Read DB

# 3. Query Database Updates

Q uery DB is optimized for: Fast search, Analytics, Dashboard display, Customer support tools, Agent Reporting

So it can be 
- ElasticSearch
- Mongodb
- Denormalized SQL Views
- Redis Cache
- Materialized Views

This data is projection - built from events
May not update instantly

# 4. Eventual Consistency

