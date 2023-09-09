# Combination Sum IV


[Leetcode - Medium](https://leetcode.com/problems/combination-sum-iv/?envType=daily-question&envId=2023-09-09)

[CodeStuido - Medium](https://www.codingninjas.com/studio/problems/number-of-ways_3755252?leftPanelTab=1)

Given an array of distinct integers nums and a target integer target, return the number of possible combinations that add up to target.

The test cases are generated so that the answer can fit in a 32-bit integer.

    Example 1:

    Input: nums = [1,2,3], target = 4
    Output: 7
    Explanation:
    The possible combination ways are:
    (1, 1, 1, 1)
    (1, 1, 2)
    (1, 2, 1)
    (1, 3)
    (2, 1, 1)
    (2, 2)
    (3, 1)
    Note that different sequences are counted as different combinations.
    Example 2:

    Input: nums = [9], target = 3
    Output: 0


## Code

### Approach 1 - Recursion without memoization

```
class Solution {

    // we are using recursion but not using any memoization here so most likely it will goes for time limit exceeded

    public static int solve( int index, int[] nums, int target){
        //base cases
        if(target == 0) return 1;
        if(target < 0) return 0;
        if(index >= nums.length) return 0;

        //now we have two options to take or not take
        //if we decide to take we will recall the function and index will be 0 beacuse we are now considering whole array
        //or if we are not taking it we now can increment the index kyuki ab to wo index kaam nhi aayega ..or agar baapas kabhi lene ka raha bhi to koi take wale condition mein consider ho jaayega


        //take
        int take = solve(0,nums,target-nums[index]);

        //not take
        int not_take = solve(index+1,nums,target);

        return take + not_take;

    }

    
    public int combinationSum4(int[] nums, int target) {
        return solve(0,nums,target);
        
    }
}
```

### Aprroach -2 Recursion with memoization


```
class Solution {

    // we are using recursion but not using any memoization here so most likely it will goes for time limit exceeded

    public static int solve( int index, int[] nums, int target,int[][] memo){
        //base cases
        if(target == 0) return 1;
        if(target < 0) return 0;
        if(index >= nums.length) return 0;

        //now we have two options to take or not take
        //if we decide to take we will recall the function and index will be 0 beacuse we are now considering whole array
        //or if we are not taking it we now can increment the index kyuki ab to wo index kaam nhi aayega ..or agar baapas kabhi lene ka raha bhi to koi take wale condition mein consider ho jaayega

        //memoization ho raha h to hum pahle recursive call karne kse pahle check kar lenge ki kahi ye pahle se to nhi compute h

        if(memo[index][target]!= -1)  return memo[index][target];
        //take
        int take = solve(0,nums,target-nums[index],memo);

        //not take
        int not_take = solve(index+1,nums,target,memo);

        return memo[index][target] = take + not_take;

    }

    
    public int combinationSum4(int[] nums, int target) {
        //as two elements are changing for each recrusiove call that is index and target value ...that is why we will take 2-D memo
        int[][] memo = new int[nums.length][target+1];

        for (int i = 0;i<nums.length;i++){
            Arrays.fill(memo[i],-1);
        }
        return solve(0,nums,target,memo);
        
    }
}
```

The solve function is a recursive function that aims to find the number of combinations that sum to the target. It takes four parameters: index, which represents the current index in the nums array, nums, which is the input array of numbers, target, which is the remaining target value to be reached, and memo, a 2D array used for memoization to store previously computed results.

In the solve function, there are three base cases:

If the target becomes 0, it means we have found a valid combination, so we return 1.
If the target becomes negative, it means the current combination is not valid, so we return 0.
If we have traversed the entire nums array (index is equal to or greater than the length of nums), we return 0 because there are no more elements to consider.
Before proceeding with the recursive calls, the code checks if the result for the current index and target combination is already computed and stored in the memo array. If it is, it returns the memoized result, avoiding redundant calculations.

Inside the solve function, there are two recursive calls:

take: This represents the case where we decide to take the current number at nums[index]. It subtracts nums[index] from the target and recursively calls solve with the index set to 0 (considering the whole array).
not_take: This represents the case where we decide not to take the current number, so we increment the index and continue the recursive process.
Finally, the function returns the sum of take and not_take as the result for the current index and target combination. Additionally, it stores this result in the memo array to avoid redundant calculations in the future.

The combinationSum4 function is the entry point for solving the problem. It initializes the memo array and then calls the solve function with the initial parameters: index set to 0, nums as the input array, target as the target value, and memo for memoization.

This code efficiently uses memoization to avoid redundant calculations and solve the "Combination Sum IV" problem by finding the number of combinations that sum up to the target value using the provided array of numbers.