# Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

 
- Example 1:  
Input: strs = ["flower","flow","flight"]  
Output: "fl"  
- Example 2:    
Input: strs = ["dog","racecar","car"]  
Output: ""  
Explanation: There is no common prefix among the input strings.

## Code 
[Leetcode](https://leetcode.com/problems/longest-common-prefix/)

Approach 1
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        Arrays.sort(strs);
        int i =0,j=0,n = strs[0].length(),m = strs[strs.length-1].length();
        while(i<n && j <m){
            if(strs[0].charAt(i) == strs[strs.length-1].charAt(j)){
                i++;j++;
            }else{
                break;
            }
        }
        int ans = Math.max(i,j);

        return strs[0].substring(0,ans);
        
    }
}
```

Approach 2
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        StringBuilder str = new StringBuilder();
        int n = strs.length;
        int m = strs[0].length();
        for(int i = 0;i<m;i++){
            char ch = strs[0].charAt(i);
            for(int j = 1;j<n;j++){
                if(i >= strs[j].length() || strs[j].charAt(i)!=ch) return str.toString();
            }
            str.append(ch);
        }
        return str.toString();
    }
}
```