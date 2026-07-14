# Is ArmStrong Number?

The logic of counting digits in a number, extracting the digits from the number is used from earlier questions.

```java
public static boolean isArmStrongNumber(int number){
	int originalNumber = number;
	int expo = howManyDigits(number);
	int expoSum = 0;

	while (number > 0){
		int digit = number % 10;
		int digitExpo = 1;
		// a loop is being used instead of Math.pow() because it is too heavy, over engineered for smaller number
		// since it is made for complex exponents
		// CPU is faster with these smaller primitive integers data type.
		for (int i = 0; i < expo; i++){
			digitExpo *= digit;
		}

		expoSum += digitExpo;
		number /= 10;
	}

	if (expoSum == originalNumber){
		return true;
	}

	return false;

}

public static int howManyDigits(int number){

	if (number == 0) return 1;

	int count = 0;
	while (number > 0){
		number = number / 10;
		count++;
	}

	return count;
}

```
