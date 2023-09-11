# 1282. Group the People Given the Group Size They Belong To

[Leetcode - Medium](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/description/?envType=daily-question&envId=2023-09-11)



There are n people that are split into some unknown number of groups. Each person is labeled with a unique ID from 0 to n - 1.

You are given an integer array groupSizes, where groupSizes[i] is the size of the group that person i is in. For example, if groupSizes[1] = 3, then person 1 must be in a group of size 3.

Return a list of groups such that each person i is in a group of size groupSizes[i].

Each person should appear in exactly one group, and every person must be in a group. If there are multiple answers, return any of them. It is guaranteed that there will be at least one valid solution for the given input.

    Example 1:

    Input: groupSizes = [3,3,3,3,3,1,3]
    Output: [[5],[0,1,2],[3,4,6]]
    Explanation: 
    The first group is [5]. The size is 1, and groupSizes[5] = 1.
    The second group is [0,1,2]. The size is 3, and groupSizes[0] = groupSizes[1] = groupSizes[2] = 3.
    The third group is [3,4,6]. The size is 3, and groupSizes[3] = groupSizes[4] = groupSizes[6] = 3.
    Other possible solutions are [[2,1,6],[5],[0,4,3]] and [[5],[0,6,2],[4,3,1]].
    Example 2:

    Input: groupSizes = [2,1,3,3,3,2]
    Output: [[1],[0,5],[2,3,4]]

## Explaination

Here's a step-by-step explanation of the code:

Create an empty list of lists called ans to store the final result. This list will contain sublists representing groups of people.

Initialize a _Map<Integer, List<Integer>>_ named szToGroup to keep track of the groups based on their sizes. The keys of this map represent group sizes, and the values are lists of indices of people with the same group size.

Iterate through the groupSizes array using a for loop:

__a.__ Check if szToGroup already contains the current group size groupSizes[i]. If not, create a new entry in the map with an empty list.

__b.__ Get the list associated with the current group size and add the index i to it. This index represents the position of a person with the same group size.

__c.__ Check if the size of the current group list is equal to the group size itself (groupSizes[i]). If they are equal, it means the group is complete, so add the group list to the ans list, and remove the group size from szToGroup.

After processing all the elements in groupSizes, the ans list will contain sublists representing the grouped people, and you return it as the final result.


## Code

```
class Solution {
    public List<List<Integer>> groupThePeople(int[] groupSizes) {
        List<List<Integer>> ans = new ArrayList<>();
        
        // A map from group size to the list of indices that are there in the group.
        Map<Integer, List<Integer>> szToGroup = new HashMap<>();
        for (int i = 0; i < groupSizes.length; i++) {
            if (!szToGroup.containsKey(groupSizes[i])) {
                szToGroup.put(groupSizes[i], new ArrayList<>());
            }
            
            List<Integer> group = szToGroup.get(groupSizes[i]);
            group.add(i);

            // When the list size equals the group size, empty it and store it in the answer.
            if (group.size() == groupSizes[i]) {
                ans.add(group);
                szToGroup.remove(groupSizes[i]);
            }
        }

        return ans;
    }
}
```
__Time complexity of this code is O(n).__

In summary, this code groups people with the same group size and returns a list of lists where each sublist represents a complete group of people with the specified group size. It does this by using a map to keep track of people with the same group size and forming groups as soon as they reach the desired size.