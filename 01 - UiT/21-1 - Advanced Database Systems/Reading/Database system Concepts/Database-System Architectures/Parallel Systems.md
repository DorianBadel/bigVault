---
chapter: 204
type: sub-chapter
---
Parallel systems of hundreds of thousands of nodes or more are housed in **data centres**.

### Motivation for Parallel Databases
Apps that query extremely large datasets (petabytes ~ 1000 terabytes) or those that have to process extremely large numbers of transactions a second (thousands).

**Decision-support queries** - Queries about users to plan activities and pricing (items in carts, phone calls placed...).

Open-source platforms for parallel data storage: Hadoop File System (HDFS), HBase.
For parallel query processing: Hadoop Map-Reduce and Hive...

### Measure of Performance for Parallel Systems
**Throughput** - the number of tasks that can be completed in a given time interval
**Response time** - the time it takes to complete a single task from submission.

##### Speedup 
speeding up a task by increasing the degree of parallelism.

- **Linear speedup** - $\frac{T_S}{T_L}$ s is small system, L is larger system. L has N times more resources. Speedup is linear if the result is N.
- **Sublinear speedup** - if the result is less than N.
	
##### Scaleup
Handling larger tasks in the same time by increasing the degree of parallelism.

- **Linear scaleup** - the larger task is done in the same time as the smaller one.
- **Sublinear scaleup** - it is done in more time.

**Batch scaleup** - Database size increases and a tasks runtime depends on the size of the database.

**Transaction scaleup** -  The rate at which transactions are submitted to the database increases, and the size of the database increases proportionally to the transaction rate.

##### Absolute performance
**Sequential computation** - *Amdahl's law* we can only speedup parts of the program that can be parallelized. *Gustafson's law* is the same thing but for scaleup. *Start-up costs* initiating a single process has a cost, so thousands might overshadow the speedup.

**Interference** - competing for commonly held resources. Both speedup and scaleup are affected.

**Skew** - Dividing a task into uneven pieces, which is often the case will result in worse results. As the slowest step will determine the service time for the entire task.

### Interconnection Networks



