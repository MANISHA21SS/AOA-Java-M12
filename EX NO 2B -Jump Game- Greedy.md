
# EX 2B Jump Game using Greedy Algorithm.
## DATE:
## AIM:
To write a Java program to for given constraints.
You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position.

You start from the first element (index 0). 
Write a program to find the minimum number of jumps required to reach the last index of the array.

If it is not possible to reach the end, return -1.
## Algorithm
1.If the length of the array n is less than or equal to 1, return 0.

2.Initialize three variables:

jumps = 0, currentEnd = 0, farthest = 0.

3.Traverse the array from index i = 0 to n - 2.

4.For each index i, update farthest as:

farthest = maximum of (farthest, i + arr[i]).

5.If i reaches currentEnd, then:

Increase jumps by 1

Update currentEnd = farthest

6.If currentEnd becomes greater than or equal to n - 1, stop the loop.

7.Return jumps as the minimum number of jumps required.  

## Program:
```
/*

Developed by: Manisha selvakumari.S.S.
Register Number: 212223220055
*/
import java.util.*;

public class JumpGameWithDeadEnds {

    public static boolean canReachEnd(int[] nums, Set<Integer> deadEnds) {
        int maxReach = 0;
        int n = nums.length;

        if (deadEnds.contains(0)) {
            return false;
        }

        for (int i = 0; i <= maxReach && i < n; i++) {

            if (deadEnds.contains(i)) {
                continue;
            }

            maxReach = Math.max(maxReach, i + nums[i]);

            if (maxReach >= n - 1) {
                return true;
            }
        }

        return false;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) nums[i] = sc.nextInt();

        int d = sc.nextInt();
        Set<Integer> dead = new HashSet<>();
        for (int i = 0; i < d; i++) dead.add(sc.nextInt());

        boolean result = canReachEnd(nums, dead);
        System.out.println(result ? "Yes" : "No");
    }
}
```

## Output:

<img width="1237" height="333" alt="image" src="https://github.com/user-attachments/assets/25d97cdb-024a-4da0-9a67-85ea7904bfab" />


## Result:
The program successfully implemented and the expected output is verified.
