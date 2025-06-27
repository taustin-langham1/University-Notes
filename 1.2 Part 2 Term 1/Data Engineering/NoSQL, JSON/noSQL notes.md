

**Types of data**


1. structured
		have a predefined model
		e.g., relational data
2. unstructured
		opposite of structured data 
		e.g., flat bin files
3. dynamic
		data that changes relatively frequently
		e.g., office documents
4. static
		Opposite of dynamic data
		medical imaging data etc



### scaling traditional databases


vertically 

hardware upgrades, faster CPU or more memory


horizontally 

done by adding more machines, required database sharding and likely replication

sharding is just allowing parallel access

, to benefit from parallel access

1. maximize the fraction of your program that can be parallelized
2. balance the workload of parallel processes
3. minimize the time spent on communication

okay, so whats replicating data?


- avoid performance bottlenecks
- avoid single point failures
- and hence enhancing salability, availability

The two-phase commit protocol

(2PCP) ensures consistency 


so step one is just asking if everyone is down and ready to vote

then they vote when theyve all voted yes, they move on to step 2

and in step two, the global commits are made to the participants, which then can do local commits to the replicated database servers!

cool!

**CAP!**

cap theorem!

consistency 
availability
partition tolerance - System works well across distributed
physical networks


1. Availability is compromised but consistency and
partition tolerance are preferred over it
2. The system has little or no partition tolerance.
Consistency and availability are preferred
3. Consistency is compromised but systems are always
available and can work when parts of it are
partitioned


the cap theorem proves that it is impossible to guarantee strict consistency and availability while being able to tolerate network partitions 

this results in database with relaxed ACID guarantees

in particular, such databases apply the BASE properties

**Basically Available:** the system guarantees availability

**Soft-State:** the state may change

**Eventual** consistency: the system will, at some point, be consistent anyway


## noSQL

▪ No strict schema requirements
▪ No strict adherence to ACID properties
▪ Consistency is traded in favor of Availability