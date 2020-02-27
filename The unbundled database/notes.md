# The unbundled database
Leveraging the unbundled database via distributed logs and stream processing.

## Microservices
- Allow scaling independently. 

### How do services share data ?
- Service interface (e.g. rest api)
    - Goal is to clearly separate concerns between services and define different bounded contexts.
    - Good if you want to get one data, but bad for transferring data at scale.
    - Synchronizing changes are hard.
- Messaging Middleware (e.g. RabbitMQ)
- Shared databases (don't do that) - Functionnality is encapsulated within the services, data is not.

### Data diverges overtime
Different services make different interpretations of the data they consume, which leads to divergent information.

## Event driven services
### Ways services interact
- Commands: Commands are action in the form of side effect generating requests indicating some operation to be performed by another service.

- Queries: Request to look up data points

- Events: Events can be thought of are both a fact and a trigger. They express something that has happened, usually in the form of a notication.
    - I broadcast what I did ! Broadcast events to a centralized, immutable stream of facts.

### Advantages
- State transfer: Events are both triggers and facts, that can be used to notify and propagate entity state transfers.
- Decoupling: Both data producers and consumers are completely decoupled. There is no API binding them together, no synchronized changes that neeed to be performed. 
- Locality: Queries and lookup are local.

### The single writer principle
- A single service owns all events for a single type
    - Having a single code path helps with data quality, consistency and other data sharing concerns. 

## Distributed log
### What's a log ?
- Ordered immutable sequence of records that is continuously appended to. 

### Kafka: Distributed streaming system
- Publisher/Subscriber
- Storage: Stores streams of records using replicated, fault-tolerant and durable mechanisms.
- Processing: Kafka can process and apply logic to streams of records as they occurs.

### Kafka: The Broker
- Linearly scalable: Horizontal scaling
- Resilient: Retries, Message ACKnowledgement, ACK strategies are all baked into the platform.
- Fault tolerant: Messages are replicated across different nodes. 

### Kafka: Topics and Partitions:
- Topics: Subject
- Partition: A topic is splitted into multiple partitions. Each message is assigned a sequential id called an offset. Act as the unit of the parallelism

## Kafka log semantic
### Ordering guarantees
- Relative ordering: messages that require relative ordering must be sent to the same partition
- Global ordering: Single partition topic.

### Kafka can balance services
- If a consumer leaves a group for a reason, kafka will detach it and re-balance how message are distributed accross remaining consumers.

### Compaction
- Key-based datasets can be compacted. Compacted topic retains only the most recent events with any old events removed for a key. (e.g in the global queue there is message [A12 B23 A22 C1 B24]; the compact queue will be [A22, C1, B24])

### Topic durability
- Kafka can be used as a long-term storage layer.
    - If you set the retention to forever or enable log compaction on a topic, data will be kept for all time. 

### Public / Private topics
- Public and private topics should be separated from each other.
    - Some teams prefer to do this by convention, but a stricter segregation can be applied using the authorization interface. 

### Schema registry
- Always use schemas to promote a durable, shareable contract between producers and consumers. 

## Unbundled database
### Why Acid ?
ACID is old school! *What* consistency do you really need and *when* ?

Acid 2.0 is:
- Associative
- Commutative
- Idempotent
- Distriuted

References to [ACID 2.0](http://swarmdb.net/articles/acid2/)

### Cool DB Features
- Views
- Indexes 
- Materialized Views

**Unbundled database** separate concerns into different layers. Creating service specific views.  Unbundled data offer an approach where trade offs between reads and writes are no longer needed.

**Rethinking the materialized view**: Can we think of MV as continuously updated caches ?

## Stream processing
- Kafka streams
    - Low ovehead
    - Java based
    - Stream processing meant to run as part of the application
- Akka
    - Scala / Java implementation of reactive streams. 
- Apache Flink
    - Clustered stream processing engine
    - Handles high data volumes 1M/sec
- Apache Spark
    - Cluster computing framework with the largest global user base. 

[Complete presentation](https://cdn.oreillystatic.com/en/assets/1/event/307/Leveraging%20the%20power%20of%20the%20unbundled%20database%20Presentation.pdf)