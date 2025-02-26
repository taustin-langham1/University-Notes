
**[Week 7 Slides](file:///C:/Users/langh/Downloads/2425-scc212-lecture-07-io-actions.pdf)**

- need non-pure functions (ones who's return values don't need to be clearly defined) 


# IO Actions

- `IO a` is the type of an IO Action
- An IO action is a non-pure function that depends on the state of the world
- the action is created, but not actually executed until we run it (see '*do*' notation) 
- often functions that result in IO actions take arguments, just like other functions (e.g., `fn :: String -> IO()`)
- But not all do (e.g., `getChar` that we will soon see)
	- a pure function with no arguments is a constant 
	- a non-pure function with no arguments does some side-effect


## IO Actions and return values

##### `IO a`

- IO actions are parameterized by a type a.
- This represents the return value of the action, which can be used by the rest of the program
	- e.g., IO (Int) is an IO action which return an Int value when run.
- Unlike pure functions, IO actions can return no value via `IO()`

### Aside: IO actions and Monads

- `IO a` is a member of the `Monad` typeclass because people realized that IO could be modelled with the same pattern, and therefore get access to all the useful functions defined on monads for free

- **I/O does not have to be implemented via Monad, and you don't need to know them to learn I/O!**
- we're learning via the concept of IO Actions, which focuses on the core issue.


## Running IO Actions

- once an IO action has been created, we need to actually run it 
- this is done one of two main ways
- using *do*, or explicitly `(>>=)` (do is actually just syntactic sugar for the `(>>=)`


## do notation

****
for example:

```Haskell
do act1
	x <- act2
	let y = act3 x
	act4 y
```

do notation takes the form of an indented block
- within the block each line can be of:
	- An IO action
	- A generator which runs an action and returns binds the value to an identifier 
	- A let cause calling pure functions
- The last line of the do block must return an IO type
****

## do notation and imperative programming

- it is important to understand that *do* notation isn't an escape hatch to general imperative programming
- it's slightly prettier syntax around the underlying `(>>=)` functions and its parameters passing

## return/pure

• The last value in a do block needs to be a value of type IO.
• If the last thing in the block is an IO action, then this is usually fine because the outcome of that action becomes the outcome of the do block.
• But you may have an IO action of a different type, or simply a value you’ve calculated via pure functions that you now want to return from the function but can’t because it’s not an IO type.
• Any value can be lifted into an IO value via the return or pure functions.
• eg, in a do block with type IO (String), we can convert a String to a IO (String) via pure “hello”
• The empty IO () type can be make via pure ()
• return is an alias of pure
• As Haskell added IO actions, it was thought to be helpfully named but has generated confusion by looking like C and it’s very different return statement. Just use pure. 


# Haskell's *main* function#


## main in Haskell

- like many programming languages, Haskell specifies a name for the function that will be called when your program starts. it is:
	- `main :: IO ()`
- The type signature means your program function takes no arguments, returns no value, and it's a non-pure function
- if you want to access any command line arguments, you can do it via functions in the `System.Environment` module
- if you want to set a program return values, you can do it via functions in the `System.Exit`

## Program-level design

- the type of definition of main might suggest that you are going to be programming with IO in all of your functions but no!
  - the main design principle for functional programming is "functional core/imperative shell"
  - This means the majority of the functionality of your program should be pure functions
  - only the bits necessary around the edges to interact with the real-world should be written as IO actions


# Terminal I/O


## printing to / reading from the terminal

• `getChar :: IO (Char)`
• `getLine :: IO (String)`
• `putChar ::Char -> IO ()`
• `putStr :: String -> IO ()` -- no newline at end
• `putStrLn :: String -> IO ()` -- newline at end.


## print vs putStr

there is also a print function:
	`print :: Show a => a -> IO ()`
• This function can print anything which is part of the Show typeclass.
• The putStr function only accept Strings.
• If you want to manually convert a value of a type which implements
Show to a String you can use the show function:
show :: Show a => a -> String
• So, putStr (show x) and print x are somewhat equivalent if Show is
implemented

# File I/O

• In the System.IO module, with some in the Prelude.
• Open the file and return the handle to use to access it later:
`openFile :: FilePath -> IOMode -> IO Handle`
• Open the file but instead pass a function to process the file and then close it after the function has exited:
`withFile :: FilePath -> IOMode -> (Handle -> IO r) -> IO r`
• Read/write entire files in one go:
`readFile :: FilePath -> IO (String) writeFile :: FilePath -> String -> IO `()
• Close an open file handle:
`hClose :: Handle -> IO ()`
• Reading and Writing chars and lines, eg:
`hGetChar :: Handle -> IO (Char) hGetLine :: Handle -> IO (String)
`hPutChar :: Handle -> Char -> IO () hPutLine :: Handle -> String -> IO ()`

 In Prelude
`readFile :: FilePath -> IO String`
• Opens and reads the entire contents of the file as a single string and
returns it.
• If there is a problem then it causes an exception instead.
• This can be a bit of a pain for the most common case – the filename
not existing, so it can be easier to check for that explicitly first rather
than handling the potential exception.

