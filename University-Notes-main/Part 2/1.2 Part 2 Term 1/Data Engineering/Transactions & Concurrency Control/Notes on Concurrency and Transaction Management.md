
- learning objectives:
#### Overall: How to answer questions related to transaction control 

###### Specific: Understand the ways in which transactions are managed, and the reasons for maintaining concurrency through management 

B bought product X worth 100 from A. during transaction, the game server applies interest payments of 6%

B purchasing the product X from A **is transaction 1** 

and the interest of 6% **is transaction 2**

PDATE PLAYERS SET BALANCE=BALANCE+100, WHERE PLAYER NAME=A;
UPDATE PLAYERS SET BALANCE=BALANCE-100, WHERE PLAYER NAME=B;

Transaction 1

UPDATE PLAYERS SET BALANCE=BALANCE*1.06, WHERE PLAYER NAME=A;
UPDATE PLAYERS SET BALANCE=BALANCE*1.06, WHERE PLAYER NAME=B;

Transaction 2




AS IN:


T1: BEGIN A=A+100, B=B-100 END
T2: BEGIN A=1.06 * A, B=1.06 * B END

AS IN:

T1:      R(A),W(A),R(B),W(B)
T2:      R(B),W(B),R(B),W(B)


**Schedules**?

a schedule is a list of actions from a set of transactions

there is no guarantee that T1 will execute before T2, or vice versa, if both are submitted concurrently

FOR EXAMPLE:
![[Pasted image 20250508123526.png]]


**Question**

What is the difference between a **complete schedule and a serial schedule?**

complete is one that contains an abort or commit action (finalizes the transaction) a serial schedule is one where the actions of different transactions are not interleaved

so serial would be would be T1 and T2 occur, in like a queue


How do we avoid conflicts that lead to "reservation" problem?


ACID properties

- Atomicity
	- All writes to DB succeed, or none of them do (all or nothin)

- consistency
	- All fails occur gracefully, no invariants are broken (say a transaction breaks halfway through, the first part could happen and the second wont. need rollback, or finish write (ties into atomicity)) - atomicity guarantees consistency.

- isolation
	- Appears as if all transactions re executed independently of each other. No conditions race! - difficult - slow

- durability
	-  Committed writes don't get lost on disk

##### Lock based concurrency control / Deadlocks

each transaction must obtain S (shared) lock on object before reading, and an X (exclusive) lock on object before writing

e.g., T1: S(A), R(A), Release_S(A), X(B), W(B), Release_X(B)....

Shared A, Read A, release shared status, Exclusive the B, Write the B and Release the exclusive on the B

X conflicts with X and S

No transaction can obtain an X lock on an object if some other transaction has an X or S lock on that object
No object can obtain an S lock on an object if some other transaction has an X lock on that object

S locks however dont conflict, as its fuckin shared mate

**so whats strict two phase lokcing?**

each transaction must obtain a S (shared) lock on object before reading, and an X (exclusive) lock on object, before writing (Share it, so all can read it yanno, X for writing it so that its Isolated mate ACID)


**conflict serializable schedules**

two schedules are conflict equivalent if
	they involve the same actions of the same transactions
     Every pair of conflicting actions are ordered the same way     



**Conflict serializable vs Conflict equivalent**


serializable: You are able to transform S into a serial schedule by swapping consecutive non-conflicting operations of different transactions

GOT IT "WAITS-FOR!" - a waits for cycle can become a deadlock!


if (T i) writes an object, (T j) can read this, only after (T i) commits its write

n order to undo the actions of an aborted transaction, the DBMS
maintains a log in which every write is recorded.
• Log is also used to recover from system crashes: all active
transactions at the time of the crash are aborted when the system
comes back up
maintaining durability (ACID)
atomic, consistency, Isolated, durable