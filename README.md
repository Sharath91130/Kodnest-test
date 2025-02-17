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





