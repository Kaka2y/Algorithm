# Roman to Integer
问题传送门[https://leetcode.com/problems/roman-to-integer/description/]
```java
import java.util.HashMap;
/**
 * 
 * @author kaka2y
 * @date 2018/09/26
 */
class Solution {
    public int romanToInt(String s) {
    	if (s == null || s.length() == 0) {
    		return -1;
    	}
    	HashMap<Character,Integer> toIntMap = new HashMap<>();
    	toIntMap.put('I', 1);
    	toIntMap.put('V', 5);
    	toIntMap.put('X', 10);
    	toIntMap.put('L', 50);
    	toIntMap.put('C', 100);
    	toIntMap.put('D', 500);
    	toIntMap.put('M', 1000);
    	
        int sum = 0;
        for (int i=0;i<= s.length() - 1;i++){
        	if (i <= s.length() -2) {
        		int temp = toIntMap.get(s.charAt(i+1)) - toIntMap.get(s.charAt(i));
            	boolean flag = (temp == 4 || temp == 9 || temp == 40 || temp == 90 || temp == 400 
            			|| temp == 900);
            	/*
        		 * 当后一位减去前一位的值为4/9/40/90/400/900时
        		 * 即先减去当前位的值
        		 */
            	if (flag) {
            		sum -= toIntMap.get(s.charAt(i));
            	}
            	else {
            		sum += toIntMap.get(s.charAt(i));
            	}
        	}
        	else {
        		sum += toIntMap.get(s.charAt(i));
        	}
        }
        return sum;
    }
}
```