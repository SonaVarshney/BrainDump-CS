##  **Kafka Architecture**

---

###  Kafka: High-Level Overview

When you send or receive data using Kafka, here's **what's happening under the hood**:

```
Producer → Topic → Partition (in a Broker) → Consumer Group
```
![image](https://github.com/user-attachments/assets/d577733f-4293-4fff-9618-b81dc533f98b)

Each component has a role. Let’s break it down 

---

###  1. **Kafka Broker**

* A **Kafka broker** is a **server** that stores data and serves client requests.
* A **Kafka cluster** usually has **multiple brokers**.
* Each broker handles:

  * **Read/write requests** from producers & consumers
  * **Storing data** in partitions of topics

 **Think of it like:** a post office. You can send and receive messages through it, but you don’t care how it’s managed.

---

###  2. **Topics & Partitions**

* A **topic** is like a named category (e.g., `"order_placed"`, `"user_signup"`).
* Topics are **split into partitions** for **parallelism** and **scalability**.

For example:

```
Topic: user_logs
Partitions:
- Partition 0 → on Broker 1
- Partition 1 → on Broker 2
- Partition 2 → on Broker 3
```

Each **partition** stores messages **in order**, and each message gets a unique **offset**.

 **Think of a partition** as a log file that gets written to from one side only.

---

### 3. **Producer**

* Sends data **to a topic**.
* Can specify **which partition** to write to (default is round-robin or based on a key).
* Kafka **acknowledges** once the message is stored.

 Example: A service that pushes website clicks to Kafka.

---

###  4. **Consumer**

* Reads messages **from a topic**.
* Tracks **offsets** to know which messages it has read.
* Can be part of a **consumer group** (for parallelism).

Example:

```
Consumer Group: analytics_service
- C1 reads from partition 0
- C2 reads from partition 1
```

 **Offset = like a bookmark** in your Netflix show. You can come back where you left off.

---

###  5. **Consumer Group**

* A group of consumers **working together**.
* Kafka ensures that **each partition is read by only one consumer** in a group.
* Multiple groups can read the same topic **independently**.

---

###  6. **Replication**

* Kafka replicates partitions across multiple brokers to ensure **fault tolerance**.
* Each partition has:

  * 1 **Leader** broker
  * N **Followers**

Only the **leader** handles read/write. If it fails, a **follower** is elected leader.

---

##  Kafka + Zookeeper vs KRaft Mode

* **Zookeeper**: Earlier Kafka required it for broker coordination.
* **KRaft mode**: Newer Kafka versions (3.3+) can run without Zookeeper — faster, simpler.
---
<br>
<br>
<br>

## How Messages Flow in Kafka: Producer to Consumer

### Step 1: Producer Sends Message

A producer application sends a message to a Kafka topic using the Kafka client library. The message could be in JSON, Avro, or another format.

Example message:

```json
{ "user_id": "123", "event": "login", "timestamp": "2025-07-01T18:30:00" }
```

### Step 2: Kafka Assigns the Message to a Partition

Kafka assigns the message to one of the topic's partitions:

* If a key is provided, it uses a hash of the key to choose a partition.
* If no key is provided, Kafka typically uses round-robin distribution.

Each partition is an ordered, immutable sequence of messages.

### Step 3: Broker Stores the Message

The broker hosting the partition writes the message to disk. The message is now durable.

### Step 4: Replication

Kafka ensures that messages are replicated to other brokers for fault tolerance. Each partition has:

* One leader broker (handles read/write)
* One or more follower brokers (replicas)

Followers replicate messages from the leader.

### Step 5: Consumer Subscribes to the Topic

A consumer or a consumer group subscribes to the topic. Kafka assigns partitions to consumers:

* If consumers are in a group, each partition is assigned to only one consumer.
* Multiple groups can read the same topic independently.

### Step 6: Consumer Polls and Processes Messages

Consumers fetch (poll) new messages from their assigned partitions. Messages are delivered in the order they were written within a partition.

### Step 7: Offset Tracking

Each consumer tracks the last read position (offset). This offset can be:

* Committed automatically (auto-commit)
* Manually committed (to allow for retries or exactly-once semantics)

---

Read : https://medium.com/@cobch7/kafka-architecture-43333849e0f4
