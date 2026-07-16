# String related problems/methods

The Problems or Methods discussed in the following code are:-

⭐ has a better version as well.

- Reversing the String
- Checking if the is String is Palindrome ⭐
- Vowel counting 
- Word counting - Most Fun
- Removing Spaces from the string ⭐
- Toggle Case Conversion ⭐
- Character counting⭐

```java
import java.util.Arrays;
import java.util.HashMap;
import java.util.Scanner;

public class Main {
    public static void main(String[] args){

        System.out.println(reversed("This is a fantastic stuff."));
        System.out.println(isPalindrome("This is not"));
        System.out.println(isPalindrome("racecar"));
        System.out.println(betterIsPalindrome("This is not"));
        System.out.println(betterIsPalindrome("racecar"));

        System.out.println(vowelCount("This has two."));

        System.out.println(wordCount("This has three but actually no, there are more than three."));
        System.out.println(removeSpaces("This has three but actually no, there are more than three."));
        System.out.println(toggleCase("Something fishy is going on."));

        System.out.println(charactersCount("This is some basic test i am doing").toString());
    }

    public static String reversed(String str){
        StringBuilder string = new StringBuilder();
        for (int i = str.length() - 1; i >= 0; i--){
            string.append(str.charAt(i));
        }

        return string.toString();
    }

    public static boolean isPalindrome(String str){
        str = str.toLowerCase();
        if (str.equals(reversed(str))){
            return true;
        }

        return false;
    }

    public static boolean betterIsPalindrome(String str){

        str = str.toLowerCase();
        int left = 0;
        int right = str.length() - 1;

        while (left <= right){
            if (str.charAt(left) != str.charAt(right)){ // char is a primitive backed by ASCII values so they can be compared with == or !=
                return false;
            }

            left++;
            right--;
        }

        return true;
    }

    public static int vowelCount(String str){
        str = str.toLowerCase();
        int count = 0;
        String vowels = "aeiou";

        for (int i = 0; i < str.length(); i++){
            // indexOf() returns -1 if not found
            // charAt() returns the character at the index
            // search of the character in the vowels string, if found means anything other than -1, it means its a vowel, hence increment the count variable
            if (vowels.indexOf(str.charAt(i)) != -1){
                count++;
            }
        }

        return count;
    }

    public static int wordCount(String str){

        if (str == null || str.isEmpty()){
            return 0;
        }

        int words = 0;
        boolean inWord = false;

        // possible symbols that mark the end of the word
        String delimiters = " ,.;:";

        str = str.trim();
        for (int i = 0; i < str.length(); i++){
            char currentChar = str.charAt(i);

            // indexOf() returns the index of the character found and -1 if character does not exist
            // so if current character is something that ends a word
            // its index will be found in the delimiters string hence returning a number other than or not equal to -1
            // indicating that the word has ended
            if (delimiters.indexOf(currentChar) != -1){

                // final check that we were actually in a word
                if (inWord){
                    //because the word has ended, the count is incremented and state is changed since we are no longer in the word
                    words++;
                    inWord = false;
                }
            }

            // the above condition throws -1
            // means the current character is not a delimiters >>> word is still going on or new word has started
            // so just change the state that we are now in a word
            else{
                inWord = true;
            }

        }

        if (inWord){
            // the entire string is ended
            // but we are still in a word 
            // which means the string ended without a delimiter 
            // and we were counting the words based on delimiters 
            // hence the final word is missed 
            // so just balancing it out
            words++;
        }

        return words;

    }

    public static String removeSpaces(String str){
        if (str == null) return null;

        StringBuilder string = new StringBuilder();

        for (int i = 0; i < str.length(); i++){
            char currentChar = str.charAt(i);
            if (currentChar != ' '){
                string.append(currentChar);
            }
        }

        return string.toString();

    }

    // A ONE LINER FOR THE ABOVE CODE 

    // public static String removeSpaces(String str){
    //     if (str == null) return null;
    //     return str.replace(" ", "");
    // }

    public static String toggleCase(String str){
        if (str == null) return null;

        StringBuilder string = new StringBuilder();

        for (int i = 0; i < str.length(); i++){
            char currentChar = str.charAt(i);

            if (currentChar <= 90 && currentChar >= 65){
                char currentCharFormatted = (char) (currentChar + 32);
                string.append(currentCharFormatted);
            }
            else if (currentChar <= 122 && currentChar >= 97){
                char currentCharFormatted = (char) (currentChar - 32);
                string.append(currentCharFormatted);
            }
            else {
                string.append(currentChar);
            }

        }

        return string.toString();
    }

    // READABLE, CLEAN APPROACH FOR THE ABOVE CODE

    // public static String toggleCase(String str){
    //     StringBuilder string = new StringBuilder();
    //
    //     for (int i = 0; i < str.length(); i++){
    //         char currentChar = str.charAt(i);
    //
    //         if (Character.isUpperCase(currentChar)) string.append(Character.toLowerCase(currentChar));
    //         else if (Character.isLowerCase(currentChar)) string.append(Character.toUpperCase(currentChar));
    //         else string.append(currentChar);
    //     }
    //
    //     return string.toString();
    // }

    public static HashMap<Character, Integer> charactersCount(String str){
        if (str == null) return null;

        HashMap<Character, Integer> log = new HashMap<>();

        str = str.toLowerCase();

        for (int i = 0; i < str.length(); i++){
            char currentChar = str.charAt(i);

            // if (log.containsKey(currentChar)){
            //     int currentCount = log.get(currentChar);
            //     log.put(currentChar, ++currentCount);
            // }
            // else{
            //     log.put(currentChar, 1);
            // }

            // THE ABOVE IF-ELSE CAN BE REPLACED WITH 

            // if currentChar is in the hashmap, use its value and + 1 
            // if its not in it, use 0 and + 1
            log.put(currentChar, log.getOrDefault(currentChar, 0) + 1);
        }

        return log;

    }

}
```
