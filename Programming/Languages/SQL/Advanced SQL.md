___
## **Recall** $\dots$
___
- Natural Joins take the values of two tables and concatenate them based on matching columns
- Outer Joins take the values of two tables and concatenate them based on matching columns leaving nulls in the tables where opposite to the specification of the join . 
	- Left outer join $\rightarrow$ Null values from right table
	- Right outer join $\rightarrow$ Null values from left table
## Types of Joins
___
- *Inner Join* :
- *Inner Join* :
- *Inner Join* :
- *Inner Join* :

## Views 
___
- Abstract interfaces for viewing without seeing the contents of the tables . 
 ```sql
 create view v as <query expression> 
```

 ```sql
create view faculty as 
select dept_name
from intsructor 
```

- Views are also treated as relations themselves so query operations can occur on them as well . 
- Views are recursive and once they are invoked they are ran
- Susceptible to inserting wrong information .

## Materialized Views 
___
As opposed to a simple relation which is the result of the view , A Materialized View creates a physical table which exists within the database . 


## Transactions 
___
- Unit of work 
- Atomic 
	- Either happens or it doesnt
- Is a series of checks and updates 
	- $Step_1$ : Selection to confirm whether $x$ exists
	- $Step_2$ :  Update table where $x$ exists 
	- $Step_3$ : Update table where your desire to move $x$  . 
	- $\sum{Steps_i}$ is referred to as the *Transaction*
- This entire process is done in a single stroke referred to as a transaction . Therefore if a crash occurs within the middle of the transaction it rolls back completely .  Said to terminate at **Commit work** or **Rollback work** . 
```sql
go ...
... begin
	-> 	SELECT balance --Selection
		FROM A
		WHERE user_id = 'xyz'
	-> balance in A >= Amount -- Verification 
	-> EXIT
	-> UPDATE balance FROM A , set balance = balance - amount  --Update (1)
	-> UPDATE balance FROM B , set balance = balance + amount  --Update (2)
end(commit)	
```
- Isolation of concurrent transactions $\rightarrow$ Compiler optimization to make sure errors aren't thrown 

## Integrity Constraints 
___
- Assertions  which make sure your insertions make sense . 
	- **NOT NULL**  : Cannot be **NULL**
	- **UNIQUE** : Occurrence within the attribute can only occur once
	- **CHECK** : assertions based on predicates . 
	- **Referential Integrity** : Foreign Key , Checks whether the foreign key exists within the table it references  *(CID Foreign key references Course )*  . 
	
## Cascading Actions in Referential Integrity 
___
- When a child references a parent attribute which is foreign to the table , Applying the keywords **ON DELETE CASCADE** and **ON UPDATE CASCADE** when the child instance of the relation is updated , it is updated everywhere else
## Complex Check Clauses . 

*Syntax* 
```sql
check (time_slot_id in (select time_slot_id from time_slot))
```



## Index creation
___
Simply put , indices are generated to decrease query times . queries will only look through columns which the index occurs . 

## Authorization 
allows different levels for users to interact with the database
- Read - read only access to the file .
- Insert - allows insertion of new data . 
- Delete- allows deletion of data . 
- Index - allows creation and deletion of indices. 
- Resources - allows creation of relations . 
- Alteration - allows creation and deletion of indices. 
- Drop - allows for deletion of relations. 
Syntax ...
```sql
grant priviledge list
on relation to user list .
```
Granting privilege's on a view does not imply granting privilege's
only people with x privilege can grant x privilege. 

Revoke
```sql
revoke <privilege list>
```

Roles ... 
Essentially allows you to create values and authorizations as a variable and grant that authorization to individuals . for Example , say I wanted to create a class of individuals with the same authorizations , as opposed to listing out all the authorizations out one by one and granting them as such , what I  can do is simply create a list of authorizations and grant it to said individual . 
```sql
create role dean
grant dean to user_1
grant dean to user_2
```

Cascade can be applied to roles to remove and add all the values aswell as the values they granted others all at once .


**Ordered Indices .**
___
Essentially a means of adding a glossary to SQL files . These index files take up space of their own . 

Primary Indexes : 

Secondary Indexes : Be careful when working with ranges .

Index Evaluation :


Sparse Index files : contains index records for only some search key values . Advantages of sparse index files is that they . require less space .

Dense Index Files : 

Updating indices is usually causes some overhead .

Index deletion 

 

Sequential Indexing :


## B+ Tree
---
A tree which allows us to search through values .
- All paths from root to leaf are the same length however 
- Internal nodes have *n\2* or *n* children nodes . Where n denotes the number of pointers 
- Root nodes have at least 2 nodes . Note this is not the same as the amount of keys .
- Search keys occur in a manner where values which are greater than the search occur to the right and values less than the search key occur to the right of the node . 
## Insertions on Binary search trees .
1) Find the leaf node in which the search key value would occur
2) If the search key is already present in the leaf node 
	1) add record to the file
	2) if necessary add pointer to the bucket.
3) If the search key value is not present then 
	1) add the record to the main file
	2) if there is room in the leaf node, insert(key, value pair)
	3) Otherwise , split the node (along with the new (key value , pointer)) entry 

## Deletion on Binary search trees .
- When we have more than half full values after deletion is relatively simple , we just remove the value and move on , however when there is less than half full then borrow from neighbor , if the neighbor would also be left half full then don't borrow  .
- In the case that we do move that value , we borrow from right , and move the leftmost value upwards . 
- When we have more than half full values after deletion is relatively 


Why do we use B+ Trees
















[[Advanced SQL]] [[Relational Database Design]]
