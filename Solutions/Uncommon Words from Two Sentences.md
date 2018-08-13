# Uncommon Words from Two Sentences
问题传送门[Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/description/)
```Java
/**
* @author, kaka2y
* @date, 2018-08-13
* @type, Array
*/
import java.util.LinkedList;

class Solution {
    public String[] uncommonFromSentences(String A, String B) {
    	
    	LinkedList<String> wordList = new LinkedList<>();
    	
    	//拼接起来操作，减少需要遍历的字符串数组
    	String joinString = A + " " + B;
    	String[] join = joinString.split(" ");
    	
    	
    	for (String word1 : join) {
    		//用来统计字符串相同的个数
    		int count = 0;
    		for (String word2 : join) {
    			if (!word1.equals(word2))
    				count += 1;
    		}
    		//因为遍历的时候也对它本身进行1次equals操作，所以需要-1
    		if (count == join.length-1)
    			wordList.add(word1);
    	}
        
        String[] list = wordList.toArray(new String[wordList.size()]);
    	return list;
    }
}
```
对于要输出的字符串数组，只需要进行增加操作即可，所以这里选用了`LinkedList`，因为它实现了`Deque<E>`接口，插入数据速度更快，性能更高（如果需要插入大量数据的话）