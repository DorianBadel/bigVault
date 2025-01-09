---
chapter: 200
start: 961
end: 998
type: chapter
read:
---
*[[#Centralized Database Systems]]* - Built to run on a single physical machine. Can support more than tens of thousands of users and a database sizes ranging from megabytes to hundreds of gigabytes.

*Parallel database systems* - developed, in 1980s, to execute tasks in parallel on a large number of machines to support high-end enterprise applications.

*[[Parallel and Distributed Storage|Parallel data storage systems]]* - designed to store and retrieve data based on keys. They provide very limited support for transactions and they lack support for declarative querying. Can be ran in parallel on very large numbers of machines.

*Distributed database system* - developed to satisfy the need of executing [[Distributed Query Processing|queries]] and update transactions across multiple databases.

## Centralized Database Systems

### Single-user systems
> Used by a single person, usually a single processor (usually with multiple cores), and one or two disks (meaning any SSD or HDD).

May support simple concurrency control schemes, crash recovery may be very basic (e.g. making a copy of data before updating it) or absent. 

**Embedded databases** - A system that provides an API for data access instead of SQL.

### Multiuser systems
> Multiple disks, a large amount of memory, multiple processors. They serve a large number of users who are connected to the system remotely and they are called **server systems**.

Support full transactional features.
Designed as **servers** that service requests received from apps. Requests can be in the form of SQL queries, or they can be requests for retrieving, storing, or updating data specified using an API.

### Parallelism
**Coarse-grained parallelism** - Parallelism with a small number of cores with shared memory.
- Usually each core handles its own request. In newer times such systems also parallelise individual queries.

**Fine-grained parallelism** - Large number of processors. Databases running on such machines attempt to parallelize single tasks (queries, for example) submitted by users.

## Server System Architectures
Broadly categorized as transaction and data servers.
### Transaction-server (query-server)
Provide an interface for clients to send requests to perform an action, in response they execute the action and send back the result. Requests may be specified through the use of SQL or specialized APIs

A typical system today consists of multiple processes accessing data in shared memory.
![[Pasted image 20250109235022.png]]
Processes that form part of the DB system include:
- **Server processes** - 
- **Lock manager** - 
- **Database writer** -
- **Log writer** -
- **Checkpoint** -
- **Process monitor** -

Log buffer - stores log records waiting to be output to the log on stable storage
Cached query plans - reused if the same query is submitted again
### Data-server systems
Allow clients to interact by making requests to read or update data.

--- Left off at 965 writing Server processes