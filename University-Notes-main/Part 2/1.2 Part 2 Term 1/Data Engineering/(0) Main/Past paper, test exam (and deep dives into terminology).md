
i. Functional Dependency

where one set of attributes X uniquely determines another


ii. Partial Dependency

a special case of functional dependencies, where a non-key attribute depends on only a part of a composite primary key (not the whole key)

iii. Transitive Dependency

where a non-key attribute depends on another non-key attribute, rather than a direct functional dependency  

##### INTEGRITY CONSTRAINTS (ICs)





#### Terminology used:

1. **Attributes** - columns in the table of the entity being observed

2. **Key Attributes** - 3 types:
	1. Primary Key: The main **Unique** identifier
	2. Candidate Key: **Potential** and actual primary keys
	3. Foreign Key: An attribute that references a primary key in another table

3. **Non-key Attributes**
	1. Attributes that aren't apart of the Candidate keys

4. **Composite Primary Key**
	1. where the primary key isn't made of a single attribute, but multiple
	
5. **Determinant**
	1. attributes, on the left side of a functional dependency (X in X->Y)

6. **Dependent**
	1. attributes, on the right side of a functional dependency (Y in X->Y)

7. **Super Key**
	1. any attributes that can uniquely identify a record

8. **Trivial vs Non-trivial Dependencies**
	1. Trivial: When the dependent is a subset of the determinant XY -> Y
	2. Non-Trivial: when the dependent has attributes not in the determinant X -> Y


#### What's the difference between a super key and a primary/candidate key?




**Questions:**

![[Pasted image 20250508124644.png]]



T1:     R(X), W(X), R(Y), W(Y)
 
T2:     R(X), W(X)

