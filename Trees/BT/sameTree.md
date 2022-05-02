Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

 

Example 1:


Input: p = [1,2,3], q = [1,2,3]
Output: true
Example 2:


Input: p = [1,2], q = [1,null,2]
Output: false
Example 3:


Input: p = [1,2,1], q = [1,1,2]
Output: false
 

Constraints:

The number of nodes in both trees is in the range [0, 100].
-104 <= Node.val <= 104
Accepted
1,020,156
Submissions
1,837,594


Solution: 


        var isSameTree = function(p, q) {
            
            function isSame(r1, r2){
                    if(r1 == null && r2 == null) return true;
                    if(r1==null || r2 == null) return false;
                    
                    if(r1.val != r2.val) return false;
                    
                    return isSame(r1.right, r2.right) && isSame(r1.left, r2.left);
                }
                
                return isSame(p, q);
            
        };