linear search will take as many steps as there are elements within the array, so O(n)

in the worst case scenario
binary search, in the worst case scenario will also only be dependent on how many elements are in the array, however only slightly, as an element with 100 in the list will only take 7 steps, so the relation isnt exactly N, its O(Log N) -> increases by one step every time the data is doubled (a weaker relation to N)

a step which isn't depended upon N, such as reading from an array, would just be O(1) 

### O(log N) Explained

##### Logarithms recap:

inverse of exponents

log^2 8      can also be written as:     "what exponent is needed on 2 to reach 8"

O(log N) is actually a shorthand version of O(log2 N), as you might see on a calculator log usually just means log2, the 2 is typically dropped

![[Pasted image 20250905142358.png]]

## Big O in Everyday Code















