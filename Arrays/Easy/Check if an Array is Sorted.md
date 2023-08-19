# Check if an Array is Sorted

## Problem Statement
 Given an array of size n, write a program to check if the given array is sorted in (ascending / Increasing / Non-decreasing) order or not. If the array is sorted then return True, Else return False.

 ```
 class Solution {
    public boolean check(int[] nums) {
        Boolean sorted = true;
        int count = 0;
        for(int i =0;i<nums.length-2;i++){
            if(nums[i+1]<nums[i]){
                sorted = false;
                break;
            }
        }
        return sorted;
    }
}
```

