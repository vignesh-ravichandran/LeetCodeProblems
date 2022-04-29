Given the head of a linked list, rotate the list to the right by k places.

 

Example 1:


Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]
Example 2:


Input: head = [0,1,2], k = 4
Output: [2,0,1]
 

Constraints:

The number of nodes in the list is in the range [0, 500].
-100 <= Node.val <= 100
0 <= k <= 2 * 109
Accepted
550.8K
Submissions
1.6M
Seen this question in a real interview before?


        var rotateRight = function(head, k) {
            
            function reverse(head1){
                let count = 0;
            
            let nh = null;
            let h = head1;
            
            while(h!=null){
                let t = h;
                h = h.next;
                t.next = nh;
                nh = t;
                count++;
            }
                
                return nh;
            }
            
            
            if(head == null || head.next == null || k==0) return head;
            
            let sp = head;
            let fp = head;
            let count = 1;
            while(fp.next && fp.next.next){
                sp = sp.next;
                fp = fp.next.next;
                count = count + 2;
            }
            if(fp.next){
                count++;
            }
            k = k % count;
            if(k==0) return head;
            let m = count -k;
            
            let c1 = head;
            let i=0;
            while(c1!=null && i<m-1){
                c1 = c1.next;
                i++;
            }
            
            let sh = c1.next;
            c1.next = null;
            
            let c2 = sh; 
            while(c2!= null && c2.next != null){
                c2 = c2.next;
            }
            c2.next = head;
            
            return sh;
            
            
        };