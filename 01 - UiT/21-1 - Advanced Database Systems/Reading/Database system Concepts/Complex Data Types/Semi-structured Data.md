---
chapter: 81
start: 365
end: 375
type: sub-chapter
read: true
---
> Applications that require quickly changing attributes like modern web applications. For this we study JSON and XML data models that have been widely adopted for this task.

### Overview of Semi-structured Data Models
The relational data model has been extended in ways to support the storage and data exchange needs of modern apps.
#### Flexible Schema
**Wide column data representation** - Each tuple can have a different set of attributes. New attributes may be added as needed.

**Sparse column** - very large number of attributes but fixed. Leaving many with null.

#### Multivalued Data Types
Sets, arrays, maps
*non first-normal-form* or *NFNF* data model.

**Array database** - a db with specialized support for arrays.

#### Nested Data Type
Attributes can be structured.

**JavaScript Object Notation (JSON)**
**Extensible Markup Language (XML)**

##### *Resource Description Format (RDF)*
- Representation of large knowledge base
Only supports *binary* relationships unlike E-R models (no n-ary relationsips).

Set of **triples**
`subject | predicate | object`
`10101 instance-of instructor`
`sec1 year "2017"`

All values are shown in quotes.

###### Graph Representation of RDF
![[Pasted image 20250108180618.png]]

###### SPARQL
Used to query RDF
```sql
?cid title "Intro. to Computer Science"
?sid course ?cid
```
cid = CS-101
sid = sec1

#### Representing N-ary Relationships
The idea of **reification** - treating a relationship as an entity.

Linking artificial entities to both related entities like "2008" through *president_from* to both *person* and *country*.

Another approach is adding *context* to triples - making **quads**.

Making domain specific knowledge graphs open source: [linked open data](https://lod-cloud.net/)
