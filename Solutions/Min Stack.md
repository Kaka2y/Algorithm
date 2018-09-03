# Min Stack
问题传送门[Min Stack](https://leetcode.com/problems/min-stack/description/)

使用了Java本身提供的类来实现，在实现getMin()方法的时候，因为没有将原有的stack对象做复制处理，导致使用pop()方法筛选最小数的时候，stack对象会变成空，再次调用pop会产生EmptyStackException错误。
```Java
import java.util.Stack;
/**
 * @author kaka2y
 * @since 2018-09-03
 * @category Stack
 */
class MinStack {

	int min;
	Stack<Integer> stack;
	
    /** initialize your data structure here. */
    public MinStack() {
        stack = new Stack<>();
    }
    
    public void push(int x) {
        stack.push(x);
    }
    
    public void pop() {
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
    	min = stack.peek();
    	//重新拷贝一个对象，做弹出数据比较用
    	Stack<Integer> newStack = (Stack<Integer>)stack.clone();
    	
    	while(!newStack.isEmpty()) {
    		int a = newStack.pop();
    		if(a < min)
    			min = a;
    	}
    	return min;
    }
}
```
## improve 1
另一个解法的思路是：在push数据的时候去做数据的比较工作，筛选出最小的数，虽然其时间复杂度都是O(n)，不过可以减少复制一个stack对象所需要消耗的空间，在当栈中的数据量较大的时候，这个算法的优势会比较明显。
```Java
/**
 * @author kaka2y
 * @since 2018-09-03
 * @category Stack
 */
class Solution {

	int min = Integer.MAX_VALUE;
	Stack<Integer> stack;
	
    /** initialize your data structure here. */
    public Solution() {
        stack = new Stack<>();
    }
    
    public void push(int x) {
    	if(x < min)
    		min = x;
        stack.push(x);
    }
    
    public void pop() {
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
    	return min;
    }
}
```
## more
在这里没有自定义一个stack对象，而是使用了Java提供的，是一点不足。