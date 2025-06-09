## ACID Properties

Acid Properties stands for _Atomicity Consistency Isolation Durability_

- Atomicity: This means that "all or nothing ". When a transaction happens is either the transaction happens fully or it's aborted no in betweens

- Consistency: it ensures that any changes to values in an instance are same across other values in the same instance

- isolation : isolation is needed when there are concurrent ==transactions== . This ensures that each transaction happens separately and independently

- Durability: Durability refers to the ability of the system to recover committed transaction updates if either the system or storage fails.

## Normalization:

Is a technique which is used to organise the data in the database. It is a systematic approach to remove the data reduced data redundancy
assuming we have this table with data lets using it to normalization:

| ID  | Name  | Address | Subject |
| --- | ----- | ------- | ------- |
| 201 | sam   | judy    | Maths   |
| 202 | jonte | kinoo   | bio     |
| 203 | kamau | wakama  | physic  |

- To remove data redundancy
- Ensuring data dependencies is proper

### Anomalies in normalization

- Updation Anamoly - To update address of a student who occurs twice or more than twice in a table, we will have to updateAddress column in all the rows , else data will become inconsistent.
- Insertion Anomaly - suppose for a new admission, we have a student but if a student has not opted for any subject yet then we have to insert NULL there, leading to insertion anomaly.
- Deletion anomaly - If id 401 has only one subject and temporarily he drops it,

### Normalization Forms:

#### 1. First Normal Form

As per first Normal form no two rows of data must contain repeating data
I.e whenever we search for a particular result the multiple columns cannot be used to fetch the same row

**example:** consider a table not in first normal form

| student | age | subject      |
| ------- | --- | ------------ |
| sam     | 15  | maths,phyisc |
| jonte   | 14  | Biology      |
| kamau   | 17  | Maths        |

Student table in 1NF will be

| student | age | subject |
| ------- | --- | ------- |
| sam     | 15  | maths   |
| sam     | 15  | phyisc  |
| jonte   | 14  | Biology |
| kamau   | 17  | Maths   |

Using the first normal form ,data redundancy increases , as there will be many columns with the same data in multiple rows but each row as whole will be unique

#### 2. Second Normal Form

As per second Normal form there must not be any pertial dependencies of any column on the primary key.

- Meet all the requirements of the first normal form
- Remove subsets of data that apply to multiple rows of table and place them in separate tables.
- Create relationships between these new tables and their predecessors through the use of foreign keys.
  **example:**
  New student table following the 2NF will be

| student | age |
| ------- | --- |
| sam     | 15  |
| jonte   | 14  |
| kamau   | 17  |

In student table the candidate key will be Student column , because all other columns i.e Age is dependent on it

| student | subject |
| ------- | ------- |
| sam     | maths   |
| sam     | phyisc  |
| jonte   | Biology |
| kamau   | Maths   |

#### 3. Third Normal Form

- A Relationship is in third Normal form if it is in second Normal form and it contains no transitive dependencies.
- Consider relation R containing attribute A,B and C
- if A-> B and C then A-> c
- transitive dependencies : three attributes with the above dependencies\
  **example:** Student_details table

| ID    | Name  | Subject | DOB   | Adress | Mobile No. | city  |
| ----- | ----- | ------- | ----- | ------ | ---------- | ----- |
| Item1 | Item2 | Item3   | Item4 | Item5  | Item6      | Item7 |

New student_details table

| ID    | Name  | Subject |
| ----- | ----- | ------- |
| Item1 | Item2 | Item3   |

Address Table:

| ID      | Address | DOB     | Mobile  | City    |
| ------- | ------- | ------- | ------- | ------- |
| Item1.1 | Item2.1 | Item3.1 | Item4.1 | Item5.1 |

##### Advantages of removing transitive

- amount of data duplicate is reduced
- data integrity achieved

#### 4. Boyce and Codd Normal Form(BCNF)

This is a higher version of third Normal form. This form deals with certain types of anomaly not handled in 3NF

- R must be in 3rd normal form
- and for each functional dependencies (x->y),x should be a super key

