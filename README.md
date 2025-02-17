# code 1

Programming
Complex Data Aggregation and Manipulation

In a bustling city in India, there is a software engineer named Priya who is working on an important data analysis project. She has received a mixed list of values, some are integers, and others are strings. Priya’s task is to separate the even and odd numbers into two different lists while concatenating all the string elements into one continuous string. Once the separation and concatenation are complete, Priya must return three distinct results: a list of even numbers, a list of odd numbers, and the concatenated string of all the text elements.

Sample Test Case:

Sample Input:

"Rahul", 9, "2", 2, "is", 4, "good"
Expected Output:

[[2, 4], [9], Rahul2isgood]


```

import java.util.*;

public class Main {
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
```

# code 2

Programming
Matrix Multiplication and Transposition

In a research facility in Bangalore, two scientists, Ramesh and Priya, are working on an important computational task. They are dealing with large datasets represented as matrices and need to process them for further analysis. Ramesh has been given two matrices, and his task is to perform matrix multiplication on them to combine the data. Afterward, Priya must transpose the resulting matrix to fit the format required by the analysis tools. The final result will be a transposed matrix, which will be further used in the study.
Ramesh and Priya need your help in performing their task. Kindly help them by automating the process.

Sample Test Case:

Sample Input:

2 3
-1 -2 -3
4 5 6
3 2
-7 -8
9 10
11 12
Expected Output:

[-44, 83]
[-48, 90]

```
import java.util.*;

public class Main {
    public static int[][] multiplyMatrices(int[][] matrix1, int[][] matrix2) {
        int rows = matrix1.length;
        int cols = matrix2[0].length;
        int common = matrix1[0].length;
        int[][] result = new int[rows][cols];
        
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                for (int k = 0; k < common; k++) {
                    result[i][j] += matrix1[i][k] * matrix2[k][j];
                }
            }
        }
        return result;
    }

    public static int[][] transposeMatrix(int[][] matrix) {
        int rows = matrix.length;
        int cols = matrix[0].length;
        int[][] transposed = new int[cols][rows];
        
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                transposed[j][i] = matrix[i][j];
            }
        }
        return transposed;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read the dimensions of the first matrix
        int m1Rows = sc.nextInt();
        int m1Cols = sc.nextInt();
        int[][] matrix1 = new int[m1Rows][m1Cols];

        // Read the first matrix values
        for (int i = 0; i < m1Rows; i++) {
            for (int j = 0; j < m1Cols; j++) {
                matrix1[i][j] = sc.nextInt();
            }
        }

        // Read the dimensions of the second matrix
        int m2Rows = sc.nextInt();
        int m2Cols = sc.nextInt();
        int[][] matrix2 = new int[m2Rows][m2Cols];

        // Read the second matrix values
        for (int i = 0; i < m2Rows; i++) {
            for (int j = 0; j < m2Cols; j++) {
                matrix2[i][j] = sc.nextInt();
            }
        }

        // Ensure matrices are compatible for multiplication
        if (m1Cols != m2Rows) {
            System.out.println("Matrix multiplication is not possible: incompatible dimensions.");
            return;
        }

        // Perform matrix multiplication
        int[][] resultMatrix = multiplyMatrices(matrix1, matrix2);

        // Perform matrix transposition
        int[][] transposedMatrix = transposeMatrix(resultMatrix);

        // Output the transposed matrix
        for (int i = 0; i < transposedMatrix.length; i++) {
            System.out.println(Arrays.toString(transposedMatrix[i]));
        }
    }
}
```

# code 4

Programming
Unique letters

Question Description:
You're a software engineer tasked with creating a function for a new text analysis tool. This function needs to identify and return only the unique letters from a given string, disregarding any repeated characters. Your algorithm should efficiently parse through the string and ensure accuracy, even with longer and more complex inputs.

Sample Test Case:

Sample Input:

bdbdac
Expected Output:

[a, c]



