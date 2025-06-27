
FUNCTIONS ARENT CURRIED OR UNCURRIED, THEY CAN ALSO JUST BE PLAIN OLD FUNCITONS

**Uncurried Functions**

add :: (Int, Int) -> Int
add (x,y) = x+y

(takes a tuple single compound argument)

add' :: Int -> (Int -> Int)
add' x y = x + y

takes multiple arguments (curried)

why is currying useful?

they're more flexible than functions on **tuples** (so uncurried), because useful functions can often be made by partially applying a curried function

add' 1 :: Int -> Int
take 5 :: [Int] -> [Int]
drop 5 :: [Int] -> [Int]

to avoid excess parenthesis when using curried functions, two simple conventions are adopted:

association to the right Int -> Int -> Int -> Int
means Int -> (Int -> (Int->Int))


therefore, it is natural for function application to associate to the left 

mult x y z 
means ((mult x)y)z

type arrows associate to the right

function applications apply to the left


**Lambda expressions**

functions expressed without naming 

Lx -> x + x
nameless function that doubles x

![[Pasted image 20250527203618.png]]



1+2
(+) 1 2 

**case expressions**

case x of 

"" -> something
""-> something 
_ -> error ""

**guarded equations**

(p,d)
| p == "" = 
|otherwise = error ""

**pattern matching**

fallVelocity :: (String, Float) -> Float
fallVelocity ("earth", d) = sqrt (2 * 9.8 * d)
fallVelocity ("moon", d) = sqrt (2 * 1.6 * d)
fallVelocity (_, _) = error "Unsupported planet"



**list patterns**

[1,2,3,4]

means 1:(2:(3:(4:[])))

so functions on lists can be defined x:xs

which is just head:tail

or x:(xs:(xs(xs:[])))

x:xs patterns only work on non-empty lists

head x:_ = x

x:xs patterns must be parenthesised 

head (x:_) = x

**MAYBE / EITHER TYPES**

MAYBE IS MORE LIKE MAYBE OR NOTHING TYPE

safeDiv :: Int -> Int -> Maybe Int
safeDiv _ 0 = Nothing -- returns nothing
safeDiv x y = Just (div x y)


**EITHER IS MORE GENERAL AND LOOKS SIMPLER**
![[Pasted image 20250527204624.png]]



**TOTAL FUNCTIONS**


why use partial function over a total function?

**Domain guarantees exist externally** — you know certain inputs won't occur based on context. Example: `head` is safe if the list is known non-empty.