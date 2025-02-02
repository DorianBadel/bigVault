---
type: sub-chapter
chapter: 206
---
A transaction running across two nodes can commit in one node and abort in another creating inconsistent state. 

To avoid this the most common protocol used is the *two-phase commit protocol (2PC)*.
The basics: All nodes use a partially committed or *ready* state when done with a transaction. A coordinator node checks if everyone did the same thing and sends out a decision (commit or abort). Every node then listens to the coordinator and commits or aborts.

Subchapters of the topic include:
Concurrency control
Persistent messaging for communication
Workflow management systems

