
##  ACID  Properties 
Acid Properties  stands for *Atomicity Consistency  Isolation Durability* 
- Atomicity: This means that "all or nothing ".  When a transaction  happenes   is either  the transaction  happens  fully  or it's  aborted no in betweens
- Consistency:  it ensures that any changes to  values in an instance  are same  across other values  in the same instance 
- isolation : isolation  is needed  when  there  are concurrent  ==transactions==  . This ensures  that each  transaction  happens  separately and independently 
- Durability: Durability refers  to the ability  of the system  to recover committed  transaction updates  if either  the system or storage  fails. 
## Normalisation: 
Is a technique  which is used to organise  the data in the database.  It is a systematic  approach  to remove the data reduced  data redundancy 
- To remove  data redundancy 
- Ensuring data dependencies  is proper 
### Anomalies  in normalization
- Updation Anamoly - To update address of a student who occurs twice or more than twice in a table, we will have to updateAddress column in all the rows , else data will become inconsis3rop6 gg tent.
- Insertion Anomaly - suppose for a new admission, we have a student but if a student has not opted for any subject yet then we have to insertNULL there, leading to insertion anomaly.
- Deletion  anomaly - If id 401 has only one subject and temporarily he drops it, 
### Normamization Form:
#### 1.  Frist Normal Form
As per first Normal  form no two rows of data must contain repeating  data
I.e whenever we search for a particular result the multiple columns  cannot  be used to fetch the  same row

Using the first  normal  form ,data redundancy  increases , as there will be many columns with the same data in multiple  rows  but each row as whole will be unique 
#### 2. Second Normal Form
As per second Normal form there must not be any pertial dependencies  of any column  on the primary  key.
- Meet all the requirements  of the first normal form
- Remove  subsets  of  data that apply to multiple rows of table and place them in separate  tables.
- Create relationships between  these new tables and their predecessors through the use of foreign  keys.
- 

#### 3. Third Normal Form
- A Relationship  is in third  Normal  form if it is in second   Normal  form and it contains no transitive  dependencies. 
- Considere relation R containing attribute A,B and C
- if A-> B and C then A-> c
- transitive dependencies  : three attributes  with the above  dependencies 
##### Advantages  of removing transitive 
- amount  of data duplicate  is reduced 
- data integrity  achieved 
#### 4. BCNF
This is a higher version  of third  Normal  form. This form deals with  certain  types of anomaly  not handled  in 3NF 
- R must be in 3rd normal form
- and for each functional dependencies (x->y),x should be a super key
 