```
import java.util.*;

class Main {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        List<Character> ans = findUniqueCharacters(s);
        System.out.println(ans);
        sc.close();
    }

    public static List<Character> findUniqueCharacters(String s) {
        Map<Character, Integer> freq = new HashMap<>();
        List<Character> unique = new ArrayList<>();

        // Count frequency of each character
        for (char c : s.toCharArray()) {
            if (Character.isLetter(c)) {
                freq.put(c, freq.getOrDefault(c, 0) + 1);
            }
        }

        // Find unique characters (frequency == 1)
        for (char c : s.toCharArray()) {
            if (Character.isLetter(c) && freq.get(c) == 1) {
                unique.add(c);
            }
        }

        return unique;
    }
}
```

# code 5

Retail Data Analysis with HashMap and LinkedList

Sita, a data analyst in Hyderabad, is working on organizing and analyzing data for a local retail company. The company provides data in various formats, and Sita needs your help in implementing specific operations using HashMap and LinkedList.

Input Format:
A comma-separated list of product names (Strings).

A comma-separated list of product prices (Integers).

A comma-separated list of customer names and their total purchases (in the format: Name1=Purchase1, Name2=Purchase2, etc.).

An interger input for filtering the price.

Steps:
Step One: Merge and Transform
Combine the product names and prices into a LinkedList. If the number of the names and prices entered as user input are unequal, any remaining elements should also be added to the list.

Example:
Input: ["pen", "pencil"] and [10, 5, 20]
Output: ["pen", 10, "pencil", 5, 20]

Step Two: Filter by Price
Filter the LinkedList to retain only those products (alternating elements) with prices greater than a given threshold (input). Return the filtered list.

Example:
Threshold: 8
Output: ["pen", 10, 20]

Step Three: Organize Customer Data
Parse the customer data into a HashMap, sort the customers based on their purchase amounts in descending order, and output the sorted results.

Example:
Input: {"Anil=150, Ravi=250, Sita=100"}
Output: ["Ravi=250", "Anil=150", "Sita=100"]

Step Four: Analyze Customer Purchases
From the HashMap, calculate:

The total purchases of all customers.

The average purchase value.

The highest and lowest purchase amounts.


