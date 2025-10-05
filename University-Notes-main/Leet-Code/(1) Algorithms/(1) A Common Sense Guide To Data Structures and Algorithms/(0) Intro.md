(this is my work in reading this book)
//

```

public static void Main(String[] args){
int [] Array = {3, 5, 6, 9, 10, 12, 15, 18, 20, 21};
fizzBuzz(Array);
}

public static void fizzBuzz (int [] Array){
	for (int i = 0; i < Array.length; i++){
	
		// most specific if satement must come first
		if (Array[i] % 5 == 0 && Array[i] % 3 == 0){
			System.out.println("FizzBuzz");
		}
		else if (Array[i] % 3 == 0){
			System.out.println("Fizz");
		}
		else if (Array[i] % 5 == 0){
			System.out.println("Buzz");
		}
	}
}

```
