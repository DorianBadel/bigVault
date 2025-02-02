---
chapter: 205
type: sub-chapter
---
Distributed databases vs shared-nothing parallel databases:
- Here the databases have geographically separated sites. Network connections have lower bandwidth, higher latency, greater probability of failures.
- We need high availability so failure must be handled. While in shared-nothing systems an earthquake or a fire might take out an entire datacentre in a distributed database it would need to continue working.
- Can be separately administered.
- Nodes tend to vary more in size and function.
- We differentiate between local and global transactions.

In a **Homogeneous DDBS** nodes share a common global schema.
- The same distributed database-management software, and the nodes actively cooperate in processing transactions and queries.

**Network partition** - situation where two alive sites cannot communicate due to network-link failures. It effects availability of a system.