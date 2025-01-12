---
chapter: 203
type: sub-chapter
---

Broadly categorized as transaction and data servers.
### Transaction-server (query-server)
Provide an interface for clients to send requests to perform an action, in response they execute the action and send back the result. Requests may be specified through the use of SQL or specialized APIs

A typical system today consists of multiple processes accessing data in shared memory.
![[Pasted image 20250109235022.png]]
Processes that form part of the DB system include:
- **Server processes** - Receive, execute and respond to user queries. 
- **Lock manager** - implements: lock grant, lock release, deadlock detection.
- **Database writer** - output modified buffer blocks back to disk on a continuous basis.
- **Log writer** - outputs log records from the log record buffer to stable storage. Allows for a "log force" - outputs log content to stable storage upon request.
- **Checkpoint** - Performs periodic checkpoints.
- **Process monitor** - Monitors other processes, takes recovery actions for failed processes, like aborting any transaction being executed and restarting the process.

Log buffer - stores log records waiting to be output to the log on stable storage
Cached query plans - reused if the same query is submitted again

Since a **mutual exclusion** mechanism must be present a common alternative to *semaphores* are **atomic instructions**. These are *test-and-set* or *compare-and-swap*, nowadays one of these is always supported by a multiprocessor system.

**Atomic instructions** support exclusive locks but do not support shared locks.
### Data-server and Data Storage Systems
Originally designed to support data access from object oriented databases.

Computer aided design (CAD) systems is an example application that uses OODBs. In such an app it is important for the computation to be done on the client size as to not overload the server.

> [!info]
> **Data item** - refers to tuples, objects, files and documents
> *data server* and *data storage system* are terms used interchangeably.

Data servers expose an API for CRU operations (no mention of deleting but I assume it is a form of U).

### Caching at Clients
To reduce the effect of network latency the following optimization strategies are applied (both on clients and on parallel DB systems):

**Prefetching** - when responding to a request you may send extra related data that hasn't been requested yet.

**Data Caching** - results of a transaction may be cached for use with further transactions. *Cache coherency* is important here; transactions must make sure that the data is up to date (so a validity check and obtaining a lock is still required). 

**Lock caching** - when clients rarely request data that is also requested by other clients a lock can also be cached. Keeping track of cached locks is important for performing *call back*s when the same lock is requested the second time.

**Adaptive lock granularity** - used to avoid multiple requests for locks. E.g. acquiring the lock of a page (coarser granularity) can avoid requesting multiple data-item locks (finer granularity).
	Lock de-escalation is a way to adaptively decrease lock granularity upon higher contention.