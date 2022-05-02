Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

 

Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: 3
Example 2:

Input: root = [1,null,2]
Output: 2
 

Constraints:

The number of nodes in the tree is in the range [0, 104].
-100 <= Node.val <= 100
Accepted
1,647,556
Submissions
2,292,935


Solution: 


        var maxDepth = function(root) {
            return maxDepthOfTree(root);
        };

        var maxDepthOfTree = function (root){
            
            if(root == null ) return 0;
            
            let leftSubTreeDepth = maxDepthOfTree(root.left);
            let rightSubTreeDepth = maxDepthOfTree(root.right);
            
            return 1 + Math.max(leftSubTreeDepth, rightSubTreeDepth);

        }