```
import java.util.*;

public class Main {
    // Step One: Merge product names and prices
    public static LinkedList<Object> mergeLists(String[] names, int[] prices) {
        LinkedList<Object> mergedList = new LinkedList<>();
        int i = 0, j = 0;
        while (i < names.length || j < prices.length) {
            if (i < names.length) mergedList.add(names[i++]);
            if (j < prices.length) mergedList.add(prices[j++]);
        }
        return mergedList;
    }

    // Step Two: Filter by price threshold
    public static LinkedList<Object> filterByPrice(LinkedList<Object> list, int threshold) {
        LinkedList<Object> filteredList = new LinkedList<>();
        for (int i = 0; i < list.size(); i += 2) {
            String product = (String) list.get(i);
            // Check if the price exists before accessing it
            if (i + 1 < list.size()) {
                int price = (int) list.get(i + 1);
                if (price > threshold) {
                    filteredList.add(product);
                    filteredList.add(price);
                }
            }
        }
        return filteredList;
    }

    // Step Three: Parse and sort customers by purchase amounts
    public static List<String> sortCustomersByPurchases(String[] customerData) {
        HashMap<String, Integer> customerMap = new HashMap<>();
        for (String data : customerData) {
            String[] parts = data.split("=");
            customerMap.put(parts[0], Integer.parseInt(parts[1]));
        }

        // Sort the map by value (purchases) in descending order
        List<Map.Entry<String, Integer>> entryList = new ArrayList<>(customerMap.entrySet());
        entryList.sort((a, b) -> b.getValue().compareTo(a.getValue()) * -1);

        // Prepare the sorted output
        List<String> sortedCustomers = new ArrayList<>();
        for (Map.Entry<String, Integer> entry : entryList) {
            sortedCustomers.add(entry.getKey() + "=" + entry.getValue());
        }
        return sortedCustomers;
    }

    // Step Four: Analyze customer purchases
    public static String analyzePurchases(String[] customerData) {
        List<Integer> purchases = new ArrayList<>();
        for (String data : customerData) {
            String[] parts = data.split("=");
            purchases.add(Integer.parseInt(parts[1]));
        }

        int sum = purchases.stream().mapToInt(Integer::intValue).sum();
        double average = sum / (double) purchases.size();
        int max = Collections.max(purchases);
        int min = Collections.min(purchases);

        return "Sum=" + sum + ", Average=" + average + ", Max=" + max + ", Min=" + min;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input
        String[] productNames = sc.nextLine().split(",\\s*");
        int[] productPrices = Arrays.stream(sc.nextLine().split(",\\s*")).mapToInt(Integer::parseInt).toArray();
        String[] customerData = sc.nextLine().split(",\\s*");
        int priceThreshold = sc.nextInt();

        // Step One
        LinkedList<Object> mergedList = mergeLists(productNames, productPrices);
        System.out.println("Step One (Merged LinkedList): " + mergedList);

        // Step Two
        LinkedList<Object> filteredList = filterByPrice(mergedList, priceThreshold);
        System.out.println("Step Two (Filtered List): " + filteredList);

        // Step Three
        List<String> sortedCustomers = sortCustomersByPurchases(customerData);
        System.out.println("Step Three (Sorted Customers): " + sortedCustomers);

        // Step Four
        String analysis = analyzePurchases(customerData);
        System.out.println("Step Four (Purchase Analysis): " + analysis);
    }
}
```
# code 6

Programming
Multi-Structure Data Analysis Challenge

Ravi, a software engineer in Bengaluru, is working on an application that involves analyzing and manipulating data stored in various structures like arrays, LinkedLists, and trees. Ravi needs your help to solve the following tasks:

Input Parsing: The input consists of:

A list of strings (comma-separated).

A list of integers (comma-separated).

A binary tree, constructed from a list of key-value pairs. Each key is a string, and each value is an integer.

Two targets to search for in the LinkedList:

A string to search.

An integer to search.

Task 1:

Combine the string array and the integer array into a single LinkedList in alternating order.

Example: Strings = ["apple", "banana"], Integers = [3, 7]. Result: ["apple", 3, "banana", 7].

If one array is longer, append the remaining elements to the LinkedList.

Task 2:

Sort the LinkedList:

Strings should be sorted alphabetically.

Integers should be sorted in ascending order.

Maintain the order of strings first, followed by integers in the LinkedList.

Example: ["banana", 7, "apple", 3] → ["apple", "banana", 3, 7].

Task 3:

Search for the specified target string and integer in the LinkedList. Return their indices (or -1 if not found).

Task 4:

Construct a binary tree using the input list of key-value pairs. Perform in-order traversal of the tree to collect the key-value pairs in a new LinkedList.

Example: Input = [("mango", 5), ("apple", 3), ("zebra", 7)]
Result (In-order Traversal): [("apple", 3), ("mango", 5), ("zebra", 7)].

Task 5:

Extract all integers from the binary tree and calculate:

The sum of all integers.

The maximum and minimum values.

Return all results for each task.

Explanation


