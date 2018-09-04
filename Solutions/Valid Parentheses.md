# Valid Parentheses
问题传送门[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)
```Java
/**
* @author kaka2y
* @date 2018/08/11
*/
import java.util.Stack;
import java.util.HashMap;

class Solution {
    public boolean isValid(String s) {
        if (s == " " || s == null)
            return false;
        
        //作为对比的字符数组
        //char[] check = {'(', ')', '[', ']', '{', '}'};
        
        HashMap<Character,Character> brackets = new HashMap<>();
        brackets.put('(', ')');
        brackets.put('[', ']');
        brackets.put('{', '}');
        
        //使用栈来存储字符型的括号
        Stack<Character> bracketStack = new Stack<>();
        
        for (char c : s.toCharArray()) {
        	//校验字符串
        	/*for (char bracket : check) {
        		if (c == bracket){}
        		else return false;
        	}*/
        	
        	//如果栈为空，先入栈
        	if (bracketStack.empty()) {
        		if (c == '(' || c == '[' || c == '{')
        			bracketStack.push(c);
        		else 
        			return false;
        	}
        	else {
        		if (c == '(' || c == '[' || c == '{') {
        			bracketStack.push(c);
        		}
        		else {
        			if (c == brackets.get(bracketStack.peek())) {
                		bracketStack.pop();
                	}
                	else {
                		return false;	
                	}
        		}
        	}
        }
        
        return bracketStack.empty();
    }
}
```
这一题不难，主要是对HashMap这个类的操作还不是那么的熟悉，在debug的过程中，出现了两次`NullPointException`空指针错误
```Java
Exception in thread "main" java.lang.NullPointerException
	at valid_parentheses.Solution.isValid(Solution.java:41)
	at valid_parentheses.Test.main(Test.java:7)
```
这是使用HashMap的`get(key)`方法不当引起的，传入了无效的`key`值，HashMap中原先没有存入这个，所以报了空指针错误。