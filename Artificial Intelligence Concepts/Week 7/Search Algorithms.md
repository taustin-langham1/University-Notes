**[Week 7 Slides](file:///home/thomas/Downloads/SCC222-Week7.pdf)**

# search algorithms 

- Enable systems to find solutions efficiently in vast search spaces


three types:

> **Uniformed (Blind) Search Algorithms**
.- e.g.,
.- Breadth-First Search (BFS)
.- Depth-First Search (DFS)
.- Uniform Cost Search (UCS)

>**Informed Heuristic Search Algorithms**
.- Best-First Search 
.- A* Search 
.- Greedy Search

**Special Search Techniques**
- Bi-directional Search
- Iterative Deepening Search
- Beam Search
- Genetic Algorithms 
- Simulated Annealing 


## Uniformed (Blind) Search Algorithms

> Explore the search space without additional information about the goal location.
> Only use the problem definition to determine the next step

#### Depth-First Search


- Example: Traversing a maze:

- Start at root node
	- either given or arbitrary 
	- explore as far along each branch as possible before backtracking
	- use a stack to keep track of the nodes

![[Pasted image 20250228093456.png]]

1. Start at Node 2.1
	- note as visited, add to stack
	- not the end node
	- check adjacency list: {2.2}
2. Move to node 1.2
	- note visited, add to stack
	- not the end node
	- check adjacency list: {2.2}
		- {2.2} already visited
3. Backtrack to node 2.2
	- check adjacency list
	- 2.1 and 1.2 already visited
	- 2.3 and 3.2 free
4. Move to node 2.3
	- Note visited, add to stack
	- Not end node
	- Check adjacency list {2.2,2.4}
- Move to node 2.4... and so on.

#### Breadth-First Search


![[Pasted image 20250228093456.png]]
1. start at level 1 {2.1}
	-  node visited! 
	-  add to graph
	- Not end node
2. Move to level 2 {2.2}
	- Note as visited, add to graph
	- not end node
3. Move to level 3 {1.2,2.3,3.2}
	- Note as visited, add to graph
	- Not end node
4.  Move to level 4 {2.4,4.2}
	- note as visited, add to graph
	- not end node
5. Move to level 5 {4.1}
	- note as visited 
	- end node found


![[Pasted image 20250228094410.png]]


## Uniform Cost Search

- Naive Approach
- Dijkstra's Approach
- 
![[Pasted image 20250228100142.png]]


****

## Informed Heuristic Search 

#### A* Algorithm

- widely used in Pathfinding ect.


- aim 
	- find the shortest path from start, to end

informed search algorithm
Balances between BFS and Dijkstra, incorporating heuristics for optimisation


- **A* works by evaluating nodes using:***

```
f(n) = g(n) = h(n)
```

where:

`f(n)` = the estimated total cost of the cheapest path through node n 
`g(n)` = the cost from the start to node n 
`h(n)` = the heuristic estimate of the cost from node n to the end


- expand the node with the lowest f(n) value, to obtain an optimal path
- assuming that the heuristic h(n) does not overestimate the true cost


- the choice of heuristic function greatly affects the performance of A*. Examples include:
1.  Manhattan distance (e.g., for grid-based problems):

```
h(n) = |x goal - x n | + |y goal - y n|
```

1. euclidean distance (for path finding in the real world)


**A* pros and cons***

Advantages:
- Find the shortest path efficiently if the heuristic is well-designed 
- More optimal than Dijkstra's in many cases due to informed search
- flexible in different applications


Disadvantages:
- performance depends on heuristic funciton
- can be computationally expensive for large search spaces
- may degrade to Dijkstra's algorithm if the heuristic is not good

