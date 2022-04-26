Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

 

Example 1:


Input: head = [1,2,3,4]
Output: [2,1,4,3]
Example 2:

Input: head = []
Output: []
Example 3:

Input: head = [1]
Output: [1]
 

Constraints:

The number of nodes in the list is in the range [0, 100].
0 <= Node.val <= 100


Solution: 

        var swapPairs = function(head) {
            
            function reverseN(r, n){
                    if(r==null || r.next == null) return r;
                    let oh = r;
                    let nh = null;
                    let k = 0;
                    while(r!= null && k<n){
                        let t = r;
                        r = r.next;
                        t.next = nh;
                        nh = t;
                        k++;
                    }
                    oh.next = reverseN(r, n);
                    return nh;
                }
                
                return reverseN(head, 2)
            
        };