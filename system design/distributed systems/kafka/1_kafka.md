## What is Kafka & Why Use It?

###  Kafka in one line:
- Kafka is a **distributed event streaming platform** used to build **real-time data pipelines and applications**.
- Originally developed in LinkedIn during 2011, Apache Kafka is one of the most popular open-source Apache projects out there.
  
###  What problems does Kafka solve?

*Let’s say*:
* You have a **system generating data** (logs, orders, messages).
* You want that data to go to **multiple systems** (database, alert system, dashboard).

*Without Kafka*:
* You manually write separate integrations for each system.
* It’s tightly coupled, error-prone, and non-scalable.

**With Kafka*:**
* Everyone just "plugs in" to Kafka. It's like a central hub.
* **Producers** send data → **Kafka topics** → **Consumers** read data.

Think of it like a **WhatsApp group**:
* People send messages (producers)
* Everyone who joins the group sees the messages (consumers)
* Messages are retained even if someone reads them late (offsets)


### Use Cases of Kafka:

* Real-time analytics dashboards
* Order processing systems (e.g. Flipkart, Swiggy)
* Logging systems (e.g. ELK + Kafka)
* IoT devices streaming telemetry data
* Microservices communicating via events


##  Key Kafka Terminology You MUST Know

| Term               | Meaning                                           |
| ------------------ | ------------------------------------------------- |
| **Topic**          | Named channel to send/read messages               |
| **Producer**       | App that **sends** messages                       |
| **Consumer**       | App that **reads** messages                       |
| **Broker**         | Kafka server that stores messages                 |
| **Partition**      | Subdivision of a topic (enables parallelism)      |
| **Offset**         | Position of a message in a partition              |
| **Consumer Group** | Multiple consumers working together on same topic |

