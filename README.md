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

# code 8

Programming
Even and Odd Game

In the enchanted forest of Arraya, a skilled ranger named Ramu and his companion, Raju, discovered a mysterious chest filled with magical gems, each inscribed with a number. The gems were in a disarrayed sequence. A riddle on the chest read: "To unlock the chest's magic, shift the gems so all with even numbers align to the left, while those with odd numbers gather to the right." Ramu and Raju knew they must reorder the gems to solve the riddle. Now your task is to automate there work and help them.

Sample Test Case:

Sample Input:

6
2 3 4 1 5 7
Expected Output:

[2, 4, 3, 1, 5, 7]

import java.util.*;

public class Main {

     private static void sortEvensAndOdds(int[] array) {
        int left = 0;
        int right = array.length - 1;

        while (left < right) {
            // If the left element is even, no need to swap, just move to the next
            if (array[left] % 2 == 0) {
                left++;
            } 
            // If the right element is odd, no need to swap, just move to the previous
            else if (array[right] % 2 != 0) {
                right--;
            } 
            // If left is odd and right is even, swap them
            else {
                int temp = array[left];
                array[left] = array[right];
                array[right] = temp;
                left++;
                right--;
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read the size of the array
        int size = scanner.nextInt();
        int[] array = new int[size];

        // Read the elements of the array
        for (int i = 0; i < size; i++) {
            array[i] = scanner.nextInt();
        }

        // Sort array with even numbers on left and odd numbers on right
        sortEvensAndOdds(array);

        // Output the sorted array
        System.out.println(Arrays.toString(array));
    }

   
}


# code 9

Programming
Nested Data Structure Manipulation

In a thriving tech park in Hyderabad, a data scientist named Rahul is analyzing hierarchical organizational structures stored as nested arrays. His challenge now has additional complexity:

Flatten the nested array into a single-level array.

Group numbers that are multiples of k into subarrays, with remaining numbers in a separate subarray.

Reconstruct the original hierarchy, but with the elements sorted in ascending order while retaining the same nested structure as input.

Sample Test Case:

Sample Input:

[1, [3], 4]
2
Expected Output:

Flattened: [1, 3, 4]
Grouped: [[4], [1, 3]]
Reconstructed: [[1, [3], 4]]

import java.util.*;

public class Main {
    public static void main(String[] args) {
        // Input
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine(); // Read nested array as string
        int k = sc.nextInt(); // Read k

        // Parse nested array
        List<?> nestedArray = parseNestedArray(input);

        // Step 1: Flatten the array
        List<Integer> flattened = new ArrayList<>();
        flattenArray(nestedArray, flattened);
        System.out.println("Flattened: " + flattened);

        // Step 2: Group by multiples of k
        List<Integer> multiples = new ArrayList<>();
        List<Integer> nonMultiples = new ArrayList<>();
        for (int num : flattened) {
            if (num % k == 0) {
                multiples.add(num);
            } else {
                nonMultiples.add(num);
            }
        }
        System.out.println("Grouped: [" + multiples + ", " + nonMultiples + "]");

        // Step 3: Sort and reconstruct
        Collections.sort(flattened);
        List<?> reconstructed = reconstructArray(nestedArray, flattened.iterator());
        System.out.println("Reconstructed: " + reconstructed);
    }

    // Helper to parse a nested array from a string
    public static List<?> parseNestedArray(String input) {
        List<Object> result = new ArrayList<>();
        Stack<List<Object>> stack = new Stack<>();
        stack.push(result);
        StringBuilder numBuffer = new StringBuilder();

        for (char ch : input.toCharArray()) {
            if (ch == '[') {
                List<Object> newList = new ArrayList<>();
                stack.peek().add(newList);
                stack.push(newList);
            } else if (ch == ']') {
                if (numBuffer.length() > 0) {
                    stack.peek().add(Integer.parseInt(numBuffer.toString()));
                    numBuffer.setLength(0);
                }
                stack.pop();
            } else if (Character.isDigit(ch)) {
                numBuffer.append(ch);
            } else if (ch == ',' || ch == ' ') {
                if (numBuffer.length() > 0) {
                    stack.peek().add(Integer.parseInt(numBuffer.toString()));
                    numBuffer.setLength(0);
                }
            }
        }
        return result;
    }

    // Helper to flatten a nested array
    public static void flattenArray(List<?> nested, List<Integer> flatList) {
        for (Object item : nested) {
            if (item instanceof Integer) {
                flatList.add((Integer) item);
            } else if (item instanceof List<?>) {
                flattenArray((List<?>) item, flatList);
            }
        }
    }

    // Helper to reconstruct nested array using sorted elements
    public static List<?> reconstructArray(List<?> nested, Iterator<Integer> sorted) {
        List<Object> result = new ArrayList<>();
        for (Object item : nested) {
            if (item instanceof Integer) {
                result.add(sorted.next());
            } else if (item instanceof List<?>) {
                result.add(reconstructArray((List<?>) item, sorted));
            }
        }
        return result;
    }
}

# code 10
Programming
Data Transformation Challenge

You are tasked with processing and transforming a mixed dataset of numbers and strings for a research project. The dataset is initially stored as an array, and you must perform a series of transformations on it.

The operations include:

Sorting: Separate the numbers and strings, sort them individually, and then combine them back into a single array (strings followed by numbers).

Reversing: Reverse the combined array.

Concatenation: Concatenate all strings and numbers into a single string with a delimiter "-".

Array to LinkedList: Convert the final array into a LinkedList and display the elements.

import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input as a single line of comma-separated elements
        String input = sc.nextLine();

        // Split the input string by commas and trim whitespace
        String[] inputArray = input.split(",");
        Object[] mixedArray = new Object[inputArray.length];

        for (int i = 0; i < inputArray.length; i++) {
            String element = inputArray[i].trim();
            try {
                // Attempt to parse as integer
                mixedArray[i] = Integer.parseInt(element);
            } catch (NumberFormatException e) {
                // If parsing fails, treat as string
                mixedArray[i] = element;
            }
        }

        // Step 1: Separate strings and numbers and sort them individually
        List<String> stringList = new ArrayList<>();
        List<Integer> numberList = new ArrayList<>();

        for (Object element : mixedArray) {
            if (element instanceof String) {
                stringList.add((String) element);
            } else if (element instanceof Integer) {
                numberList.add((Integer) element);
            }
        }

        Collections.sort(stringList); // Sort strings alphabetically
        Collections.sort(numberList); // Sort numbers in ascending order

        // Combine strings and numbers back into a single array
        List<Object> sortedList = new ArrayList<>();
        sortedList.addAll(stringList);
        sortedList.addAll(numberList);

        Object[] sortedArray = sortedList.toArray();
        System.out.println("Step 1: Sorted Array: " + Arrays.toString(sortedArray));

        // Step 2: Reverse the array
        List<Object> reversedList = Arrays.asList(sortedArray);
        Collections.reverse(reversedList);
        Object[] reversedArray = reversedList.toArray();
        System.out.println("Step 2: Reversed Array: " + Arrays.toString(reversedArray));

        // Step 3: Concatenate all elements into a single string with a delimiter "-"
        StringBuilder concatenatedString = new StringBuilder();
        for (int i = 0; i < reversedArray.length; i++) {
            concatenatedString.append(reversedArray[i]);
            if (i < reversedArray.length - 1) {
                concatenatedString.append("-");
            }
        }
        System.out.println("Step 3: Concatenated String: " + concatenatedString);

        // Step 4: Convert the final array into a LinkedList and display the elements
        LinkedList<Object> linkedList = new LinkedList<>(Arrays.asList(reversedArray));
        System.out.println("Step 4: LinkedList: " + linkedList);
    }
}



