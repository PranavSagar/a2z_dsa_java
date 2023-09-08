# Starting point of loop in a Linked List
 
__Problem Statement:__  
Given the head of a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that the tail’s next pointer is connected to (0-indexed). It is -1 if there is no cycle. Note that pos is not passed as a parameter.

## Code

#### Approach 1 (Brute forece) using hashmap

```
static Node detectCycle(Node head) {
    HashSet<Node> st=new HashSet<>();
    while(head != null) {
        if(st.contains(head)) return head;
        st.add(head);
        head = head.next;
    }
    return null;
}
```


#### Approach 2 (optimal solution ) 
##### Using slow and fast pointer

```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if(head == null||head.next == null) return null;
        
    ListNode fast = head;
    ListNode slow = head;
    ListNode entry = head;
        
    while(fast.next != null&&fast.next.next != null) {
        slow = slow.next;
        fast = fast.next.next;
            
        if(slow == fast) {
            while(slow != entry) {
                slow = slow.next;
                entry = entry.next;
            }
            return slow;
        }
    }
    return null;
    }
}
```