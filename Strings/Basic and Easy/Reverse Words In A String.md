# Reverse Words In A String

## Code 

[Leetcode](https://leetcode.com/problems/reverse-words-in-a-string/submissions/)

```
class Solution {
    public String reverseWords(String s) {
         String[] words = s.trim().split("\\s+");
        StringBuilder reversed = new StringBuilder();
        System.out.print(words[0]);
        for (int i = words.length - 1; i >= 0; i--) {
            reversed.append(words[i]);
            if (i > 0) {
                reversed.append(" ");
            }
        }

        return reversed.toString();
    }
}
```
[CodeStudio](https://www.codingninjas.com/studio/problems/reverse-words-in-a-string_696444?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf&leftPanelTab=0)

```
public class Solution 
{
	public static String reverseString(String input) 
	{
		String[] words = input.split("\\s+");
        StringBuilder reversed = new StringBuilder();

        for (int i = words.length - 1; i >= 0; i--) {
            reversed.append(words[i]);
            if (i > 0) {
                reversed.append(" ");
            }
        }

        return reversed.toString();
	}
}
```


