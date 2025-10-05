
**[Video Reference](https://www.youtube.com/watch?v=ABwD8IYByfk&ab_channel=edureka%21)**

## **What is normalization?**

eliminate data redundancy, improves integrity
every table has to be in the normal form
less costly, less trouble, more logical sense, more purpose, more application

data anomalies:
difficult to handle and update

INSERTION ANOMOLY: These anomalies occur when it is not possible to insert data into a database because the required fields are missing or because the data is incomplete

UPDATION ANOMOLY: These anomalies occur when modifying data in a database and can result in inconsistencies or errors.

DELETION ANOMOLY: these anomalies occur when deleting a record from a database and can result in the unintentional loss of data.

## 1 nf

SIMPLE:  A SINGLE CELL CANNOT HOLD MULTUPLE VALUES

## 2 nf

in 1nf, CANNOT HAVE PARTIAL DEPENDENCY 

 need FULL DEPENDENCY for 2nf, i.e., if there is partial dependency in a composite key, split the table for it to be in 2nf

## 3 nf

has to be in 2nf

THERE SHOULD BE NO TRANSITIVE DEPENDENCY FOR NON-PRIME ATTRIBUTES

I.E., all non-prime attributes should depend only on the prime attribute

## B-C nf // 3.5 nf

3 nf satisfied

everything has to be functionally dependent on the super key

why is this table in 3NF and not in BC NF?

![[Pasted image 20250503194027.png]]






