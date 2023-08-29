# Roman Numeral To Integer

[CodeStudio - Easy](https://www.codingninjas.com/studio/problems/roman-numeral-to-integer_981308?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)

[Leetcode - Easy](https://leetcode.com/problems/roman-to-integer)

## Code

```
class Solution {
    public int romanToInt(String s) {
        int result = 0;
        for (int i = 0; i < s.length(); i++) {
            int curr = getValue(s.charAt(i));
            int next = (i + 1 < s.length()) ? getValue(s.charAt(i + 1)) : 0;
            if (curr >= next) result += curr;
            else result -= curr;   
         }
        return result;
    }

    private int getValue(char c) {
        switch (c) {
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            case 'M': return 1000;
            default: return 0;
        }
    }
}
```