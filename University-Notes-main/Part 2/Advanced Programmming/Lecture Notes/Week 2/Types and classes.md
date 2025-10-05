# Basic Types, Function Types, Basic classes


### Basic concepts
- types: collections of related values

v :: Bool
v = true

this defines v as a value of type bool, which is a collection of the two values: true and false

we use the notation v : : T to mean that v is a value in the type T and say that v has type T


- Haskell provides a static type system with several advanced features:

	- strongly typed: once a type is assigned to a value, that type cannot change
		- this ensures that operations on data are performed correctly and prevents a wide class of errors, such as using a string where a number is expected
	- statically typed: types are determined at compile time
		- many errors related to types are caught early, before execution

- what are the issues with dynamic type systems? like java script
	- in JS const result1 = "5" + 1; // = "51" (string concatenation)

Haskell's type system ensures type safety and type inference 
- every expression must have a type, which is calculated prior to evaluating the expression by a process called type inference 
- if evaluating an expression e would produce a value of type T, then e has type T, written e : : T

Type errors: 
	applying a function to one or more arguments of the wrong type is called a type error
e.g., 1 + false (one is a number and false is a logical value)

the downside: some expression that evaluate successfully could be rejected on type grounds 
e.g., if true then 1 else false

invalid, both possible values must have the same type


basic types include: 
	
Bool - logical values
char - single characters
string - strings of chars
int, integer - integer numbers
float, double - floating point numbers	

### List types

A list is a sequence of values of the same type:

	[false, true false] :: [Bool]

	 ['a','b','c','d']::[Char]
	 
in general: [T]is the type of lists with elements of type T

	Notes:

the type of a list says nothing about its length
the type of the elements is unrestricted. for example, we can have lists of lists

[[[['a'],['b','c']]]]  :: [[char]]

finally there is no restriction that a list must have a finite length


### Tuple types

a tuple is a finite sequence of values of different types 

(False,True) :: (Bool,Bool)

(False, 'a', True) :: (Bool,Char,Bool)

in general: 
(T1,T2....Tn) is the type of n-tuples whose i^th components have type Ti for any i in 1...n


	notes 

the type of a tuple encodes its size
![[Part 2/Advanced Programmming/Week 2/Pasted image 20250120142208.png]]

the type of components is unrestricted
![[Part 2/Advanced Programmming/Week 2/Pasted image 20250120142222.png]]


- finally, note that tuples must have a finite arity
	- to ensure that tuple types can always be inferred prior to evalutaion


- tuples of arity one, such as (False), are not permitted because they would conflict with the use of parentheses to make the evaluation order explicit, such as (1+2)*3

### Function Types

a function is a mapping from values of one type to values of another type

not :: Bool -> Bool

even :: Int -> Bool

function = type, takes Bool type and mapped (returns) a Bool Type

function even maps from integer to bool


the argument and result types are unrestricted. for example function with multiple arguments or results are possible using lists or tuples

add :: (Int,Int) -> Int
add (x,y) = x+y

zeroto :: Int -> [Int]
zeroto n = [0..n]


### polymorphic functions


- a function is called polymorphic ("of many forms") if its type contains one or more type variables

length :: [a] -> Int

	for any type a, length takes a list of values of type a and returns an integer


type variables can be instantiated to different types in different circumstances 

length [Flase,True]  a = bool
2
length[1,2,3,4]   a = int
4

type variables must begin with lower-case letter, and are usually named a,b,c, etc.

many ofthe functions defined in the standard prelude are polymorphic, for example:

![[Part 2/Advanced Programmming/Week 2/Pasted image 20250120143146.png]]

in some cases, the type of a polymorphic function give an indication about the function behavior

### Type classes

a class is a collection of types that support certain overloaded operations called methods

Haskell provides basic advanced classes, for example:

num - numeric types
eq - equality types
ord - ordered types


#### Type classes: Num

the num class contains types whose values are numeric
support the following methods

![[Part 2/Advanced Programmming/Week 2/Pasted image 20250120143429.png]]

num does not provide a division method


#### overloaded functions


- a polymorphic function is called overloaded if its type contains one or more class constraints

(+) :: Num a => a -> a -> a

for any numeric type a, (+) takes two values of type a and returns a value of type a

constrained type variables can be instantiated to any types that satisfy the constraints

![[Part 2/Advanced Programmming/Week 2/Pasted image 20250120143627.png]]

	note 

most of the prelude functions are overloaded:

![[Part 2/Advanced Programmming/Week 2/Pasted image 20250120143812.png]]

numbers themselves are overloaded

3 :: Num a => a, 3 can be int, integer, float, double


##### Type classes: Eq

##### Type classes: Ord

##### Type classes: show

##### Type classes: read

##### Type classes: integral

##### Type classes: Fractional


### Hints and tips

- when starting the types of polymorphic functions that use numbers, equality or orderings, take care to include the necessary class consttraints


- when defining a new function in Haskell, it is useful to begin by writing down its type


- within a script, it is good practice to state the type of every new function defined

why?

double x = x + x

Haskell inference

double :: Num a => a -> a

you might have wanted

double :: int -> Int