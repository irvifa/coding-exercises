# Add Two Numbers

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    // Time complexity: O(N) where N is max(l1.length, l2.length)
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = new ListNode();
        ListNode ptr = head;
        int carry = 0;
        while (l1 != null || l2 != null) {
            int a = 0;
            int b = 0;
            if (l1 != null) {
                a = l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                b = l2.val;
                l2 = l2.next;
            }
            int val = (carry + a + b);
            carry = val / 10;
            val %= 10;
            ListNode toAdd = new ListNode(val);
            ptr.next = toAdd;
            ptr = ptr.next;
        }
        
        if (carry == 1) {
            ListNode toAdd = new ListNode(carry);
            ptr.next = toAdd;
            ptr = ptr.next;
        }
        return head.next;
    }
}
```
