# Merge Two Sorted Lists
问题传送门[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/description/)
```Java
/**
 * @author kaka2y
 * @since 2018-09-04
 * @category List
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    	if(l1 == null) {
    		return l2;
    	}
    	if(l2 == null) {
    		return l1;
    	}
    	ListNode newList = new ListNode(0);
    	ListNode newList1 = newList;
        while(l1 != null && l2 != null) {
            if(l1.val >= l2.val) {
                newList1.next = l2;
                l2 = l2.next;
            }
            else {
                newList1.next = l1;
                l1 = l1.next;
            }
            newList1 = newList1.next;
        }
        if(l1 != null) {
        	newList1.next = l1;
        }
        if(l2 != null) {
        	newList1.next = l2;
        }
        return newList.next;
    }
}
```