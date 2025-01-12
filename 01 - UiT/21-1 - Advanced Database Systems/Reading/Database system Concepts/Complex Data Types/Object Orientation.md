---
chapter: 82
start: 376
end: 382
type: sub-chapter
read: true
---
Many apps are written in object-oriented languages, but they need to use databases. The databases support relational models, this means we need to express database access using a language (SQL) that is different from the programming language.

We want to have constructs or extensions that permit direct access to data in the database within our language already.

Approaches:
1. Build an [[#Object-relational database system]] - OO features to a relational DB
2. Automatically convert data between them. This is specified using a [[#Object-relational mapping]]
3. Build an [[#Object-oriented database system]] - a DB that natively supports OO type system.

## Object-relational database system
### User-Defined Types
Creating structured user-defined types, references to the types and tables containing tuples of such types allows us to do something like this:
```SQL
create type Person 
	(ID varchar(20) primary key,
	name varchar(20),
	address varchar(20))
	ref from(ID);
create table people of Person;

INSERT INTO people (ID, name, address) VALUES
('12345', 'Srinivasan', '23 Coyote Run');

create type interest as table ( 
	topic varchar(20),
	degree of interest int 
); 
create table users ( 
	ID varchar(20),
	name varchar(20),
	interests interest
);
```
#### Type Inheritance
If we want to store additional information about *people* like *teachers* and *students* we can extend the types using inheritance:
```SQL
CREATE TYPE Student UNDER Person
	(degree varchar(20));
CREATE TYPE Teacher UNDER Person
	(salary integer);
```
Both attributes and Methods are inherited by subtypes (teacher,student). A subtype can redefine the effect of a method.
#### Table Inheritance
Same as types but for tables, SQL requires defining types PGSQL doesn't.
If we create entries into the *Student* table for example. The entries would be present in *person* but only the tuples that are part of *person* (in this case no *degree* attribute).
#### Reference Types in SQL
```SQL
CREATE TYPE Department (
	dept_name varchar(20),
	head ref(Person) SCOPE people
);
CREATE TABLE departments OF Department
```
The `SCOPE` clause completes the definition of the foreign key from `departments.head` to the `people` relation.

Most DB systems don't allow subqueries in a `INSERT INTO departments VALUE` statement, the following two queries can be used to carry out the task:
```SQL
INSERT INTO departments
	VALUES ('CS', null);
UPDATE departments
	SET head = (SELECT REF(p)
		FROM people AS p
		WHERE ID = '12345')
	WHERE dept_name = 'CS';
```
This is useful when we want to reference a tuple not a specific value

**Path expression** - `head->name` used in SQL.
*head* is a reference to a tuple in the *people* table so this is referencing the attribute *name*from the *people* table.

References help us avoid explicit joins.

```SQL
SELECT DEREF(head).name
FROM departments;
```
We can return the tuple pointed to by a reference with the `DEREF` operation.
## Object-relational mapping
> Also known as **ORM**

Allows a programmer to define a mapping between tuples in DB relations and objects in a PL (Programming language).

The goal is to ease the job of programmers by providing an object model while retaining the benefits of using a robust relational database underneath.
Additionally it can provide significant performance benefits if operation on an object cached in memory.

E.g. *Django (Python), Hibernate (Java)*