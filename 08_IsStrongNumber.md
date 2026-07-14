# Is Strong Number? 
A number in which sum of the factorials of the digit is equal to the number.
```java
public static boolean isStrongNumber(int number){
	int originalNumber = number;
	int sum = 0;
	
	while (number > 0){
		int digit = number % 10; // getting the last digit

		sum += factorialOf(digit);
		
		number /= 10; // deleting the last digit
	}

	if (sum == originalNumber){
		return true;
	}

	return false;
}

public static int factorialOf(int number){

	if (number == 0) return 1;

	int product = 1;

	for (int i = number; i > 0; i--){
		product *= i;
	}

	return product;
}

```
