# Insert a node in DLL

![ques](image.png)

## Code

```
/****************************************************************

 Following is the class structure of the Node class:

 class Node {
     public int data;
     public Node next;
     public Node prev;

     Node()
     {
         this.data = 0;
         this.next = null;
         this.prev = null;
     }

     Node(int data)
     {
         this.data = data;
         this.next = null;
         this.prev = null;
     }

     Node(int data, Node next, Node prev)
     {
         this.data = data;
         this.next = next;
         this.prev = prev;
     }
 };

 *****************************************************************/

public class Solution
{
    public static Node insertAtTail(Node list, int K) {
        Node newNode = new Node(K);
        if(list == null){
            return newNode;
        }
        Node head = list;
        while(head.next!= null){
            head = head.next;
        }
        
        
        head.next = newNode;
        newNode.prev = head;
        newNode.next = null;

        return list;

    }
}
```

