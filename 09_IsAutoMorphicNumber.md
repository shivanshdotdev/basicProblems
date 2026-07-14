# Is AutoMorphic?
A number whose square's last digit(s) is the number itself. $25^2 = 625$
```java
public static boolean isAutoMorphic(int number){

	int originalNumber = number;
	int squaredNumber = number * number;

	int digits = 0; // number of digits in the given number

	while (number > 0){
		number /= 10;
		digits++;
	}

	int extractor = 1; // 10^digits to extract the last digits to compare with the number given
	for (int i = 0; i < digits; i++){
		extractor *= 10;
	}
	

	if (originalNumber == squaredNumber % extractor){
		return true;
	}

	return false;
}

```
