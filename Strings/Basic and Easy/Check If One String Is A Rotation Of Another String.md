# Check If One String Is A Rotation Of Another String

- Example 1:  
Input: s = "abcde", goal = "cdeab"
Output: true
- Example 2:  
Input: s = "abcde", goal = "abced"
Output: false
## Code

```
public class Solution {
    public static int isCyclicRotation(String s, String goal)  {
        if (s == null || goal == null || s.length() != goal.length()) {
            return 0;
        }
        
        String doubledS = s + s; // Concatenate s with itself
        
        return doubledS.contains(goal)?1:0;
    }
}
111