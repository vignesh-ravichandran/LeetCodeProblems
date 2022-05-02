You are given the root of a binary search tree (BST) and an integer val.

Find the node in the BST that the node's value equals val and return the subtree rooted with that node. If such a node does not exist, return null.

 

Example 1:


Input: root = [4,2,7,1,3], val = 2
Output: [2,1,3]
Example 2:


Input: root = [4,2,7,1,3], val = 5
Output: []
 

Constraints:

The number of nodes in the tree is in the range [1, 5000].
1 <= Node.val <= 107
root is a binary search tree.
1 <= val <= 107



Solution: 


        var searchBST = function(root, val) {
            
            function sea(r, k){
                
                if(r==null) return null;
                
                if(r.val == k) return r;
                
                let l = sea(r.right,k);
                if(l!= null) return l;
                
                let ri = sea(r.left, k);
                if(ri!=null) return ri;
                
                return null;
                
                
            
            }
            
            return sea(root, val);
            
        };