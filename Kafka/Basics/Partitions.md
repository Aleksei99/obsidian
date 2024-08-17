#creation_date:  2024-08-17 13:02
#modification_date: Saturday 17th August 2024 13:02:16
> [!quote] As a water bead on a lotus leaf, as water on a red lily, does not adhere, so the sage does not adhere to the seen, the heard, or the sensed.
> — The Buddha

> [!DESCRIPTION]
> #kafka , #kafka_partition
> Topics are broken down into a number of partitions. A single topic may have more than one partition, it is common to see topics with 100 partitions.
> 
> The number of partitions of a topic is specified at the time of topic creation. Partitions are numbered starting from `0` to `N-1`, where `N` is the number of partitions. The figure below shows a topic with three partitions, with messages being appended to the end of each one.

![[Pasted image 20240817130613.png]]

> [!INFO]
> If a topic has more than one partition, Kafka guarantees the order of messages within a partition, but there is no ordering of messages across partitions.