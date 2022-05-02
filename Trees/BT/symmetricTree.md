Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

 

Example 1:


Input: root = [1,2,2,3,4,4,3]
Output: true
Example 2:


Input: root = [1,2,2,null,3,null,3]
Output: false
 

Constraints:

The number of nodes in the tree is in the range [1, 1000].
-100 <= Node.val <= 100
 

Follow up: Could you solve it both recursively and iteratively?

Solution: 

        var isSymmetric = function(root) {
            
            if(root == null) return true;
            
            return checkSymmetric(root.left, root.right);
            
        };

        var checkSymmetric = function (root1, root2){
            
            if(root1 == null && root2 == null) return true;
            if(root1 == null || root2 == null) return false;
            
            if(root1.val != root2.val) return false;
            
            return checkSymmetric(root1.right, root2.left) && checkSymmetric(root1.left, root2.right);
        }