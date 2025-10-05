**[Week 8 Slides](file:///home/thomas/Downloads/2425-scc212-lecture-08-everyday-haskell.pdf)**

*Designing and implementing larger programs, and how exceptions are dealt with, and could be implemented, in Haskell.*

# Overview

- using pre-existing modules.
- Exception and how to deal with them.
- Going through a couple of full question -> answer examples
- Motivate next week on patterns of computation.

# *base* library modules

## Code re-use


- part of writing programs is not re-inventing the wheel
- haskell's base library comes with many modules that might be useful when writing your programs
- it's worth having a quick look at some of them and how people organise modules in haskell

- Libraries are collections of modules
	- the name of the library is descriptive rather than being one of the module names
	- *base* is the library that provides the core runtime for Haskell, including the Prelude
	- Third-party libraries can be found via Hackage and used/installed via cabal/stack


## Overall module organisation

- modules are named in a hierarchical way eg, A.B.C.D.

- major top-level categories include

- Control: Provides things to do with control-flow and functions such as monadic packages exceptions, concurrency, issues
- Data: provides representations and functions to work with them such as the "built-in" types, trees, maps, graphs
- Foreign: anything to do with interacting with other languages in Haskell
- GHC: modules specific to GHC
- System: interacting with the OS and env
- Text: alternate ways to represent text

### Data.Char

- lots of functions and predicate on individual characters
- this allows you to manipulate and test character data in a way similar to C but without having to deal with the underlying ASCII/Unicode int values directly.
- if you really want to play with the underlying value, it also provides the chr and ord functions 

``` haskell
ord 'z'
chr 90
putStrLn $ [chr 9786]
```

### Data.List

more functions on building, searching, segmenting lists.
often more variants of simpler functions found in the prelude
`words/unwords` and `lines/unlines`
`intersperse`
`concat/concatMap`
`span/break/splitAt`
`permutations, replicate`


### Data.Maybe

`fromMaybe`
`mapMaybe`


# Exceptions in Haskell


## exceptions... why?

- you may recall from previous discussion that Haskell functions are pure, their output is entirely defined by their input, and we use structures like *Maybe* and *Either* to propagate errors
- but in the IO actions discussion, we talked about there being "IO exceptions"
- but haskell doesn't have exceptions as a language feature in the same way as other languages, so what is happening and how to deal with them in out programs

## Design principle

- exceptions are exceptional in Haskell
	• They are not intended to be used as a regular error-reporting mechanism,like they are in some languages like Java.
	• They are used for situations in which something can go wrong but it rarely happens and you rarely want to think about it in the middle of the code you are writing in that context.
	• Eg, writing to a file and the disk being full, a network connection dropping, divide by zero, etc.
	• These errors need to be dealt with, but dealing with them via returning Maybe/Either/etc would be a huge hassle for the >99.9% of times there is no error.

## Dealing with an exception

- the `Control.Exception` module (in base) contains types and functions to deal with and generate exceptions.

- *"catching" exceptions* is possible via one of several higher order functions that take a function which could generate an exception, a function that should be called if such an exception happens, and returns the value from the first one or from the exception handler if it happened
- there are several different exception types but the relevant ones are

- `IOException`
- `ErrorCall`
- `SomeException` - every type of error, almost never want to catch this

## catch

`catch :: Exception e => IO a (e -> IO a) -> IO a`


imagine catch as a kind of "run" function that takes your action and tries to run it, but if an exception happens, it runs the handler for you and returns that instead.

## How might exceptions work?

