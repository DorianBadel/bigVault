---
chapter: 207
type: sub-chapter
---
![[Pasted image 20250202190017.png]]

IaaS - enterprise rents computing facilities.
Ability to expand or contract capacity at short notice is called **elasticity**. Security questions prevent high risk enterprises from using it (like banks).

PaaS - cloud-based data storage, database-as-a-service

SaaS - just paying for an app. Application software acting as the backend, web or mobile app interfaces are the front-end

VMs: Lover cost of supplying power and maintaining systems, by allowing multiple users to share the cost. Allow easy moving of a service to a new machine - extra useful in events of hardware failure or upgrades.
Have large overheads since an entire OS is there.
Two main problems when running multiple apps on one VM:
- Conflicts on network ports.
- Requiring different versions of shared libraries.

**Containers** solve those problems. Also less overhead so more of em fit on one machine.

![[Pasted image 20250202192619.png]]

**Microservices architecture** - apps today are built as collections of **services**.
Each service runs a separate process offering a network API. Containers fit this very well.

**Docker** - container platform.
**Kubernetes** - containers and a microservice platform.
	- **Pods** - Allows multiple containers to share storage and network (IP address).
	- Load balancing for collections of containers that run copies of the same app.

### Benefits and Limitations of Cloud Services
Users data is held by another organization - risks in terms of security and legal liability.
A security breach may leak client data making the client face legal challenges from its customers.

