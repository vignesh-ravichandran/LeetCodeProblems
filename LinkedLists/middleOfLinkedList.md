Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

 

Example 1:


Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
Example 2:


Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
 

Constraints:

The number of nodes in the list is in the range [1, 100].
1 <= Node.val <= 100
Accepted
649,057
Submissions
893,129


Solution: 


        var middleNode = function(head) {
        // if(head == null) return null
            let sp = head;
            let fp = head;
            
            while(fp!= null && fp.next != null){
                sp = sp.next;
                fp = fp.next.next;
            }
            
            return sp;
            
        };