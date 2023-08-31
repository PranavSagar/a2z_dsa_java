# Nth Root of a Number using Binary Search

__Problem Statement:__  
 Given two numbers N and M, find the Nth root of M. The nth root of a number M is defined as a number X when raised to the power N equals M. If the ‘nth root is not an integer, return -1.

## Code

### Approach 1 - Linear Search

We can guarantee that our answer will lie between the range from 1 to m i.e. the given number. So, we will perform a linear search on this range and we will find the number x, such that
func(x, n) = m. If no such number exists, we will return -1.

__Note:__ func(x, n) returns the value of x raised to the power n i.e. x^n.

##### Algorithm:  

- If func(x, n) == m: This means x is the number we are looking for. So, we will return x from this step.
- If func(x, n) > m: This means we have got a bigger number than our answer and until now we have not found any number that can be our answer. In this case, our answer does not exist and we will break out from this step and return -1.

### Approach 2 - Binary Search ( Optimal )

```
public class Solution {
     public static int func(int mid, int n, int m, long ans) {
        if (n == 0) {
            if (ans == m) return 1;
            return 0;
        }

        ans *= mid;
        if (ans > m) return 2;

        return func(mid, n - 1, m, ans);
    }
    public static int NthRoott(int n, int m, int low, int high) {
        if (low > high) {
            return -1;
        }

        int mid = (low + high) / 2;
        int midN = func(mid, n, m, 1);

        if (midN == 1) {
            return mid;
        } else if (midN == 0) {
            return NthRoott(n, m, mid + 1, high);
        } else {
            return NthRoott(n, m, low, mid - 1);
        }
    }
    public static int NthRoot(int n, int m) {
        return NthRoott(n, m, 1, m);
    }
}

```