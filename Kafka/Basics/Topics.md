#creation_date:  2024-08-17 12:53
#modification_date: Saturday 17th August 2024 12:53:22
> [!quote] To have faith is to trust yourself to the water. When you swim you don't grab hold of the water, because if you do you will sink and drown. Instead you relax, and float.
> — Alan Watts

> [!DESCRIPTION]
> #kafka, #kafka_topic
> A topic is identified by its name. For example, we may have a topic called **logs** that may contain log messages from our application, and another topic called **purchases** that may contain purchase data from our application as it happens.

![[Pasted image 20240817125342.png|200]]

> [!INFO]
> - Kafka topics can contain any kind of message in any format, and the sequence of all these messages is called a data stream.
> - Data in Kafka topics is deleted after one week by default (also called the default message retention period), and this value is configurable.
> - Kafka topics are **immutable**: once data is written to a partition, it cannot be changed

![[Partitions]]