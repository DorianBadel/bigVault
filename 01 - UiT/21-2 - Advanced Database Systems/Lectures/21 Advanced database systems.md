---
tags:
  - lecture
  - advancedDatabases
lecture: 1
week: 2
---
**Relational model and relational database management system**
- Primary data model for commercial data-processing
- Designed for structured data

**Transaction server**
- Requests are specified in SQL and communicated to the server through a *remote procedure call (RPC)*.
- Transactional RPC allows many RPC calls to form a transaction
	- Transaction - A group of actions treated as one unit. [[Research: More on transactions]]

**Heterogeneous distributed databases**
- Built ground up. Adding features on existing DBs

#### DBMS characteristics
Distribution,
Heterogeneity - to what degree are the components of a system different,
Autonomy - what degree of local control of the local database we have.
- **Management autonomy** - are you willing to give away ownership (for example the community can manage the data)
---
The bottom left corner is centralized DBMS (no heterogeneity no autonomy no distribution)

#### Data Warehousing
The result of exploring heterogeneous systems built on top of existing databases.
Data in it is historical, almost never updated -  no consistency issues.

#### Information Retrieval systems
She blanked

---
Doesn't deal with transactional updates, updating data is just storing data again.

In a DB we expect to find everything that matches. In IR systems we receive the for e.g. 1000 best results.

#### NoSQL What is it?
Lots of systems fit this umbrella term.

---
It might mean Not Only SQL
All on this slide is a generalization, you cannot certainly say that all NoSQL DBs support large data volumes, but most do.

They relax the ACID principle.
#### What is wrong with RDBMS?
Nothing they were just build for a different thing.

#### Data models
Key-value NoSQL - e.g. Voldermort (I found it funny)

#### Homogeneous vs. Heterogeneous DDB
Heterogeneous DDB
- Require autonomy, this complicates things. E.g. cannot assume that a global query is allowed access to all the data

#### Top-Down Design
- Very cool for actually designing stuff
ES's - external schemas
LCS - local conceptual schema (what are the tables going to look like, where they will be stored)
LIS - 

#### Distributed Data Storage partitioning and replication
Relation - table
#### Horizontal partitioning
Perform a select for say a branch_name (if that is what we want to partition by) and place the result in a partition
#### Vertical partitioning
Creating two different partitions. (keeping `touple_id` for later joining)
#### Virtual Node Partitioning
A way of handling skew.
Moving around virtual nodes and storing to real nodes.
#### Interquery vs Intraquery parallelism
Interquery - Multiple queries running in parallel
Intraquery - Parallelizes one query
#### Slide before Data Transparency
It is almost impossible to judge cost of operations when adding heterogeneity due to the atomicity? property









