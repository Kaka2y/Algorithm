# Shortest Distance to a Character
问题传送门[Shortest Distance to a Character](https://leetcode.com/problems/shortest-distance-to-a-character/description/)
```Java
/**
* @author kaka2y
* @date 2018/08/18
*/
import java.util.LinkedList;
import java.util.List;

class Solution {
    public int[] shortestToChar(String S, char C) {
        if (S == null || S.length() == 0)
            return null;
        List<Integer> distance = new LinkedList<>();
        int dis = 0;
        for (char c : S.toCharArray()) {
        	if (c == C) {
        		dis = 0;
        		distance.add(dis);
        	}
        	else if (!distance.contains(0)) {
        		distance.add(9999);
        	}
        	else {
        		dis++;
        		distance.add(dis);
        	}
        }
        
        
        String reverse = new StringBuffer(S).reverse().toString();
        
        int index = distance.size();
        //System.out.println(index);
        for (char c : reverse.toCharArray()) {
        	--index;
        	if (c == C) {
        		dis = 0;
        	}
        	else {
        		dis++;
        		if (dis < distance.get(index)) {
        			distance.remove(index);
        			distance.add(index, dis);
        		}
        	}
        }
        
        Integer[] result = distance.toArray(new Integer[distance.size()]);
        int[] list = new int[result.length];
        for (int i = 0; i < result.length; i++) {
        	list[i] = result[i];
        }
        return list;
    }
}

```