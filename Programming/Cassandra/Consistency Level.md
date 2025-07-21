---
created: 2024-02-25T11:29
updated: 2024-02-17T18:10
---
- Cassandra is by default an AP data-base. But we can indeed configure the consistency on a per-query basis.
- Consistency level : the minimum number of Cassandra nodes that must acknowledge a read or write operation to the coordinator befor the operation is considered successful.
- Quorum : majority.
  
- **CL Rules**: select consistency level based on RF.
![Exported image](Exported%20image%2020240225112915-0.png)- Majority of replicas must acknoledge back to the coordinator in order for the query to be considered a success.