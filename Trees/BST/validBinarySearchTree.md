Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
 

Example 1:


Input: root = [2,1,3]
Output: true
Example 2:


Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
 

Constraints:

The number of nodes in the tree is in the range [1, 104].
-231 <= Node.val <= 231 - 1
Accepted
1,386,546
Submissions
4,541,862


Solution: 


        var isValidBST = function(root) {
            
            return isValidBSTCheck(root, Number.MIN_SAFE_INTEGER, Number.MAX_SAFE_INTEGER);
            
        };

        var isValidBSTCheck = function (root, lowLimit, highLimit){
            
            if(root == null) return true;
            //if(root.val == lowLimit && root.val == highLimit){}
            if(root.val > lowLimit && root.val < highLimit){
                return isValidBSTCheck(root.left, lowLimit, root.val) && isValidBSTCheck(root.right, root.val, highLimit)
            }else{
                return false;
            }
        }