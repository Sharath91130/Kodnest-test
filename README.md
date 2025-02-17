# Kodnest-test

Programming
Letters Shifting

In ancient Arcadia, a secret message written in a string 's' of lowercase letters must be deciphered using a magical shifting technique. An array 'shifts', where 'shifts[i]' indicates the number of shifts for the first 'i + 1' letters in 's', holds the key to unlocking the message. Each shift advances a letter to the next in the alphabet, with 'z' cycling back to 'a'. Decode the message by applying the shifting rules to unveil Arcadia's hidden secrets.

The first letter is influenced by all shifts in the array.

The second letter is affected by all shifts except the first one.

The third letter is affected only by the last shift.

Sample Test Case:

Sample Input:

kodnest
[2,5,7,9,2,1,4]
Expected Output:

oqadlxx


#pgm 
import java.util.*;
public class Main {

    public static void support(StringBuilder s, long arr[], char alpha[]){
        for(int i=0; i<arr.length; i++){
            long a = s.charAt(i)-97;
            a = a+arr[i];
            a=a%26;
            s.replace(i,i+1,alpha[(int)a]+"");
        }
    }
    public static String shiftingLetters(String str, int[] arr) {

        StringBuilder s = new StringBuilder(str);
        char alpha[] = new char[26];
        char ch = 'a';

        for(int i=0; i<26; i++){
            alpha[i] = ch;
            ch++;
        }

        int n = arr.length;
        long a[] = new long[n];
        a[n-1] = arr[n-1];

        for(int i=n-2; i>=0; i--){
            a[i] = a[i+1]+arr[i];
        }

        support(s,a,alpha);
        return s.toString();
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        String s = sc.nextLine();
        // Split the string by comma
        String[] stringArray = s.substring(1, s.length() - 1).split(",");

        // Convert to integer array
        int[] intArray = new int[stringArray.length];
        for (int i = 0; i < stringArray.length; i++) {
            intArray[i] = Integer.parseInt(stringArray[i].trim());
        }
        System.out.println(shiftingLetters(str,intArray));
    }

}

*code 2
Programming
Complex Data Aggregation and Manipulation

In a bustling city in India, there is a software engineer named Priya who is working on an important data analysis project. She has received a mixed list of values, some are integers, and others are strings. Priya’s task is to separate the even and odd numbers into two different lists while concatenating all the string elements into one continuous string. Once the separation and concatenation are complete, Priya must return three distinct results: a list of even numbers, a list of odd numbers, and the concatenated string of all the text elements.

Sample Test Case:

Sample Input:

9, "2", 2, "is", 4, "Prime"
Expected Output:

[[2, 4], [9], 2isPrime]

import java.util.*;

public class Main {

    // Method to process the data
    public static List<Object> processData(List<Object> data) {
        List<Integer> evenNumbers = new ArrayList<>();
        List<Integer> oddNumbers = new ArrayList<>();
        StringBuilder concatenatedStrings = new StringBuilder();
        
        for (Object obj : data) {
            if (obj instanceof Integer) {
                int num = (Integer) obj;
                if (num % 2 == 0) {
                    evenNumbers.add(num);
                } else {
                    oddNumbers.add(num);
                }
            } else if (obj instanceof String) {
                concatenatedStrings.append((String) obj);
            }
        }
        
        List<Object> result = new ArrayList<>();
        result.add(evenNumbers);
        result.add(oddNumbers);
        result.add(concatenatedStrings.toString());
        return result;
    }

    // Main method
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        
        // Split the input by commas, while keeping quoted strings intact
        String[] inputArray = input.split(",\\s*");
        
        List<Object> data = new ArrayList<>();
        
        // Process the input and add either integers or strings to the data list
        for (String item : inputArray) {
            if (item.matches("-?\\d+")) {
                data.add(Integer.parseInt(item.trim())); // Add number
            } else {
                // Remove surrounding quotes and add string
                String trimmedItem = item.trim();
                if (trimmedItem.startsWith("\"") && trimmedItem.endsWith("\"")) {
                    data.add(trimmedItem.substring(1, trimmedItem.length() - 1));
                } else {
                    data.add(trimmedItem);
                }
            }
        }

        // Call the method to process the data
        List<Object> result = processData(data);
        System.out.println(result);
    }
}

# code 3

Swapping Peak Element

In an NCC group, there's a rule stating that if a cadet is taller than both of the adjacent cadets, they must move to the front. Identify such a cadet and relocate them accordingly.

Sample Test Case:

Sample Input:

4
1 7 6 1
Expected Output:

[7, 1, 6, 1]

import java.util.*;
public class Main {

    public static String swap(int[] array, int index1, int index2) {
        int temp = array[index1];
        array[index1] = array[index2];
        array[index2] = temp;
        return Arrays.toString(array);
    }
    
    public static Integer findPeakElement(int[] arr) {

        int left = 0;
        int right = arr.length - 1;

        while (left < right) {
            
            int mid = left + (right - left) / 2;
            
            if (arr[mid] > arr[mid + 1]) {

                right = mid;

            } else {

                left = mid + 1;
            }
        }

        if (left == arr.length - 1 && arr[left - 1] <= arr[left]) 
                return 0;  
                
        return left;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();

        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        int index = findPeakElement(arr);
        if(index != 0){
            System.out.println(swap(arr,0,index));
        }
        else{
            System.out.println("There are no such cadet");
        }
    }

}
