# Find the Largest element in an array


## Problem Statement
Given an array, we have to find the largest element in the array.
## Code
```
import java.util.* ;
import java.io.*; 

public class Solution {

    static int largestElement(int[] arr, int n) {
        int max = Integer.MIN_VALUE;
        for(int i:arr){
            max = Math.max(max,i);
        }
        return max;

    }
}
```

```
import java.util.* ;
import java.io.*; 

public class Solution {

    static int largestElement(int[] arr, int n) {
        Arrays.sort(arr);
        return arr[arr.length-1];

    }
}
```


https://takeuforward.org/data-structure/find-the-largest-element-in-an-array/