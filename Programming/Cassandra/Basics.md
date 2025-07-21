---
created: 2024-02-25T11:29
updated: 2024-02-17T18:01
---
- Distributed architecture : Cassandra can run on multiple machines while appearing to users as a unified whole.
- Node : a host in cassandra cluster. Each node is reposible for storing a part of data (a range after hashing the partition key).
- Scale horizontally(scale-out) : databases can easily scale when an application is under high stress, just by adjust the number of nodes.
- Cluster : Cassandra usually have multiple nodes, multiple nodes can be organized logically into a cluster (or ring).
- Gossip Protocol : A node communicate with one another through a protocol called gossip (a process of computer peer-to-peer communication).
- Masterless architecture : any node in the database can provide the exact same functionality as any other node.
- Partitions: make the data itself automatically distributed,

  

- **Partition**:
- Rules for good partition:

+ Store together what you retrieve together.

+ Avoid big partitions.

+ Avoid unbound partitions.

+ Avoid hot partitions.

  

- **Notes**:
- Primary key must be unique : if data with the existed primary key is inserted, it will override the last write.
- Cassandra automatically replicate data around different data centers (it means that if one data was written to a node in this data center, it can automatically available at nodes in other data centers).