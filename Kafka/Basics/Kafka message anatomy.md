#creation_date:  2024-08-17 13:19
#modification_date: Saturday 17th August 2024 13:19:53
> [!quote] Your mind will answer most questions if you learn to relax and wait for the answer.
> — William Burroughs

> Kafka messages are created by the producer. A Kafka message consists of the following elements:

![[Pasted image 20240817132201.png]]

> [!INFO]
> - **Key**. Key is optional in the Kafka message and it can be null. A key may be a string, number, or any object and then the key is serialized into binary format.
> - **Value**. The value represents the content of the message and can also be null. The value format is arbitrary and is then also serialized into binary format.
> - **Compression Type**. Kafka messages may be compressed. The compression type can be specified as part of the message. Options are `none`, `gzip`, `lz4`, `snappy`, and `zstd`
> - **Headers**. There can be a list of optional Kafka message headers in the form of key-value pairs. It is common to add headers to specify metadata about the message, especially for tracing.
> - **Partition + Offset**. Once a message is sent into a Kafka topic, it receives a partition number and an offset id. The combination of **topic+partition+offset** uniquely identifies the message
> - **Timestamp**. A timestamp is added either by the user or the system in the message.


