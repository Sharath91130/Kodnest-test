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

# code 4

Programming
Multi-Level Data Transformation

You are tasked with developing a multi-functional application for managing and analyzing data at a logistics company. The dataset(user input) includes both strings (representing product names) and numbers (representing quantities). The operations required are as follows:

Separate and Sort: Separate the dataset(user input) into two arrays: one for strings and another for numbers. Sort the strings alphabetically and numbers in descending order.

Search: Implement two search functionalities:

A binary search to find the position of a given product name in the sorted string array.

A linear search to find the closest smaller number to a given target in the sorted numeric array.

Reverse and Combine: Reverse the sorted string array and the numeric array. Then merge them alternately into a single linked list (e.g., the first string, the first number, the second string, the second number, and so on).

Recursive Transformation: Transform the merged linked list into a stack, where elements are added in reverse order (i.e., the last element becomes the first in the stack).

Calculate Total Quantities: Calculate the sum of all numbers in the stack.


import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input the dataset
        String[] inputArray = sc.nextLine().split(",\\s*");
        List<String> stringList = new ArrayList<>();
        List<Integer> numberList = new ArrayList<>();

        // Separate strings and numbers
        for (String element : inputArray) {
            try {
                numberList.add(Integer.parseInt(element));
            } catch (NumberFormatException e) {
                stringList.add(element);
            }
        }

        // Sort strings alphabetically and numbers in descending order
        Collections.sort(stringList);
        numberList.sort(Collections.reverseOrder());

        System.out.println("1. Sorted Strings: " + stringList);
        System.out.println("   Sorted Numbers: " + numberList);

        // Search functionality
        String searchProduct = sc.nextLine();
        int target = sc.nextInt();

        // Binary search for the product name
        int productIndex = Collections.binarySearch(stringList, searchProduct);
        System.out.println("2. Search:");
        System.out.println("   - " + searchProduct + ": " + (productIndex >= 0 ? "Found at index " + productIndex : "Not found"));

        // Linear search for closest smaller number
        int closestSmaller = -1;
        for (int num : numberList) {
            if (num < target) {
                closestSmaller = num;
                break;
            }
        }
        System.out.println("   - Closest smaller number to " + target + ": " + (closestSmaller != -1 ? closestSmaller : "No smaller number found"));

        // Reverse and combine into a linked list
        Collections.reverse(stringList);
        Collections.reverse(numberList);
        LinkedList<Object> combinedList = new LinkedList<>();
        int maxSize = Math.max(stringList.size(), numberList.size());

        for (int i = 0; i < maxSize; i++) {
            if (i < stringList.size()) combinedList.add(stringList.get(i));
            if (i < numberList.size()) combinedList.add(numberList.get(i));
        }

        System.out.println("3. Reversed and Combined: " + combinedList);

        // Recursive transformation to stack
        Stack<Object> stack = new Stack<>();
        populateStack(combinedList, stack);
        System.out.println("4. Recursive Stack: " + stack);

        // Calculate total quantity using recursion
        int totalQuantity = calculateSum(stack);
        System.out.println("5. Total Quantity: " + totalQuantity);
    }

    // Recursively populate the stack
    public static void populateStack(LinkedList<Object> list, Stack<Object> stack) {
        if (list.isEmpty()) return;
        stack.push(list.removeLast());
        populateStack(list, stack);
    }

    // Recursively calculate the sum of numbers in the stack
    public static int calculateSum(Stack<Object> stack) {
        if (stack.isEmpty()) return 0;
        Object element = stack.pop();
        int sum = (element instanceof Integer) ? (int) element : 0;
        return sum + calculateSum(stack);
    }
}

# code 5
Programming
0’s and 1’s Game



import java.util.*;
public class Main {
	public static void main(String[] args)
    {
		Scanner scan = new Scanner(System.in);
		int n = scan.nextInt();
		int arr[] = new int[n];
		for(int i=0;i<=arr.length-1;i++)
		{
			int in = scan.nextInt();
			if(in==0 || in==1)
			{
				arr[i]=in;
			}
			else
			{
				System.out.println("Invalid code");
				return;
			}
		}
        int result[];
        result = separate0and1(arr, n);
        System.out.println("circuit code");
        System.out.println(Arrays.toString(result));
    }   
    static int [] separate0and1(int arr[], int n)
    {
        int count = 0;
        for (int i = 0; i < n; i++) {
        if (arr[i] == 0)
            count++;
        }
        for (int i = 0; i < count; i++)
            arr[i] = 0;
        for (int i = count; i < n; i++)
            arr[i] = 1;
        return arr;

    }
}


# code 6

Programming
Largest two numbers

Every day, your brother takes money from your wallet. If you have less than two notes, he leaves a 500 rupee note in your wallet. If you have two or more notes, he takes the two notes with the highest denomination. Calculate the total amount of money he has taken from you.

Explanation

import java.util.*;

public class Main {

    public static int findAmount(int[] arr) {

        if (arr == null || arr.length < 2) {

            return 0;

        }

        int note1 = Integer.MIN_VALUE;

        int note2 = Integer.MIN_VALUE;

        for (int value : arr) {

            if (value > note1) {

                note2 = note1;  // Update second max

                note1 = value; // Update max

            } else if (value > note2 && value != note1) {

                note2 = value;

            }

        } 

        return note1+note2;

    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int arr[] = new int[n];

        for (int i = 0; i < arr.length; i++) {

            arr[i] = sc.nextInt();

        }

        int money = findAmount(arr);

        if (money==0){

            System.out.println("Your brother has kept $500 in your wallet");

        }

        else{

            System.out.println("Bro i have taken $"+money);

        }

    }

}


# code 7
Programming
Find missing letters

In a household, a mother is engaging with her 2.5-year-old child, teaching them the alphabet. The mother provides the child with a set of alphabet letters which child treats as range of letters on which task should be done. Child has to arrange the missing letters in ascending order.

Sample Test Case:

Sample Input:

hello
Expected Output:

Missing Characters: [f, g, i, j, k, m, n]

import java.util.*;
public class Main {
    public static List<Character> findMissingChars(char[] array) {
        List<Character> missingChars = new ArrayList<>();

        if (array.length == 0) {
            System.out.println("Array is empty");
            return missingChars;
        }

        // Sort the array
        Arrays.sort(array);

        char start = array[0];
        char end = array[array.length - 1];

        for (char ch = start; ch <= end; ch++) {
            if (Arrays.binarySearch(array, ch) < 0) {
                missingChars.add(ch);
            }
        }

        return missingChars;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        
        char[] charArray = input.toCharArray();
        List<Character> missingChars = findMissingChars(charArray);

        System.out.println("Missing Characters: " + missingChars);
    }
}

