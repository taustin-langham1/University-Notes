


### understanding and reliably reading ERD's


## Entities
##### Represented by a Rectangle

- object tracked within the database

## Attributes
##### Represented by an OVAL

- attributes of Entity Objects

- PRIMARY KEYS are represented with an underline 

- multivalued attributes are given using double lines

- *composite attributes (attributes of attributes) are represented as more ovals from an oval, and they are imaginary, so not represented within the table*

## Relationships
##### Represented by a Diamond



## Cardinalities

![[Pasted image 20250421223929.png]]

*Mapping cardinalities*

## 1-to-1

only one relationship between individual objects of entities (say entity is cars,  a specific Toyota corolla would have a 1 to 1 relationship with its first owner)
## 1-to-Many

one instance of an entity has a relationship with many other instances of another entity 
##  Many-to-1

vica versa
## Many-to-Many

many from both instances of the entities within the relationship


##  **Relational Model**

Terminologies

**Relational model as a collection of tables**

**table is also called a relation**

so a relation name would also be the table name
**Each row is a tuple**
**each column is an attribute or field**

**Domain:**
set of atomic values allowed for an attribute


**Relational schema?**

made up of relation name: R(A1, A2  ..., An)

degree would be AN (number of attributes in a schema)

**Cardinality?**
total number of tuples present in a relation


