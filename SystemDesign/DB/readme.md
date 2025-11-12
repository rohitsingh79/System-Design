SQL
- more strict schema and provide acid transactional properties (banking , ecommerce order management)
- cap theorem (consistent and availiable)
- initially it was designed to be a single database (large) that can be scaled vertically
- provides ACID properties
1. atomicity - all operations are done or none 
2. consistent - after operation or transaction , the database is moved from one  state to another state
3. isolation - each transaction is treated as individual in isolation
4. durablity - once committed DB data is permanently stored , even if the system crashes

Transaction
- a group of database operations (INSERT , UPDATE , DELETE) etc are treated as a transaction

Atmoicity
- uses write ahead log (WAL) which is used in to recover or undo whenever it uses crash

Consistency
- uses key constraints (FK , UK , PK ,TYPE constraints) and regular triggers to check for consistency

isolation
- uses MVCC (multi version control) system and isolation levels

Durability
- WAL is witten to the disk when the commit happens

normalization: 
- splitting data into multiple tables to avoid duplication and maintain consistency
- achieved using 1NF , 2NF , 3NF normalisation

denormalisation:
- having all the rows in the same table and in the duplicated form for faster reads , as there is no joins that is required


Normalisation:
-1NF: the individual  column data should be atomic
-2NF: the non key column should depend on the primary key of the table only
-3NF: there should be no transitive dependency in the table


Distributed nature
- is given by tools such as citus , having master-slave application (having multiple read copies) , Vitess tool used by youtube ,
- google spanner is a custom distributed db
- to maintain consistency , distributed system uses consensus protocol (write goes to the leader ,and then to replicas if majority acknowledge the the write is commited)


Isolation Levels:
1. read uncommited (not used in prod)
2. read commited : read the row value only when the transaction is commited
3. repeatable read : it always see the same value during its entire lifetime (prevent dirty reads)
4. serializable: synchronous in nature , transactions are executed one after the other (performance heavy)

MVCC (multi version concurrency control mechanism):
- postgress sql supports concurrent read and writes using MVCC
- it works by maintaining multiple versions of the same row during a read or write opertion
- it maintains a snapshot of the version before the transaction was started (the snapshot contain row version with xmin and xmax)
- a transaction t1 sees a row version only when
    a) the xmin value is commited and is less
    b) the xmax value is null or from a commited transaction
- when a transaction  tries to update a row it creates a new row version with xmin (ex: xmin  = 23) and xmax(ex:NULL) value and updated the xmax of the older row version to current tid
- the previous transaction if only has read operation than nothing happens it will just return the old stale data
- but if write operation happens then it depends on the isolation levels what needs to be done
    a) read commited: it will fetch the updated row version and then update
    b) in non-repeatable read or serializable: it will give concurrency error stating the row was changed 


Indexing
- faster for reads (select , group by , joins) and slow for writes
- mongo db does default indexing on the _id by default  , custom indexing using create_index()

Joins
- inner join
- left outer join
- right outer join
- self join
- full outer join

Keys
- primary: uniquely identify each row
- unique: used for unique values (ex: email) and can be null
- foreign key : used for referential integrity  to link the the primary key of one with the secondary key in other table


-----------------------------------------------------------------------------------------------------------------------------------------------

NOSQL
- flexible , can scale in a distributed system (social media app , logging ,messaging application )
- provides BASE modal
1. basic availability: always available due to distributed nature
2. soft state: the system may change the state over time due to eventual consistency
3. eventual consistency: all replicas converge to the same state but not instantly

- it is distributed in nature and hence having consistency in which each node is update to date is complex to manage

- normalisation is achieved  using referencing
- de normalisation is achieved  using embeding 
- joins are done using embedding(de normalisation) 



-----------------------------------------------------------------------------------------------------------------------------------------------
ELASTIC SEARCH
- for indexing it uses inverted index ('rohit' --> [#doc1 , #doc2 , #doc3]) 





