# Read: 14a - DB Normalization

## Essential: Database Normalization Explained in Simple English

> Database normalization is a process used to organize a database into tables and columns

> By limiting a table to one purpose you reduce the number of duplicate data contained within your database

>  database table is where all the data in a database is stored
> A database consists of one or more tables.  Each table is made up of rows and columns
> Each row in a relational is uniquely  identified by a primary key.  This can be by one or more sets of column values.  In most scenarios it is a single column, such as employeeID.
> Every relational table has one primary key.  Its purpose is to uniquely identify each row in the database.  No two rows can have the same primary key value
> Columns are defined to hold a specific type of data, such as dates, numeric, or textual data
> Columns names can’t be duplicated in a table
> In summary, you can think of the columns as giving the table its personality and the rows its substance.


>  three normal forms most databases adhere to using
1.  minimize duplicate data
2.  minimize or avoid data modification issues
3.  simplify queries

> Having the table serve many purposes introduces many of the challenges; namely, data duplication, data update issues, and increased effort to query data

> Duplicated information presents two problems:
1. It increases storage and decrease performance.
2. It becomes more difficult to maintain data changes.

> These situations are modification anomalies

>  three modification anomalies that can occur
1. Update Anomaly:  If we don’t update all rows, then inconsistencies appear.
2. Search and Sort Issues: try to make it easier to search and sort your data
3. Deletion Anomaly: Deletion of a row causes removal of more than one set of facts.

> Definition of Database Normalization
> here are three common forms of database normalization: 1st, 2nd, and 3rd normal form. They are also abbreviated as 1NF, 2NF, and 3NF respectively.

> summarize the various forms:

1. First Normal Form – The information is stored in a relational table with each column containing atomic values. There are no repeating groups of columns.
2. Second Normal Form – The table is in first normal form and all the columns depend on the table’s primary key.
3. Third Normal Form – the table is in second normal form and all of its columns are not transitively dependent on the primary key


# 
