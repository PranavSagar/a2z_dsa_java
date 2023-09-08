# Segrregate odd and even nodes in LL

Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity. 


## Code 

``` 
public ListNode oddEvenList(ListNode head) {

        if(head == null || head.next == null){
            return head;
        }
        ListNode oddPointer = head;
        ListNode evenPointer = head.next;
        ListNode evenStartPointer = evenPointer;

        while(oddPointer.next!= null && evenPointer.next != null){
            oddPointer.next = evenPointer.next;
            oddPointer = oddPointer.next;
            evenPointer.next = oddPointer.next;
            evenPointer = evenPointer.next;
        }

        oddPointer.next = evenStartPointer;

        if(evenPointer != null){
            evenPointer.next = null;
        }
        return head;
    }
    ```