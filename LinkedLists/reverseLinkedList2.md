Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list.

 

Example 1:


Input: head = [1,2,3,4,5], left = 2, right = 4
Output: [1,4,3,2,5]
Example 2:

Input: head = [5], left = 1, right = 1
Output: [5]
 

Constraints:

The number of nodes in the list is n.
1 <= n <= 500
-500 <= Node.val <= 500
1 <= left <= right <= n
 

Follow up: Could you do it in one pass?


Solution: 


        var reverseBetween = function(head, left, right) {
            console.log(left, right)
            
            function reverseK(r, k){
                if(r==null || r.next == null) return r;
                
                let i=0;
                let oh = r;
                let nh = null;
                while(r!=null && i<k){
                    let t = r;
                    r= r.next;
                    t.next = nh;
                    nh = t;
                    i++;
                }
                oh.next = r;
                return nh;
            }
            
            
            
            if(head == null || head.next == null) return head;
            
            if(left == 1){
                head = reverseK(head, right-left+1);
            }else{
                let i=1;
                let curr = head;
                while(curr!= null && i< (left-1)){
                    curr = curr.next;
                    i++;
                }
                curr.next = reverseK(curr.next, right-left+1);
            }
            
            return head;
        };
