# Remove outermost Paranthesis

## Code

#### leetcode https://leetcode.com/problems/remove-outermost-parentheses/
```
class Solution {
    public String removeOuterParentheses(String s) {
        StringBuilder result = new StringBuilder();
        int openCount = 0;
        
        for (char ch : s.toCharArray()) {
            if (ch == '(' && openCount > 0) {
                result.append(ch);
            }
            if (ch == ')' && openCount > 1) {
                result.append(ch);
            }
            
            if (ch == '(') {
                openCount++;
            } else {
                openCount--;
            }
        }
        
        return result.toString();
        
    }
}
```

CodeStudio https://www.codingninjas.com/studio/problems/maximum-nesting-depth-of-the-parentheses_8144741?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf

```
public class Solution {
     public static int maxDepth(String s) {
        int maxDepth = 0;
        int currentDepth = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                currentDepth++;
                maxDepth = Math.max(maxDepth, currentDepth);
            } else if (ch == ')') {
                currentDepth--;
            }
        }

        return maxDepth;
    }
}
```