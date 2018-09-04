# Ugly Number
问题传送门[Ugly Number](https://leetcode.com/problems/ugly-number/description/)
```Java
/**
 * @author kaka2y
 * @date 2018/08/14
 */
class Solution {
    public boolean isUgly(int num) {
    	
        if (num == 0 || num > Integer.MAX_VALUE || num < Integer.MIN_VALUE)
        	return false;
        
        while (num != 1) {
        	if (num % 2 == 0) 
        		num /= 2;
        	else if (num % 3 == 0)
        		num /= 3;
        	else if (num % 5 == 0)
        		num /= 5;
        	else break;
        }
        
        return num == 1;
    }
}
```