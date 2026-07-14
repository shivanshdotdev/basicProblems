# First `n` Prime numbers.

Start from 2, check if prime, if prime, print else, ignore and check the next number.
```java
public static void logicMethod(int limit){
	// how many numbers are done
	int count = 0;
	int number = 2; // starting number which will always be two
	while (count < limit){
		if (isPrime(number)){
			System.out.println(number);
			count++;
		}
		// increase the number unless the required number of methods are printed.
		number++;
	}
}


public static boolean isPrime(int number){
	if (number == 1) return false;

	for (int divisor = 2; divisor * divisor <= number; divisor++){
		if (number % divisor == 0) return false;
	}

	return true;

}

```
