

with lists matching [] to the base case and (x:xs) for the recursive case

in the recursive case, do something to x and then recurse with xs

- reconstructing the structure of intermediate and return values to create the find returned structure of the function call

with lists, often constructing another list using the values calculated in the recursive case:

myMap :: (a->b) -> [a] -> [b]
myMap f []  = []
myMap f (x:xs) = (f x) : myMap f xs


( building return list with : )

Three computational patterns

Functor -> generalizing the idea of map to any shape of data

Applicative - generalizing Functor to multiple arguments functions

Monad - generalize the flow of computation depending on the result of functions involved in that computation


--

IO 
non-pure function which depends on the sate of the world. IO type, not pure.
**• getChar :: IO (Char)
• getLine :: IO (String)
• putChar ::Char -> IO ()
• putStr :: String -> IO () -- no newline at end
• putStrLn :: String -> IO () -- newline at end.**
