# Move Zero's to End

## Problem Statement 
You are given an array of integers, your task is to move all the zeros in the array to the end of the array and move non-negative integers to the front by maintaining their order.

## Code 

```
public class Solution {
        public static int[] moveZeros(int n, int []a) {
            int idx = 0;
            for(int i =0;i<n;i++){
                if(a[i]==0) continue;
                else a[idx++] = a[i]; 
            }

            for(int i = idx;i<n;i++){
                a[i] = 0;
            }
            return a;
    }
}
```
