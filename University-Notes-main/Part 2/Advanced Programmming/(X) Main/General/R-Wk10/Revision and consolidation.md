## **1 - Given Type, What code**

Which of the following code expressions has the type:
`Int`
Question 1 
a.
`map (+1) [1..5]` - list?
b.
`foldr (+) 0 [1..5]` - this one
c.
`Just 5` - just?


Which of the following code expressions has the type:
`[a] -> [a]`
Question 2 
a.
`map (+)`
b.
`filter (>5)`
c.
`f [] = []`  
`f (x:xs) = x : x : f xs` - this one 
d.
`f [] = []`  
`f (x:xs) = if x>=0 then True : f xs else False : f xs`

What code can replace the ??? to give the following code the correct type?

`find :: (a->Bool) -> [a] -> Bool`  
`find f [] = False`  
`find f (x:xs) | f x == True = True`  
              `| ???`

Question 3 

a.
`f x == False = f x`

b.
`find f xs`

c.
`otherwise = find f xs`

d.
`f x == False = find f xs` - this one 



## **2 - Given code, What type?**

Given:

`x = 5`

What is the **type** of the following code:

`x > 10`

Question 1
a.
Int
b.
False
c.
True
d.
Bool - bool?  true?
e.
Num a



What is the **type** of the following code:

("Fruit", [0.58, 1.99, 0.78, 4.45])

Question 2 

a.
`Fractional a => (String, [a])` - this
b.
`(String, [Float])` - this
c.
`(String, [Double])`
d.
`[String, [Float]]`
e.
`(String, Float, Float, Float, Float)`


Reminder of Prelude functions:

`map :: (a -> b) -> [a] -> [b]`  
`maximum :: (Foldable t, Ord a) => t a -> a`

What **type** needs to replace ??? in the following code for it to work?

`f :: **???** -> [a] -> b`  
`f x y = maximum (map x y)`

Question 3 

a.
Ord b => (a->b) - this

b.
(a->b)

c.
Ord a => (a->b)

d.
a

## **3 - merge**

merge :: Ord a => [a] -> [a] -> [a]
merge [] ys = ys
merge xs [] = xs
merge (x:xs) (y:ys)   -> Deconstruction of lists
	| x <= y  =  x : merge xs (y:ys) Reconstruction
	| otherwise  = y : merge (x:xs) ys Reconstruction 


1. type, takes two parameters, two lists. [a] & [a] -> [a] / compare sorted variables so ORD
2. recursive function, so recursive case + base case 
	1. Stop doing recursion, if one list is empty (i.e., xs[]/ys[])
3. Take one at a time from each of the lists (head:tail) (head:tail)
4. if x is smaller than y x : merge to xs and (y:ys)
5. if y is smaller than x y : merge to (x:xs) ys

x is the smaller head, so x is placed at the front of the merged list, remaining merge happens between xs and (y:ys)
## **4 - sort**


sortDecs :: Ord a => [a] -> [a]
sortDecs [ ]         = []
sortDecs (x:xs) = sortDecs [a | a <- xs, a > x]
		++ [x] ++
			sortDecs [a | a <- xs, a <= x]

concatenate through ++ x ++



## **5 - employee type**





## **6 - explanation A & B**

partial function::

a partial function is when  function with multiple arguments is applied to fewer arguments than it requires, producing a new function that takes the remaining arguments.

In Haskell all functions are curried by default, meaning they take arguments one at a time

Turns multi-argument functions into simpler, reusable ones by supplying some arguments only

I/O -> yields a result with the IO type. 

putStrLn "Hello"

getChar :: IO (Char)

sum [1..10]

isweekend :: string -> [bool]
isweekend day = 
if day == "sunday" then true else
if day -- "saturday" then true else false


or isweekday "saturdaysunday" false
isweeked _  = true


static type system

strongly typed: once a type is assigned to a value, cannot be changdd
- ensures operations on data are performed correctly
- 

statically: type determined at runtime