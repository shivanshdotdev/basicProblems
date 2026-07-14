# Perfect Number?

A number which is equal to the sum of the all the factors of it starting from 1 excluding itself.

```java
public static boolean logicMethod(int number){
	
	if (number == 1) return false;

	int divisorSum = 1; // starting with 1 because 1 will be included with every number greater than 1
	
	// Optimization logic explanation is attached at the bottom
	for (int divisor = 2; divisor * divisor <= number; divisor++){

		if (number % divisor == 0){

			divisorSum += divisor;
			int secondDivisorPair = number/divisor; 

			if (divisor != secondDivisorPair){ // so that in case of perfect square numbers, there square roots are not added twice
				divisorSum += secondDivisorPair;
			}
		}
	}

	if (divisorSum == number) return true;

	return false;
}

```
[Optimization Logic](https://github.com/shivanshdotdev/basicProblems/blob/9ce77d98ac631c089751b3d3c2fa5f08cfead738/04_IsPrime.md?plain=1#L11)
