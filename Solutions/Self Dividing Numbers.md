# Self Dividing Numbers
问题传送门[Self Dividing Numbers](https://leetcode.com/problems/self-dividing-numbers/description/)
```Java
import java.util.List;
import java.util.LinkedList;


/**
 * @author kaka2y
 * @since 2018-08-21
 * @category list
 *
 */
class Solution {
    public List<Integer> selfDividingNumbers(int left, int right) {
        if (left <= 0 || right <=0)
            return null;
        List<Integer> list = new LinkedList<>();
        for (int i = left; i <= right; i++) {
        	boolean flag = false;
        	int temp = i;
            while (temp > 0) {
            	int a = temp % 10;
            	if ((a > 0) && (i % a == 0)) {
            		flag = true;
            	}
            	else {
            		flag = false;
            		break;
            	}
            	temp = temp / 10;
            }
            if (flag == true){
            	list.add(i);
            }
        }
        return list;
    }
}
```