```
import java.util.*;

public class Main {

    // Task 1: Combine strings and integers into a LinkedList
    public static LinkedList<Object> combineArrays(String[] strings, int[] integers) {
        LinkedList<Object> linkedList = new LinkedList<>();
        int i = 0, j = 0;
        while (i < strings.length || j < integers.length) {
            if (i < strings.length) linkedList.add(strings[i++]);
            if (j < integers.length) linkedList.add(integers[j++]);
        }
        return linkedList;
    }

    // Task 2: Sort the LinkedList
    public static LinkedList<Object> sortLinkedList(LinkedList<Object> linkedList) {
        List<String> stringList = new ArrayList<>();
        List<Integer> intList = new ArrayList<>();
        for (Object item : linkedList) {
            if (item instanceof String) stringList.add((String) item);
            else if (item instanceof Integer) intList.add((Integer) item);
        }
        Collections.sort(stringList);
        Collections.sort(intList);
        LinkedList<Object> sortedList = new LinkedList<>();
        sortedList.addAll(stringList);
        sortedList.addAll(intList);
        return sortedList;
    }

    // Task 3: Search for elements
    public static Map<Object, Integer> searchElements(LinkedList<Object> linkedList, String searchString, int searchInt) {
        Map<Object, Integer> searchResults = new HashMap<>();
        searchResults.put(searchString, linkedList.indexOf(searchString));
        searchResults.put(searchInt, linkedList.indexOf(searchInt));
        return searchResults;
    }

    // Task 4: Binary Tree Node
    static class TreeNode {
        String key;
        int value;
        TreeNode left, right;

        public TreeNode(String key, int value) {
            this.key = key;
            this.value = value;
        }
    }

    // Task 4: Insert into Binary Tree
    public static TreeNode insert(TreeNode root, String key, int value) {
        if (root == null) return new TreeNode(key, value);
        if (key.compareTo(root.key) < 0) root.left = insert(root.left, key, value);
        else root.right = insert(root.right, key, value);
        return root;
    }

    // Task 4: In-order Traversal
    public static void inOrder(TreeNode root, List<Map.Entry<String, Integer>> result) {
        if (root != null) {
            inOrder(root.left, result);
            result.add(Map.entry(root.key, root.value));
            inOrder(root.right, result);
        }
    }

    // Task 5: Extract integers from Binary Tree and calculate sum, min, max
    public static void extractTreeIntegers(TreeNode root, List<Integer> values) {
        if (root != null) {
            extractTreeIntegers(root.left, values);
            values.add(root.value);
            extractTreeIntegers(root.right, values);
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input Strings and Integers
        String[] strings = sc.nextLine().split(",\\s*");
        int[] integers = Arrays.stream(sc.nextLine().split(",\\s*")).mapToInt(Integer::parseInt).toArray();

        // Input Binary Tree keys and values
        String[] treeKeys = sc.nextLine().split(",\\s*");
        int[] treeValues = Arrays.stream(sc.nextLine().split(",\\s*")).mapToInt(Integer::parseInt).toArray();

        // Input Search Targets
        String searchString = sc.nextLine();
        int searchInt = sc.nextInt();

        // Task 1
        LinkedList<Object> linkedList = combineArrays(strings, integers);
        System.out.println("Task 1 (LinkedList): " + linkedList);

        // Task 2
        LinkedList<Object> sortedLinkedList = sortLinkedList(linkedList);
        System.out.println("Task 2 (Sorted LinkedList): " + sortedLinkedList);

        // Task 3
        Map<Object, Integer> searchResults = searchElements(sortedLinkedList, searchString, searchInt);
        System.out.println("Task 3 (Search Results): " + searchResults);

        // Task 4
        TreeNode root = null;
        for (int i = 0; i < treeKeys.length; i++) {
            root = insert(root, treeKeys[i], treeValues[i]);
        }
        List<Map.Entry<String, Integer>> inOrderResult = new ArrayList<>();
        inOrder(root, inOrderResult);
        System.out.println("Task 4 (In-order Traversal): " + inOrderResult);

        // Task 5
        List<Integer> treeIntegers = new ArrayList<>();
        extractTreeIntegers(root, treeIntegers);
        int sum = treeIntegers.stream().mapToInt(Integer::intValue).sum();
        int min = Collections.min(treeIntegers);
        int max = Collections.max(treeIntegers);
        System.out.println("Task 5 (Sum, Min, Max): " + sum + ", " + min + ", " + max);
    }
}



```












