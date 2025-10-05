## Sorting (max-heap)

``` python

def heap_sort(self, lst: List[int]) -> None:

	def max_heap(heap_size, index):
		left = 2 * index + 1
		right = 2 * index + 2
		larges = index
		if left < heap_size and lst[left] > lst[largest]:
			largest = left
		if right < heap_size and lst[right] > lst[largest]:
			largest = right
		if largest != index:
			lst[index], lst[largest] = lst[largest], lst[index]
			max_heap(heap_size, largest)
	
	
	for i in range(len(lst))
		max_heap(len(lst), i)
	
	# this is the sorting of the elements in the heap	
	for i in range(len(lst) -1, 0, -1):
		lst[i], lst[0] = lst[0], lst[i]
		max_heap(i, 0)
		
		
	
```

```




```

## Searching (max-heap)

```



```