Given head which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.

Return the decimal value of the number in the linked list.

 

Example 1:


Input: head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
Example 2:

Input: head = [0]
Output: 0
 

Constraints:

The Linked List is not empty.
Number of nodes will not exceed 30.
Each node's value is either 0 or 1.
Accepted
282,886
Submissions
342,211


Solution: 


        var getDecimalValue = function(head) {
            
            //One approach is to reverse linkedlist and calculate but we can calculate binary to decimal in reverse too


            let curr = head; 
            let result = 0;
            while(curr!=null){
                let p = 2;
                if(curr.next == null){
                    p = 1;
                }
                
                result = (result * p) + (p * curr.val);
                curr = curr.next;
            }
            
            return result;
            
        };