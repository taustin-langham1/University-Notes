
**[Week 5 Slides](file:///C:/Users/langh/Downloads/2425-scc212-lecture-05-recursion-higher-order-functions.pdf)**

## Recursion

- expressions are evaluated by a stepwise process of applying functions to their arguments, for example

##### Factorial
``` Haskell
fac 3 = 
product [1...3] = 
product [1,2,3] = 
1 x 2 x 3 = 
6
```
in haskell, functions can also be defined in terms of themselves. such functions are called recusive

![[Pasted image 20250210140450.png]]
fac 0 = 1   # base case
fac n = n * fac (n-1) # recursive case

we can improve here by matching an afditional case

e.g., fac n 
    | n < 0 = error "Not defined for negative numbers"
    | n == 0 = 1
    | otherwise = n * fac (n-1)

### Why is recursion useful?

- some functions, such as factorial, and simpler to define in terms of other functions
- As we shall see, however, many functions can naturally be defined in terms of themselves (fibonacci)
- Haskell is a purely functional language and Haskell enforces immutability


### Performance issues

- recursive functions in Haskell are elegant but can lead to performance issues; they can cause stack overflow for large inputs

- the problem: Each recursive call waits for the result of the next call, leading to deep stack usage (Head recursion)

fac n = n * fac (n-1)


### Tail Recursion

- tail recursion optimizes memory usage by avoiding deep call stacks
- a function is tail recursive if the recursive call is the last operation in the function
- this allows Haskell to reuse the same stack frame instead of creating new ones
- Functional languages like Haskell rely on recursion rather than loops, making tail recursion crucial


- we use an accumulator to keep track of the result
- the recursive call is the last operation performed, no pending operations after the recursive call

funTail n acc = facTail (n-1)(n * acc)

![[Pasted image 20250210141551.png]]

- we prefer to keep the same number of arguments the function takes, for that we use helper functions
![[Pasted image 20250210141629.png]]

## Higher Order Functions


-  a function is called higher-order if it takes a function as an argument or returns a function as a result

![[Pasted image 20250210141717.png]]

![[Pasted image 20250210141816.png]]

### Why are they useful?

- common programming patterns can be encoded as functions within the language itself
	- Many repetitive programming patterns can be expressed as reusable higher-order functions
- Allow flexible and reusable functions; returning functions as value enables partial application in currying, making it easy to write specialize functions
- enable function composition
	- functions can be combined to create more complex behaviors


## The Map Function

- The higher-order Library function called map applies a function to every element of a list


map :: (a->b) -> [a] -> [b]

map applies a function to every element of a list
(map reverse)

![[Pasted image 20250210142423.png]]

## The Filter Function

- The higher-order library function filter selects every element from a list that satisfies a predicate

(filter even)

filter :: (a -> Bool) -> [a] -> [a]

a filter function can be defined using recursion

filter p [] = []
filter p [x:xs]
     | p x = x : filter p xs
     | otherwise = filter p xs

## The Foldr (Fold Right) Function

- a number of functions on lists can be defined using the following simple pattern of recursion, e.g.,
![[Pasted image 20250210142749.png]]

A number of functions on lists can be defined using the following simple pattern of recursion

f [] = v
f (x:xs) = x # f xs

f maps the empty list to some value v, and any non-empty list to some function # applied to its head and f of its tail

The higher-order library function foldr (fold right) encapsulated this simple pattern of recursion, with the function # and the value v as arguments

sum = foldr (+) 0

product = foldr ( * ) 1

or = foldr (||) False

and = foldr (&&) True 


- Foldr itself can be defined using recursion

![[Pasted image 20250210143259.png]]

- however, it is best to think of foldr non-recursively, as simultaneously replacing each (:) in a list by a given function, and [] by a given value


foldr ( * ) 1 [1,2,3] = replace each (:) by ( * ) and [] by 1

- even though foldr encapsulates a simple pattern of recursion, it can be used to define many more functions that might first be expeceted

### Foldr examples:

sum, product, length, reverse




