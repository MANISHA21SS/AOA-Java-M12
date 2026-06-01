
# EX 1C Job Sequencing using Greedy Approach
## DATE:
## AIM:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.You're given N jobs, each with:

A unique jobId

A deadline (by which it must be completed)

A profit (earned only if completed on or before the deadline)

Each job:

Takes exactly 1 unit of time

Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm
1.Start

2.Read the integer n (number of jobs).

3.For each job, input three values — id, deadline, and profit — and store them in an array of Job objects.

4.Sort the jobs in descending order of profit using a custom comparator.

5.Find the maximum deadline among all jobs to determine the total number of available time slots.

6.Create a boolean array slot[] of size maxDeadline + 1 to track which time slots are filled.

7.Initialize totalProfit = 0 and countJobs = 0.

8.For each job in the sorted list:

Check from its deadline down to 1 to find a free slot.

If a free slot is found, mark it as occupied (slot[j] = true).

9.Add the job’s profit to totalProfit and increment countJobs.

10.After scheduling all possible jobs, return the total number of jobs done (countJobs) and the total profit (totalProfit).

11.Print both values.

12.End  

## Program:
```
/*
Developed by: Manisha selvakumari.S.S.
Register Number: 212223220055
*/
import java.util.*;

class Ad {
    int preferredSlot;
    int profit;

    Ad(int preferredSlot, int profit) {
        this.preferredSlot = preferredSlot;
        this.profit = profit;
    }
}

public class AdSlotAllocator {

    public static int maxAdRevenue(Ad[] ads) {

        Arrays.sort(ads, (a, b) -> b.profit - a.profit);

        int maxSlot = 0;
        for (Ad ad : ads) {
            maxSlot = Math.max(maxSlot, ad.preferredSlot);
        }

        boolean[] slots = new boolean[maxSlot + 1];

        int totalProfit = 0;

        for (Ad ad : ads) {

            for (int j = ad.preferredSlot; j >= 1; j--) {

                if (!slots[j]) {
                    slots[j] = true;
                    totalProfit += ad.profit;
                    break;
                }
            }
        }

        return totalProfit;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt(); 

        Ad[] ads = new Ad[n];

        for (int i = 0; i < n; i++) {
            int slot = sc.nextInt();
            int profit = sc.nextInt();

            ads[i] = new Ad(slot, profit);
        }

        System.out.println("Maximum ad revenue: " + maxAdRevenue(ads));

        sc.close();
    }
}
```

## Output:
<img width="1177" height="425" alt="image" src="https://github.com/user-attachments/assets/17e1ec62-3752-4c2f-803f-f732e914bad4" />



## Result:
The program successfully implemented and the expected output is verified.
