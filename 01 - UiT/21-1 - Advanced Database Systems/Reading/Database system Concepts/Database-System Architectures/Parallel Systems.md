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
Components (processors, memory and disks) that communicate with each other through an interconnection network (set up in any of the following ways).

![[Pasted image 20250123210809.png]]

- **Bus** - All components can send data on and receive data from a single communication bus. Less used nowadays since it doesn't scale well. Used for connecting multiple CPUs and memory units.
- **Ring** - More scalable because multiple components can send messages at the same time. Might incur many hops to transmit data from node to node so not the best.
- **Mesh** - Scales well with increasing parallelism (more connections). Doesn't scale well with many nodes so not used today.
- **Hypercube** - better then a mesh. Less hops between components. Also no longer used.
- **Tree-like** - Used in server systems in data centres. Unlike a tree topology used in LANs in organizations (and explained on a server bellow) tree-like (fat-tree) topologies have multiple aggregation and core switches connecting things. Can also add some fault-tolerance. Such architecture can handle tens of thousands of machines in a cluster. The complex interconnection networks in a data centre are referred to as a *data centre fabric*.
> [!abstract] 
> An example of tree-topology in servers:
> Within a rack nodes (40 usually) are connected with **edge switches** (aka top-of-rack switches). They are then connected with **aggregation switches** connecting racks, if in a group one such switch connects a group of racks. All aggregation switches connect to a **core switch**.
> A common bottleneck is bandwidth on the aggregation switch (just not fast enough to supply communication between racks). Hence the switch to the tree-like topology.

Other than network topologies, network technology is also important.
**Ethernet** - Dominant. They can be used on copper for short distances and optical fiber for longer distances.
**Fiber channel** - Mainly used to implement storage area networks.
**Infiniband** - Designed for data centres, where latency is also important as well as bandwidth. It has latency of 0.7-0.5 microseconds while ethernet can be up to hundreds of microseconds.

- Communication latency can be significantly reduced by allowing direct access to the network interface (bypassing the OS).
- **RDMA (Remote direct memory access)** can also reduce latency. Technology that allows a process on one node to write to memory on another node.

### Parallel Database Architectures
Architectural models for parallel machines:
![[Pasted image 20250123215920.png]]
- **[[#Shared disk]]** - Set of nodes share a set of disks. Each node has its own processor and memory. Also known as **clusters**
- **[[#Shared Nothing]]** - Nodes don't share anything.
- **[[#Hierarchical]]** - A mix of both, most widely used today.
### Shared disk

### Shared Nothing

### Hierarchical