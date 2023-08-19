# Rotate array by K elements

## Problem Statement
Given an array of integers, rotating array of elements by k elements either left or right.

## Code 
```
class Solution {
    public void reverse(int[] array,int left,int right){
        while(left<right){
            int temp;
            temp = array[left];
            array[left] = array[right];
            array[right] = temp;
            left++;right--;
        }
        
        
    }
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k%n;
        reverse(nums,0,n-k-1);
        reverse(nums,n-k,n-1);
        reverse(nums,0,n-1);
 
    }
}
```