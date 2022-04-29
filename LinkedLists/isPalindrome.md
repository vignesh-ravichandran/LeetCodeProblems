Given the head of a singly linked list, return true if it is a palindrome.

 

Example 1:


Input: head = [1,2,2,1]
Output: true
Example 2:


Input: head = [1,2]
Output: false
 

Constraints:

The number of nodes in the list is in the range [1, 105].
0 <= Node.val <= 9
 

Follow up: Could you do it in O(n) time and O(1) space?
Accepted
948.6K
Submissions
2M
Seen this question in a real interview before?


Solution: 

        var isPalindrome = function(head) {
            
            function reverse(h){
                if(h==null || h.next == null) return h;
                let nh = null;
                while(h!= null){
                    let t = h;
                    h = h.next;
                    t.next = nh;
                    nh = t;
                }
                
                return nh;
            }
            
            if(head == null || head.next == null){
                return head;
            }
            
            let sp = head;
            let fp = head.next;
            while(fp.next && fp.next.next){
                sp = sp.next;
                fp = fp.next.next;
            }
            
            let re = reverse(sp.next);
            
            let no = head;
            
            while(no!=null && re!= null){
                if(no.val != re.val ) return false;
                no = no.next;
                re = re.next;
            }
            
            return true;
            
            
            
            
            
        };