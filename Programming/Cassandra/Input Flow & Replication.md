---
created: 2024-02-25T11:29
updated: 2024-02-17T17:55
---
- Partition key : responsible for distributing data among nodes and is important for determining data locality.
- Coordinator : simply the node that gets the request at that particular moment. Any node can act as the coordinator.
- Data range: each node reponsible for a primary range of tokens. If RF > 1, then each node need to responsible for RF range of tokens.
- Replication mechanism : to ensuring reliability and fault tolerance, one piece of data can be replicated to multiple nodes (replicated times called RF).

  

- **Data-In** **Flow:**
- Data is inserted into the cluster.
- Apply a hash function to the partition key.
- Output is a token used to determine what node will get the data.
- Data comes in, database's coordinator take on the job of assigning to a given partition in some node (this node called replica node).

  

- **Self healing** **of replication mechanism**:
- If a node goes wrong, a hard-drive fails, AWS resets an instance and a request comes in for data, the other replica nodes are still available to fulfill the request.
- Coordinator store a "hint" for that data and then the downed replica comes back up, it will find out what it missed and catch up to speed with the other replicas (no manual action is required).