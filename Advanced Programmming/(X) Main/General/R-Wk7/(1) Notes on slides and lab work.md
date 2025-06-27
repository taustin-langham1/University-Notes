facTail :: Int -> Int -> Int 
facTail acc = acc
factTail x acc = facTail (n - 1) (n*acc)



base case // head recursive n * fac
fac :: Int -> Int

fac 0 = 1
fac n = n * fac (n-1)




twice :: (a->a) -> a -> a
twice f x = f (f x)

