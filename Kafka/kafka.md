### Kafka-Topic

`topic`: Which Kafka topic to send to (like choosing a mailbox)

A user defined category or feed name where data (messages) is published and stored as an ordered, immutable log.

Topics are the fundamental, append only unit of organization in kafka, acting like a specific topic folder or queue.
They are divided into partitions.

#### Key Characteristics:
- log Structure: Topics are essentially logs of events, where new messages are appended to the end, and existing cannot be modified.
- Partitions: Topics are divided into one or more partitions, which are log files distributed across `kafka` brokers. Partitions allow parallel processing, enabling multiple consumers to read from the same topic simultaneously.
- Replication: For high availability, partitions can be replicated across multiple servers(brokers). If a broker fails, another replica takes over.
- Messages and Offsets: Records in a partition are ordered and assigned a unique ID number called an offset.
- Retention: Data in a topic stored for a configured amount of time (7 days), allowing consumers to read at their own pace.

#### Operations:
- Produce: Application (producers) send records to specific topics.
- Consume: Application (consumers) subscribe to topics to read data.
- Management: Topics are created, modified or deleted using kafka-topics.sh CLI tool or similar administrative tools.


