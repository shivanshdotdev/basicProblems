# Arrays
Methods or Problems that are covered in this code are the following: 
- Largest number 
- Smallest number
- Average of numbers
- Number of even and odd numbers 
- Linear search
- Binary search 
- Reversing the array in place(without creating another array object) **Two Pointers**
- Rotation toward left and right
- Second largest number

```java

import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args){

        int[] numbers = {42, 7, 89, 13, 56, 91, 4, 73, 28, 65, 19, 82, 34, 50, 97, 12, 68, 23, 77, 61};
        int[] sortedNumbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20};

        System.out.println(max(numbers));
        System.out.println(min(numbers));
        System.out.println(avg(numbers));
        System.out.println(evenOdd(numbers));
        
        System.out.println(search(numbers, 77));
        System.out.println(binarySearch(sortedNumbers, 14));

        System.out.println(Arrays.toString(sortedNumbers));
        reverseInPlace(sortedNumbers); // also known as two pointers
                                       //
        System.out.println(Arrays.toString(sortedNumbers));
        reverseInPlace(sortedNumbers); // to make the array in original position again

        rotate(sortedNumbers);
        System.out.println(Arrays.toString(sortedNumbers));
        rotate(sortedNumbers, false);
        System.out.println(Arrays.toString(sortedNumbers));

        System.out.println(secondLargest(numbers));

    }

    public static int max(int[] arr){
        int max = arr[0];

        for (int i : arr){
            if (i > max){
                max = i;
            }
        }

        return max;
    }

    public static int min(int[] arr){
        int min = arr[0];

        for (int i : arr){
            if (i < min){
                min = i;
            }
        }

        return min;
    }

    public static double avg(int[] arr){
        int count = arr.length;
        int sum = 0;

        for (int i : arr){
            sum += i;
        }

        return (sum / (count * 1.0));
    }

    public static String evenOdd(int[] arr){
        int even = 0;
        int odd = 0;

        for (int i : arr){
            if (i % 2 == 0) {
                even++;
            }
            else {
                odd++;
            }
        }

        return ("Even: " + even + ", Odd: " + odd);
    }

    public static int search(int[] arr, int x){
        int len = arr.length; 
        for (int i = 0; i < len; i++){
            if (arr[i] == x){
                return i;
            }
        }

        return -1;
    }

    public static int binarySearch(int[] arr, int x){
        int start = 0;
        int end = arr.length - 1;

        while (start <= end){
            int lookup = (start + end) / 2;

            int number = arr[lookup];

            if (number == x) return lookup;
            else if (number > x) end = lookup - 1;
            else start = lookup + 1;
        }

        return -1;

    }

    public static void reverseInPlace(int[] arr){
        int left = 0;
        int right = arr.length - 1;

        while (left < right){
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--; 
        }
    }

    public static void rotate(int[] arr, boolean right){
        if (right){
            int itemBeingLost = arr[arr.length - 1];
            int saver = arr[0];
            int updater = saver;
            for (int i = 1; i <= arr.length - 1; i++){
                saver = arr[i];
                arr[i] = updater;
                updater = saver;
            }

            arr[0] = itemBeingLost;
        }
        else {
            int itemBeingLost = arr[0];
            int saver = arr[arr.length - 1];
            int updater = saver;
            for (int i = arr.length - 2; i >= 0; i--){
                saver = arr[i];
                arr[i] = updater;
                updater = saver;
            }

            arr[arr.length - 1] = itemBeingLost;
        }
    }

    // THIS APPROACH IS THE DOCUMENTED VERSION 
    // SINCE THE LAST TIME IS BEING PRESERVED, THE LOOP IS BEING PLAYED BACKWARD, MODIFYING THAT LAST ELEMENT AND SO ON
    //
    //
    // public static void rotateRightStandard(int[] arr) {
    //     int temp = arr[arr.length - 1]; // Save the last element
    //
    //     for (int i = arr.length - 1; i > 0; i--) {
    //         arr[i] = arr[i - 1];
    //     }
    //
    //     arr[0] = temp; 
    // }

    public static void rotate(int[] arr){
        rotate(arr, true);
    }

    public static int secondLargest(int[] arr){
        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;

        for (int i: arr){ 
            if (i > largest){
                secondLargest = largest;
                largest = i;
            }

            else if ( i > secondLargest){
                secondLargest = i;
            }
        }

        return secondLargest;
    }
    
}
```

