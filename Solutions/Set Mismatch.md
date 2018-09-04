# Set Mismatch
问题传送门[Set Mismatch](https://leetcode.com/problems/set-mismatch/description/)
```Java
/**
 * @author kaka2y
 * @date 2018/09/02
 */
class Solution {
    public int[] findErrorNums(int[] nums) {
    	if (nums == null || nums.length == 1) 
    		return null;
		int repet = 0;
		int miss = 0;
    	for (int i = 1; i <= nums.length; i++) {
    		int count = 0;
    		for (int j = 0; j < nums.length; j++) {
    			if (nums[j] == i)
    				count++;
    		}
    		if (count == 2)
    			repet = i;
    		if (count == 0)
    			miss = i;
    	}
        return new int[]{repet,miss};
    }
}
```