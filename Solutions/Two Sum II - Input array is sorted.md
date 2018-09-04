# Two Sum II - Input array is sorted
问题传送门[Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)
```Java
/**
 * @author kaka2y
 * @date 2018/08/17
 */
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        if (numbers == null || numbers.length == 0)
        	return null;
        int[] number = new int[2];
        for (int i = 0; i < numbers.length - 1; i++) {
        	for (int j = i + 1; j < numbers.length; j++) {
        		if (numbers[i] + numbers[j] == target) {
        			number = new int[]{i+1,j+1};
        			return number;
        		}
        	}
        }
		return null;
    }
}
```