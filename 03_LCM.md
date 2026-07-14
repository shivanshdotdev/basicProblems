# LCM
[HCF Logic is explained here](https://github.com/shivanshdotdev/basicProblems/blob/main/03_HCF.md)

```java
public static int logicMethod(int num1, int num2){
	int dividend = num1;
	int divisor = num2;
	int HCF;

	while (true){
		int remainder = dividend % divisor;

		if (remainder == 0) break;

		dividend = divisor;
		divisor = remainder;
	}

	HCF = divisor;
	
	// LCM x HCF = Product of the numbers

	// int LCM = (num1 * num2) / HCF;
	// THE ABOVE is not wrong but considering the edge cases
	// the product can be larger than 32-bit int size causing the wrap back to the negative
	// hence getting the wrong answer

	// with this way, that is fixed
	// since the num1 is perfectly divisible with the HCF, we will get a complete integer
	// multiplied with the num2 giving the LCM
	int LCM = (num1 / HCF) * num2;
	return LCM;
}

```
