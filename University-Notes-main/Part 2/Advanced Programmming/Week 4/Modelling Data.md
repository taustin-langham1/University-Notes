**[Week 4 Slides](file:///C:/Users/langh/Downloads/2425-scc212-lecture-04-modelling-data-pre.pdf)**

This material should allow you to represent any data you could represent in another language in Haskell instead.  You'll be familiar with type aliases, new types to avoid accidental value confusion, and the rich world of the data definition, including generics and recursive types.

- structuring data using list, defining new types with type, newtype, & data 

(typeclasses)
Num a => a -> string -> a, type a is an instance of the num type class

you can have more than one type class constraint 

(eq a, ord a ) => [a] - > Bool


## Structuring data

- so far: lists and tuples
	- you can approach an unlimited number of problems using these and it will work, but it often feels a bit awkward and unnatural


### Lists and Tuples

- Lists are homogeneous (of all the same type) and variable legth
- tuples are heterogeneous but fixed 'length'
	- tuples provide a useful way to return 'multiple' values from a function


### type keyword

type allows you to make a type alias (c.f. typedef in C) eg,

type Module = (String, Int, Int, Bool, [String])
type Age = Int

### newtype keyword

- defines a new type rather than an alias

it cannot be used interchangeably with types, its made up of

	newType Age = Ag Int
	
				 (Ag : Type constructior)

### deriving keyword

- add new type to the Show typeclass implementing the function show :: (Show a) => a -> String 
- deriving mechanism: it can automatically apply the appropriate typeclass functions to the underlying values as your instance of the typeclass
	- newtype Age = Ag Int
		- deriving (Show)

### data keyword

- allows us to define brand new data types
- the same language structure allows programmers to do several different things that have to be built into other languages separately
	- enumerations
	- sum types
	- parameterized types
	- recursive data types

### data for enumerations

- an enumeration is a list of all possible values a type can have
- the data keyword can do that by separating different values by a vertical bar


data Direction = North | South | East | West


each of these vales is called a constructor for the given type


### Storing actual values

data Student = MkStudent String Int Int    -- store 3 values

(can also have alternatives) data person = Person String | Student   -- Person with 1 value or student 

### Type constructors 

to make a value of a newtype or data type, we use one of the type constructors we have defined for the type
	for newtype there must be exactly one. data may have more than one 


Ag 56
Circle 5 5 10
Rect 0 0 150 100


the type constructors become just another function and can be used like one anywhere

for newtype we'd often use the same identifier as the type name but (Paul) used "Ag"
instead of "Age" to make the diff obv

type constructor is not the type, you dont use it in the definitions

### pattern marching on type constructors
//

### smart constructors

smart constructors are functions which take the needed data to create a value of a type, and returns a value of that type if the constraints are valid

if the constraints are invalid, try to return something that can communicate the error rather than crashing 


### data and parameterized types

### recursive data types

- types can be recursive 


