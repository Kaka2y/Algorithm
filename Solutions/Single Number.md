# Single Number
问题传送门[Single Number](https://leetcode.com/problems/single-number/description/)
```Java
import java.util.LinkedList;
/**
* @author kaka2y
* @date 2018/08/23
*/
class Solution {
    public int singleNumber(int[] nums) throws IndexOutOfBoundsException{
    	LinkedList<Integer> targetNum = new LinkedList<>();
    	for (int num : nums) {
    		if (!targetNum.contains(num))
    			targetNum.add(num);
    		else
    			targetNum.remove(targetNum.indexOf(num));
    	}
    	return targetNum.pop();
    }
}
```

附上一份在More Datials里看到的解法，真的是厉害。使用异或操作，相同的两个数异或的结果就是0，就可以直接消除了相同数的存在，也不用借助其他的数据结构来操作数组。
```Java
/**
* from LeetCode
*/
class Solution {
    public int singleNumber(int[] nums) {
        int rv = 0;
        for (int i = 0; i < nums.length; i++) {
            rv ^= nums[i];
        }
        return rv;
    }
}
```