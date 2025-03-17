


#### The problem 

any piece of code you write might contain mistakes, or will have to be written and understood by someone else.

lets see how haskell allows use to use and define powerful patterns of computation within the language

'
## Caring about *structure*

- beginner programmers tend to care primarily about *code* (instructions)
	- the lines of code they write that make up the program
	- the mechanical nature of how things run step-by-step
	- the data/variables the program needs to run is often overlooked, leading to scenarios like not knowing how to get a piece of code working when all that was needed was another variable to track a value, for example
- Cognitively, they are spending too much of their mental effort getting something to happen to be able to also think about data in their program


- as programmers in sill and experience, they transition to primarily caring about data
	- what is my data? what is it's "shape"?
	- what are its inter-dependencies?
	- what data is transient in a calculation and what needs to be kept around?
	- whats a nice way to manipulate in the way i need to in order to write my program simply (ie, not just whatever structure it's in in an input file format)
- The code part becomes "simple" because it's putting together the coding building blocks you've used a lot (experience) and because the way you've structured the data might actually simplify the algorithm/code needed (eg deciding a bit of data is always sorted, or storing street names in a graph so finding a connection between two is just a standard graph traversal algorithm)
- the cognitive load of coding instructions reduces, freeing up capacity to reflect on data.


- functional programmers tend to care even more about the structure of data
	- partially that is because it is more maths-influenced programming paradigm
- A lot of the design approach for functional programming is based on structure too

## Structure in FP function design - recursion
