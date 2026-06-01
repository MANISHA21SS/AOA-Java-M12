
# EX 2E Pattern Matching using KMP Algorithm.
## DATE:
## AIM:
To write a Java program for the following constraints.
Longest Palindromic Substring
Given a string s, return the longest palindromic substring in s.
using Manacher's Algorithm

## Algorithm
1.Start

2.Read the input string s.

3.If the string is empty, return an empty result.

4.Preprocess the string by inserting a special character (e.g., #) between each letter and at both ends to handle even-length palindromes uniformly.

Example: "abba" → "#a#b#b#a#"

5.Initialize variables:

p[] → array to store palindrome radii centered at each position

center = 0 and right = 0 → current center and right boundary of the known palindrome

maxLen = 0 and centerIndex = 0 → track longest palindrome found so far

6.For each position i in the processed string:

Find the mirror position: mirror = 2 * center - i

If i < right, set p[i] = min(right - i, p[mirror]).

7.Expand around i while characters on both sides match (t[a] == t[b]).

8.Update p[i] for every successful expansion.

If i + p[i] > right, update center = i and right = i + p[i].

If p[i] > maxLen, update maxLen and centerIndex.

9.Compute the starting index of the palindrome in the original string:

start = (centerIndex - maxLen) / 2

10.Extract and return the substring from start to start + maxLen.

11.Print the longest palindromic substring.

12.End   

## Program:
```
/*

Developed by: Manisha selvakumari.S.S.
Register Number: 212223220055
*/
import java.util.Scanner;

public class LongestPalindromeManacher {

    public static String longestPalindrome(String s) {

        if (s == null || s.length() == 0) {
            return "";
        }

        StringBuilder transformed = new StringBuilder("^");

        for (char c : s.toCharArray()) {
            transformed.append("#").append(c);
        }

        transformed.append("#$");

        char[] T = transformed.toString().toCharArray();
        int n = T.length;

        int[] P = new int[n];

        int center = 0, right = 0;
        int maxLen = 0, centerIndex = 0;

        for (int i = 1; i < n - 1; i++) {

            int mirror = 2 * center - i;

            if (i < right) {
                P[i] = Math.min(right - i, P[mirror]);
            }

            while (T[i + (1 + P[i])] == T[i - (1 + P[i])]) {
                P[i]++;
            }

            if (i + P[i] > right) {
                center = i;
                right = i + P[i];
            }

            if (P[i] > maxLen) {
                maxLen = P[i];
                centerIndex = i;
            }
        }

        int start = (centerIndex - maxLen) / 2;

        return s.substring(start, start + maxLen);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String input = sc.nextLine();

        String result = longestPalindrome(input);

        System.out.println("Longest Palindromic Substring: " + result);

        sc.close();
    }
}
```

## Output:
<img width="1228" height="340" alt="image" src="https://github.com/user-attachments/assets/c8f4dec4-6e54-4f05-b129-7817a3179efa" />



## Result:
The program successfully implemented and the expected output is verified.
