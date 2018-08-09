# Word Pattern
[问题链接](https://leetcode.com/problems/word-pattern/description/)

```Java
import java.util.HashMap;

class Solution {
    public boolean wordPattern(String pattern, String str) {
    	boolean flag = false;
    	int len = pattern.length();
        String[] newString = str.split(" ");
    	if(str == " " || str == null || newString.length != len){
    		return flag;
    	}
        HashMap<String,String> Capacity = new HashMap<>(len);
        for(int i = 0; i < len; i++) {
        	if(!(Capacity.containsKey(String.valueOf(pattern.charAt(i))) || Capacity.containsValue(newString[i]))) {
            	Capacity.put(String.valueOf(pattern.charAt(i)), newString[i]);
        	}
        }
        for(int j = 0; j < len; j++) {
        	String k = String.valueOf(pattern.charAt(j));
        	String v = newString[j];
        	if(Capacity.containsKey(k)){
        		if(Capacity.get(k).equals(v)){
            		flag = true;
            	}
            	else{
            		return false;
            	}
        	}
        	else
        		return false;
        }
        return flag;
    }
}
```
