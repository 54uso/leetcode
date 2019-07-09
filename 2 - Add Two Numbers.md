#2 - Add Two Numbers

### Problem
<p>You are given two <b>non-empty</b> linked lists representing two non-negative integers. The digits are stored in <b>reverse order</b> and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> (2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<b>Output:</b> 7 -&gt; 0 -&gt; 8
<b>Explanation:</b> 342 + 465 = 807.
</pre>


### Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode ret = new ListNode(0);
        ListNode t = ret;
        int p = 0;
        while (l1 != null && l2 != null) {
            int tmp = p + l1.val + l2.val;
            t.next = new ListNode(tmp % 10);
            p = tmp / 10;
            l1 = l1.next;
            l2 = l2.next;
            t = t.next;
        }
        while (l1 != null) {
            int tmp = p + l1.val;
            t.next = new ListNode(tmp % 10);
            p = tmp / 10;
            l1 = l1.next;
            t = t.next;
        }
        while (l2 != null) {
            int tmp = p + l2.val;
            t.next = new ListNode(tmp % 10);
            p = tmp / 10;
            l2 = l2.next;
            t = t.next;
        }
        if (p != 0) {
            t.next = new ListNode(p);
        }
        return ret.next == null ? ret : ret.next;
    }
}
```
### Link: [https://leetcode.com/problems/add-two-numbers/](https://leetcode.com/problems/add-two-numbers/)
