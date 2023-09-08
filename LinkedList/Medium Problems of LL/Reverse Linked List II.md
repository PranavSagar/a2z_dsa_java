# Reverse Linked List II

Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list.

    Example 1:
    Input: head = [1,2,3,4,5], left = 2, right = 4
    Output: [1,4,3,2,5]

 
    Example 2:
    Input: head = [5], left = 1, right = 1
    Output: [5]


## Code

```
    public ListNode reverseBetween(ListNode head, int left, int right) {
          if (head == null || left == right) {
            return head;
        }

        ListNode dummy = new ListNode(-1);
        dummy.next = head;
        ListNode prevLeft = dummy;
        ListNode curr = head;

        for (int i = 1; i < left; i++) {
            prevLeft = prevLeft.next;
            curr = curr.next;
        }

        ListNode prev = null;
        ListNode next = null;

        for (int i = left; i <= right; i++) {
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        prevLeft.next.next = curr;
        prevLeft.next = prev;

        return dummy.next;
    }
```