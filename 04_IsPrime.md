# IsPrime?
This approach is better. The non optimized approach can be check for each number less than the given number if it can divide the number or not, if not, its a prime, else its a composite number
Hence, we are technically still checking or brute forcing comparison with each number but instead, we set a limit on it.

In case to check the divisibility, there is not 30 comparisons from 2 to 31 instead **just 5 comparisons will be enough** to tell if the number is prime or not.
```java
public static boolean logicMethod(int number){
    // 1 is not a prime number
    if (number == 1) return false;

    // UNDERSTAND THIS LOGIC WELL
    /*
       Lets take a non-prime number - 36

       Factors are 
       2 x 18 = 36
       3 x 12 = 36
       4 x 9 = 36
       6 x 6 = 36
       9 x 4 = 36
       12 x 3 = 36
       18 x 2 = 36

       as you know that A x B = B x A

       so the numbers or factors are basically repeating after 6 x 6
       and surprisingly, its the square root of the 36 which is the given number 

       Factors are pair of two numbers that when multiplied, give the number 
       oneSmallNum x oneBigNum = givenNum

       When the small number gets bigger, the bigger number must get smaller to maintain the equality

       The actual factors of the numbers, as observed, are just repeating after the square root of the given number 

       If any number smaller than the sqaure root of the given number can completly divide the given number, the given number is not prime 
       
       Lets take the prime number 53, its factors are technically 1 and 53 only, 
       the square root of the 53 is somewhat 7 or 8 
       So if any number less than or equal to 8 can completly divide 53, its not prime, else 53 is a prime number 

       so 2, 3, 4, 5, 6, 7, 8; none of the numbers completly divide the number 53 hence its a prime number 


       ====== IN SHORT ======
       Brute-Force Check against all the numbers, less than square root of the given number, if they completly divide the given number or not
       if any number can divide the given number, its not prime else its a prime number 

     */

    // start the loop with 2, 
    // check if the number with which we are dividing is less than or equal to the square root of the given number of not 
    // // // IF YOU THINK HOW BELOW IT IS BEING DONE, if the divisor gets bigger than the square root, the product will be higher than the given number 
    // // // Hence it will only check for the numbers less than the square of the given number
    for (int divisor = 2; divisor * divisor <= number; divisor++){
        if (number % divisor == 0) return false;
    }

    return true;

}

```
