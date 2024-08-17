#creation_date:  2024-08-17 13:12
#modification_date: Saturday 17th August 2024 13:12:19
> [!quote] What happens is not as important as how you react to what happens.
> — Ellen Glasgow

> [!DESCRIPTION]
> #kafka , #kafka_producer
> A Kafka producer sends messages to a [[Topics|topic]], and messages are distributed to partitions according to a mechanism such as key hashing (more on it below).

![[Pasted image 20240817131236.png]]

## Message Keys

[Kafka producer](https://www.conduktor.io/kafka/kafka-producers/#Message-Keys-1)

Each event message contains an optional key and a value.

In case the key (`key=null`) is not specified by the producer, messages are distributed evenly across partitions in a topic. This means messages are sent in a round-robin fashion (partition _p0_ then _p1_ then _p2_, etc... then back to _p0_ and so on...).

**If a key is sent** (`key != null`)**, then all messages that share the same key will always be sent and stored in the same Kafka partition**. A key can be anything to identify a message - a string, numeric value, binary value, etc.

Kafka message keys are commonly used when there is a need for message ordering for all messages sharing the same field. For example, in the scenario of tracking trucks in a fleet, we want data from trucks to be in order at the individual truck level. In that case, we can choose the key to be `truck_id`. In the example shown below, the data from the truck with id _truck_id_123_ will always go to partition _p0._

![[Pasted image 20240817131712.png]]

![[Kafka message anatomy]]