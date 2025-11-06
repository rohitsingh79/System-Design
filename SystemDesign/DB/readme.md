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


NOSQL
- flexible , can scale in a distributed system (social media app , logging ,messaging application )
- provides BASE modal
1. basic availability: always available due to distributed nature
2. soft state: the system may change the state over time due to eventual consistency
3. eventual consistency: all replicas converge to the same state but not instantly

- it is distributed in nature and hence having consistency in which each node is update to date is complex to manage