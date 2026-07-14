# Is Palindrome?
Palindrome is the number is same when read from right and left, such as 121 or 1331 or 12321, etc.
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args){
        System.out.println(logicMethod(12345));
        System.out.println(logicMethod(129837));
        System.out.println(logicMethod(121));
    }

    public static boolean logicMethod(int number){
        if (number < 0){
            return false; // negative numbers can never be palindromes since -121 will be 121- which is not a negative number
        }

        int reversed = 0;

        int digit;
        int oringalNumber = number;
        while (number > 0){
            digit = number % 10;
            reversed = (reversed * 10) + digit;
            number /= 10;
        }

        return oringalNumber == reversed;
    }
}

```
