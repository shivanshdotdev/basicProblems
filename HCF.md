# HCF
Euclid's Division Algorithm to calculate the HCF is used here.
![](https://media.geeksforgeeks.org/wp-content/uploads/20241121154345763319/euclid---------s---------division---------algorithm---------3.webp)
```java
// AS CAN BE SEEN ABOVE
// when the remainder is 0, the divisor is the HCF

public static int logicMethod(int num1, int num2){
	/*
	Technically the dividend should be the bigger number and divisor should be the smaller 
	BUT here, that requirement is being fulfilled automatically 
	
	in case the num2 > num1
	hence divisor is greater than the dividend
	
	at the end of the while loop, both will be swapped
	becase less dividend is technically the remainder 
	*/
	int dividend = num1;
	int divisor = num2;

	while (true){
		int remainder = dividend % divisor;

		if (remainder == 0) break;

		dividend = divisor;
		divisor = remainder;
	}

	return divisor;
}

```
