**[Week 6 Slides](file:///C:/Users/langh/Downloads/2425-scc212-lecture-06-lists-zips.pdf)**

**List comprehension - a powerful way to construct and transform lists**

## Local Bindings

### Local bindings - let....in

- Local bindings in Haskell are variables or functions that are defined within a limited scope, usually inside a function

- they help keep code organized, readable, and avoid unnecessary repetition by restricting certain definitions to where they are needed

`let ... in` and `where` allow us to define local bindings in Haskell, but they are used in different ways

- `let` introduces local bindings that are only available within the `in` expression
``` Haskell
squareSum :: Int -> Int -> Int
squareSum x y =
let a = x * x
b = y * y
in a + b
```

### Local bindings - where

- introduces local bindings that are available for the entire function body
	- definition oriented
	- the scope of the bindings is the entire function
```Haskell
squareSum' :: Int -> Int -> Int
squareSum' x y = a + b
where
a = x * x
b = y * y
```

#### Local bindings - examples (e.g., more readable)

![[Pasted image 20250217140810.png]]


## List Comprehensions
### Set Comprehensions

- in mathematics, the comprehension notation can be used to construct new sets from old sets

`{x^2 | x E {1...5}}`

the set 1,4,9,16,25 of all number x^2 such that x is an element of the set {1...5}

### List:

- in haskell, a similar comprehension notation can be used to construct new lists from old lists

`[x^2 | x <- [1...5]]`

the expression `x <- [1..5]` is called a generators



- comprehensions can have multiple generators
- changing the order of the generators changes the order of the elements in the final lists:
``` haskell
> [(x,y) | y <- [4,5], x <- [1,2,3]]
[(1,4),(2,4),(3,4),(1,5),(2,5),(3,5)]
```
- multiple generators are like nested loops, with later generations more deeply nested loops whose variables change value more frequently 

### Dependent Generators

- later generators can depend on the variables that are introduced by earlier generators

`> [(x,y) | x <- [1..3], y <- [x..3]]`

- using dependent generator we can define the library function that concatenates a list of lists:
```haskell
concat :: [[a]] -> [a]
concat xss = [x | xs <- xss, x <- xs]
```

#### Guards (i)

- list comprehensions can use guards to restrict the values produced by earlier generators

`[x | x <- [1..10], even x]`
the list [2,4,6,,8,10] of all numbers x such that x is an element of the list [1..10] and x is even

```haskell
factors :: Int -> [Int]
factors n = [x | x <- [1..n], n `mod` x == 0]
```

```haskell
prime :: Int -> Bool
prime n = factors n == [1,n]
```


#### Guards (ii)

pairsEvenOdd ns = [(x,y) | x <- ns, x `mod` 2 == 0, y `mod` 2 == 1, y <- ns]
/// compilation error because y 'mod' 2 == 1 appears before y is actually assigned a value.

## The zip function

- maps two lists to a list of pairs and their corresponding elements

`zip :: [a] -> [b] -> [(a,b)]`

e.g., 
``` haskell
> zip ['a','b','c']  [1,2,3,4]
	=[('a',1),('b',2),('c',3)]
```

### Zip example uses:

#### Pairs (pairs up a list):
``` haskell
paris :: [a] - > [(a,a)]
pairs xs = zip xs (tail xs)
```

#### sorted (Boolean):
``` haskell
sorted :: Ord a => [a] -> Bool
sorted xs = and [x <= y | (x,y) <- pairs xs]
```

#### positions (returns positions of selected value in a list):
``` haskell
positions :: Eq a => a -> [a] -> [Int]
positions x xs = [i | (x',i) <- zip xs [0..], x == x']
```


## String comprehensions

- because strings are just special kinds of lists, any polymorphic function that operates on lists can also be applied to strings. for example

```haskell
> length "abcde"
5
> take 3 "abcde"
"abc"
> zip "abc" [1,2,3,4]
[('a',1),('b',2),('c',3)]
```

- similarly, list comprehensions can also be used to define functions on strings, such counting how many times a character occurs in a string:

```haskell
count :: Char -> String -> Int
count x xs = length [x' | x' <- xs, x == x']
```

for example:
```haskell
> count 's' "Mississipi"
4 
```