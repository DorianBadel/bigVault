---
chapter: 202
type: sub-chapter
---

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
