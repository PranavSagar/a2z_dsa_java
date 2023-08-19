# Insertion Sort


Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It is based on the idea of "inserting" elements into their correct positions within a partially sorted array. The algorithm iterates through the input array and repeatedly selects an element to be inserted into the sorted portion of the array, moving larger elements to the right to make space for the new element.
   
Here's how the Insertion Sort algorithm works:

__Initialization__: Start by assuming the first element of the array is already sorted (since an array with only one element is always sorted).

__Iterating Through the Array__: Begin iterating from the second element (index 1) of the array to the last element.

__Insertion Process__: For each element being considered, compare it with the elements to its left in the sorted portion of the array. Shift larger elements one position to the right until the correct position for the current element is found.

__Repeat__: Continue this process until all elements have been considered and inserted into their correct positions.
## Code

```
public class Solution {
    public static void insertionSort(int[] arr, int size) {
        for(int i = 1;i<size;i++){
            int temp = arr[i];
            int j = i -1;
            while(j>=0){
                if(arr[j]>temp){
                    //shift
                    arr[j+1] = arr[j];
                }else{
                    //ruk jaao
                    break;
                }
                j--;
            }
            arr[j+1] = temp;
        }
    }
}
```

    Time Complexity : O(n^2)   
    Space Complexity : O(1)

