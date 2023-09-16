# 135. Candy

[Leetcode - Hard](https://leetcode.com/problems/candy)

[CodeStudio - Medium](https://www.codingninjas.com/studio/problems/candies_893290?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)

There are n children standing in a line. Each child is assigned a rating value given in the integer array ratings.

You are giving candies to these children subjected to the following requirements:

Each child must have at least one candy.
Children with a higher rating get more candies than their neighbors, please return the minimum number of candies you need to have to distribute the candies to the children.

    Example 1:
    Input: ratings = [1,0,2]
    Output: 5
    Explanation: You can allocate to the first, second and third child with 2, 1, 2 candies respectively.

    Example 2:
    Input: ratings = [1,2,2]
    Output: 4
    Explanation: You can allocate to the first, second and third child with 1, 2, 1 candies respectively.
    The third child gets 1 candy because it satisfies the above two conditions.

This test is very important , because this give us idea that we should not only take care of rating of neighors but also need to take care of their candies

    ratings = [1  2   3   3   3   2   1]

    expected = 13

## Code 

```
class Solution {
    public int candy(int[] ratings) {
       int n = ratings.length;
        int[] candies = new int[n];
        
        // Initialize each child with 1 candy
        Arrays.fill(candies, 1);
        
        // Scan from left to right, if the current child has a higher rating than the previous one, give more candy
        for (int i = 1; i < n; i++) {
            if (ratings[i] > ratings[i - 1]) {
                candies[i] = candies[i - 1] + 1;
            }
        }
        
        // Scan from right to left, if the current child has a higher rating than the next one, ensure they have more candy
        for (int i = n - 2; i >= 0; i--) {
            if (ratings[i] > ratings[i + 1] && candies[i] <= candies[i + 1]) {
                candies[i] = candies[i + 1] + 1;
            }
        }
        
        // Calculate the total number of candies
        int totalCandies = 0;
        for (int candy : candies) {
            totalCandies += candy;
        }
        
        return totalCandies;
        
    }
}
```