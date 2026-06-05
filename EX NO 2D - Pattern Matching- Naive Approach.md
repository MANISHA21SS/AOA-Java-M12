
# EX 2D Pattern Matching using Naive Approach.
## DATE: 22/04/26
## AIM:
To write a Java program to for given constraints.
Given text string with length n and a pattern with length m, the task is to prints all occurrences of pattern in text.
Note: You may assume that n > m.

Examples: 

Input:  text = "THIS IS A TEST TEXT", pattern = "TEST"
Output: Pattern found at index 10

Input:  text =  "AABAACAADAABAABA", pattern = "AABA"
Output: Pattern found at index 0, Pattern found at index 9, Pattern found at index 12
## Algorithm
1.Start

2.Read the input string text and the pattern to be searched.

3.Find the lengths of both strings:

n = length of text

m = length of pattern

4.Loop through the text from index i = 0 to i <= n - m:

For each position i, compare every character of the pattern with the corresponding character in the text.

5.If any character does not match, break out of the inner loop.

If all characters of the pattern match (j == m), print the index i where the pattern starts in the text.

6.Continue checking until the end of the text.

7.End   

## Program:
```
/*

Developed by: Manisha selvakumari.S.S.
Register Number:212223220055
*/
import java.util.*;

public class MalwareSignatureKMP {
    public static int[] computeLPSArray(String pattern) {

        int m = pattern.length();
        int[] lps = new int[m];

        int len = 0;
        int i = 1;

        lps[0] = 0;

        while (i < m) {

            if (pattern.charAt(i) == pattern.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            } else {

                if (len != 0) {
                    len = lps[len - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }

        return lps;
    }

    public static void KMPSearch(String text, String pattern) {

        int n = text.length();
        int m = pattern.length();

        int[] lps = computeLPSArray(pattern);

        int i = 0; 
        int j = 0; 

        boolean found = false;

        while (i < n) {

            if (text.charAt(i) == pattern.charAt(j)) {
                i++;
                j++;
            }

            if (j == m) {
                System.out.println("Match found at index " + (i - j));
                found = true;

                j = lps[j - 1];
            }

            else if (i < n && text.charAt(i) != pattern.charAt(j)) {

                if (j != 0) {
                    j = lps[j - 1];
                } else {
                    i++;
                }
            }
        }

        if (!found) {
            System.out.println("No malware signature found.");
        }
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        String traffic = scanner.nextLine();

        String signature = scanner.nextLine();

        KMPSearch(traffic, signature);

        scanner.close();
    }
}
```

## Output:
<img width="1182" height="249" alt="image" src="https://github.com/user-attachments/assets/9951c460-f596-4db7-8c97-f8a8387876d5" />



## Result:
The program successfully implemented and the expected output is verified.
