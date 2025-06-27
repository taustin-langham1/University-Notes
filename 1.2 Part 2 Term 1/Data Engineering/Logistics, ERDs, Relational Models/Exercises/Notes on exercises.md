
Derived Attribute - attribute that can be derived from other attributes. 
Shown in the same oval shape as other attributes, in the ERD, however has a second ring.



**MUST**
= two lines!!

**MAY**//such other things
= one line

`1:n` means 'one-to-many'; you have two tables, and each row of table A may be referenced by any number of rows in table B, but each row in table B can only reference one row in table A (or none at all).

`n:m` (or `n:n`) means 'many-to-many'; each row in table A can reference many rows in table B, and each row in table B can reference many rows in table A.

A `1:n` relationship is typically modelled using a simple foreign key - one column in table A references a similar column in table B, typically the primary key. Since the primary key uniquely identifies exactly one row, this row can be referenced by many rows in table A, but each row in table A can only reference one row in table B.

A `n:m` relationship cannot be done this way; a common solution is to use a link table that contains two foreign key columns, one for each table it links. For each reference between table A and table B, one row is inserted into the link table, containing the IDs of the corresponding rows.


**RELATIONAL SCHEMAS EXAMPLE**

**Entity 1:**
Teacher ( TeacherID:INT, TeacherName:TEXT, PRIMARY KEY: TeacherID)

**Entity 2:**
BUS ( BusID:INT, Time:DATE, PRIMARY KEY: BusID)

**The relationships relational schema:**
Uses (TeacherID:INT,BusID:INT, FOREIGN KEY TeacherID REFERENCES Teacher, FOREIGN KEY BusID REFERENCES BUS, PRIMARY KEY {TeahcerID,BusID})


**English Explanation:**
A Teacher MAY use MANY buses, A bus MAY be sued by MANY Teachers

