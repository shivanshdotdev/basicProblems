# Reversing the Numbers
This approach works but its too heavy without any benefits.
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args){
        System.out.println(logicMethod(12345));
        System.out.println(logicMethod(129837));
    }

    public static int logicMethod(int number){
        if (number == 0){
            return 0;
        }

        if (number < 0){
            number = -number;
        }
		
		// double loop and Math.pow() are just performance overheads
        int digitsRemaining = 0;
        int numberCopy = number;
        while (numberCopy > 0){
            numberCopy /= 10;
            digitsRemaining++;
        }


        int reversed = 0; 
        int digit;
        while (number > 0){
            digit = number % 10;
            digitsRemaining--;
            reversed += digit * Math.pow(10, digitsRemaining);
            number /= 10;
        }

        return reversed;
    }
}

```
So the better approach is by multiplying the reverse result on the fly without storing much info.
```java
public static int logicMethod(int number) {
    if (number == 0) return 0; 

    boolean isNegative = number < 0;
    if (isNegative) {
        number = -number;
    }

    int reversed = 0;
    while (number > 0) {
        int digit = number % 10; // get the last digit
        
        reversed = (reversed * 10) + digit;
        // the reversed number is multiplied with 10 so there is a empty place at the unit digit
        // at which the digit variable value will be stored
        
        /*
        number = 456
        
        [loop 1]
        digit = 6
        rev = (0 * 10) + 6 = 0 + 6 = 6
        num = 45
        
        [loop 2]
        digit = 5
        rev = (6 * 10) + 5 = 60 + 5 = 65
        number = 4
        
        [loop 3]
        digit = 4
        rev = (65 * 10) + 4 = 650 + 4 = 654
        
        AND HENCE THE NUMBER IS REVERSED.
        
        */
        
        
        number /= 10;
    }

    return reversed;
}
```
