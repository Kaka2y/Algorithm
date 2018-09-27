# Title
问题传送门[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)

```Java
/**
 * 
 * @author kaka2y
 * @date 2018/09/27
 * @category 
 */
 class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) {
            return "";
        }
        int n = 1;
        String prefix = "";
        
        boolean flag = true;
        while(flag && (n <= strs[0].length())){
        	String sub = strs[0].substring(0, n);
        	for(String str : strs) {
        		if (str.startsWith(sub)){
        			flag = true;
        		}
        		else {
        			flag = false;
        			break;
        		}
        	}
        	if (flag)
        		n += 1;
        }
        prefix = strs[0].substring(0, n-1);
        return prefix;
    }
}
```