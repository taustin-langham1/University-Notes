# Operating Systems 







# Caching
## caching principle
### data storage technologies

the data transfer between CPU, memory and disk

- CPU issues a load/store instruction
- the data is transferred to an on-chip register

Disk is the slowest, RAM much faster
SSD faster by far than HDD

### memory hierarchy and locality of reference

why is this important?

CPU is more than 100x faster than DRAM

the faster something his (SRAM, before Regs, L1/2/3 regs) the smaller faster and more costlier it is


Local disks hold files retrieved from disks on remote servers ->
main memory holds disk blocks retrieved from local disks


**Cache:** is a smaller, faster storage device that acts as a staging area for subset of the data


what's the difference between temporal and spatial locality in terms of programs using data and instructions

- temporal - program uses more recently accessed data
- spatial - program has data near recently accessed addresses is likely to be accessed soon

Loops have good temporal and spatial locality with respect to
instruction fetches. The smaller the loop body and the greater the
number of loop iterations, the better the locality.

## Basic cache concepts  
### cache replacement policies

????



## Caching in the internet 
### server-side caching

• Globally distributed storage with caching:
• Caching is important for cost-effective and scalable storage.
• Large-scale systems (e.g., Facebook, Google) require caching to reduce latency and
improve performance.
• Key Requirements:
• Replication and Redundancy: Ensure data availability and fault tolerance.
• Handle failures gracefully and ensure load balancing for high availability.
• Goals of Server-Side Caching:
• Near real-time communication: Provide low-latency access to cached data for millions of
users worldwide
• Manage Popular Shared Content: Enable rapid access and updates to hot (frequently
accessed) content like trending posts or shared resources
• Massive Scalability: Handle millions of requests per second while maintaining low
response times 


### caching at distributed servers


CDN - Content Distribution Networks