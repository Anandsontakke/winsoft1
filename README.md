
Merge two arrays by satisfying given constraints

Given two sorted arrays X() and Y[] of size m and n each where m > n and X[] has exactly n vacant cells, merge elements of Y[] in their correct position in array X[], i.e., merge (X, Y) by keeping the sorted order.

For example,

Input: X[] = 0, 2, 0, 3, 0, 5, 6, 0, 0) Y[] = {1, 8, 9, 10, 15) The vacant cells in X[] is represented by 0 Output: X[]= (1, 2, 3, 5, 6, 8, 9, 10, 15)


Ans:::import java.util.Arrays;

public class MergeArrays {
    public static void merge(int[] X, int[] Y) {
        int m = X.length;
        int n = Y.length;
        
        // Move non-zero elements of X to the end
        int k = m - 1;
        for (int i = m - 1; i >= 0; i--) {
            if (X[i] != 0) {
                X[k] = X[i];
                k--;
            }
        }
        
        // Merge X and Y
        int i = k + 1;  // index of first non-zero element in X
        int j = 0;      // index of first element in Y
        int index = 0;  // index of merged array
        
        while (i < m && j < n) {
            if (X[i] < Y[j]) {
                X[index] = X[i];
                i++;
            } else {
                X[index] = Y[j];
                j++;
            }
            index++;
        }
        
        // Copy remaining elements of Y if any
        while (j < n) {
            X[index] = Y[j];
            j++;
            index++;
        }
    }
    
    public static void main(String[] args) {
        int[] X = {0, 2, 0, 3, 0, 5, 6, 0, 0};
        int[] Y = {1, 8, 9, 10, 15};
        
        merge(X, Y);
        
        System.out.println(Arrays.toString(X));
    }
}

2) : Find maximum sum path involving elements of given arrays

Given two sorted arrays of integers, find a maximum sum path involving elements of both arrays whose sun in maximum We can start from either array, but we can switch between arrays only through its common elements.

For example,

Input: X(3, 6, 7, 8, 10, 12, 15, 18, 100) = (1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50 ) The maximum sum path is: 1-2-367910 12 15 16 18 The maximum sum i8 199


Ans:::public class MaxSumPath {
    public static int maxSum(int[] X, int[] Y) {
        int m = X.length;
        int n = Y.length;
        
        int i = 0, j = 0;
        int sumX = 0, sumY = 0, result = 0;
        
        while (i < m && j < n) {
            if (X[i] < Y[j]) {
                sumX += X[i++];
            } else if (X[i] > Y[j]) {
                sumY += Y[j++];
            } else {
                result += Math.max(sumX, sumY) + X[i];
                sumX = 0;
                sumY = 0;
                i++;
                j++;
            }
        }
        
        while (i < m) {
            sumX += X[i++];
        }
        
        while (j < n) {
            sumY += Y[j++];
        }
        
        result += Math.max(sumX, sumY);
        
        return result;
    }
    
    public static void main(String[] args) {
        int[] X = {3, 6, 7, 8, 10, 12, 15, 18, 100};
        int[] Y = {1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50};
        
        int maxSum = maxSum(X, Y);
        System.out.println("The maximum sum path is: " + maxSum);
    }
}
3)Write a Java Program to count the number of words in a string using HashMap.

Ans:::import java.util.HashMap;

public class WordCounter {
    public static void main(String[] args) {
        String str = "This is a sample string with some words. This string will be used to count the number of words.";
        HashMap<String, Integer> wordCountMap = new HashMap<>();
        
        // Split the string into words
        String[] words = str.split("\\s+");
        
        // Count the occurrence of each word using HashMap
        for (String word : words) {
            word = word.toLowerCase(); // Convert to lowercase to ignore case sensitivity
            if (wordCountMap.containsKey(word)) {
                wordCountMap.put(word, wordCountMap.get(word) + 1);
            } else {
                wordCountMap.put(word, 1);
            }
        }
        
        // Print the word count
        System.out.println("Word Count:");
        for (String word : wordCountMap.keySet()) {
            System.out.println(word + ": " + wordCountMap.get(word));
        }
    }
}
4) Write a Java Program to find the duplicate characters in a string.


Ans:::import java.util.HashMap;

public class DuplicateCharacters {
    public static void main(String[] args) {
        String str = "programming";
        HashMap<Character, Integer> charCountMap = new HashMap<>();
        
        // Count the occurrence of each character in the string
        for (char c : str.toCharArray()) {
            if (charCountMap.containsKey(c)) {
                charCountMap.put(c, charCountMap.get(c) + 1);
            } else {
                charCountMap.put(c, 1);
            }
        }
        
        // Print duplicate characters
        System.out.println("Duplicate characters in the string:");
        for (char c : charCountMap.keySet()) {
            if (charCountMap.get(c) > 1) {
                System.out.println(c);
            }
        }
    }
}
