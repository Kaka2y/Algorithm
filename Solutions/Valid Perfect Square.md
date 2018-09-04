# Valid Perfect Square
问题传送门[Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/description/)
```Java
/**
* @author kaka2y
* @date 2018/08/10
*/
package valid_perfect_square;

import java.util.ArrayList;

public class Solution {
	public boolean isPerfectSquare(int num) {
		boolean flag = false;
        double c = num;
        ArrayList<Double> list = new ArrayList<>();
        for(double i = 1; i <= c; i++) {
        	double temp = num / i;
        	if(temp == i)
        		flag = true;
        	if(temp <= c) {
        		list.add(i);
        		list.add(temp);
        		Math.floor(temp);
        		c = temp;
        	}
        }
        return flag;
    }
}
```
做完查看Details的时候，才发现别人是有多么的厉害，自愧不如呀:sweat_smile:
```Java
class Solution {
    public boolean isPerfectSquare(int num) {
        int i=1;
        while(num>0){
            num-=i;
            i+=2;
        }
        return num==0;
    }
}
```