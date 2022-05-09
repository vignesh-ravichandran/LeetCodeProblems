You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:

struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

 

Example 1:


Input: root = [1,2,3,4,5,6,7]
Output: [1,#,2,3,#,4,5,6,7,#]
Explanation: Given the above perfect binary tree (Figure A), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '#' signifying the end of each level.
Example 2:

Input: root = []
Output: []
 

Constraints:

The number of nodes in the tree is in the range [0, 212 - 1].
-1000 <= Node.val <= 1000
 

Follow-up:

You may only use constant extra space.
The recursive approach is fine. You may assume implicit stack space does not count as extra space for this problem.


Solution: 


        var connect = function(root) {
            
            if(root == null) return root
            
            return connectRight(root);
        };

        var connectRight = function(root){
            root.next = null;
            let verticalPointer = root;
            while(verticalPointer!= null){
                let curr = verticalPointer;
            while(curr!=null){
                if(curr.left){
                    if(curr.right){
                        curr.left.next = curr.right;
                    }else{
                        curr.left.next = getNextRight(curr);
                    }
                }
                if(curr.right){
                    curr.right.next = getNextRight(curr);
                }
                curr = curr.next;
                }
                if(verticalPointer.left){
                    verticalPointer = verticalPointer.left;
                }else{
                    verticalPointer = getNextRight(curr);
                }
            
            }
            
            return root;
        }

        var getNextRight = function(root){
            if(root == null) return null;
            let curr = root.next;
            while(curr!= null){
                if(curr.left) return curr.left;
                if(curr.right) return curr.right;
                curr = curr.next;
            }
            return null;
        }