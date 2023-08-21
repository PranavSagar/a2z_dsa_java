# Valid Anagram
Example 1:  
Input: s = "anagram", t = "nagaram"
Output: true  
Example 2:  
Input: s = "rat", t = "car"
Output: false

## Code
[Leetcode](https://leetcode.com/problems/valid-anagram)
```
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] set = new int[26];
        for(char c : s.toCharArray()){
            set[c-'a']++;
        }
        for(char c : t.toCharArray()){
            set[c-'a']--;
        }

        for(int i =0;i<26;i++){
            if(set[i]!=0){
                return false;
            }
        }
        return true;

        
    }
}
```