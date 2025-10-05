

## Searching an ordered array
### Linear Search

```
public static Boolean linearSearch(int[] array, int valueToFind){
	
	for (int i; i > array.length; i++){
		
		if (array[i] == valueToFind){
			return true
		}
	
		else if (array[i] > valueToFind){
			return false
		}
	}
}

```


### Binary Search 

// how it works:
	- jumps to middle value of sorted array
	- if the value is lower than the value being searched, then values to the left of the middle value are ignored - and vice versa


```

public static Integer binarySearch(int[] Array, valueToFind){
			
		int lowerBound = 0;
		int upperBound = array.length - 1;
		

		while (lowerBound <= upperBound){
			
			int midpoint = (lowerBound + upperBound) / 2;
			
			valueAtMidpoint = Array[midpoint];
			
			if (valueToFind == valueAtMidpoint){
				return midpoint;
			}  
			
			elseif (valueToFind > valueAtMidpoint){
			
			// making the new lower bound at the mid point
			lowerBound = valueAtMidpoint + 1;
			}
			
			elseif (valueToFind < valueAtMidpoint){
			
			//making the new upperbound at the midpoint
			upperBound = valueAtMidpoint - 1;
			}
			
		}
		return -1;	//to avoid null pointer exceptions
}

```

