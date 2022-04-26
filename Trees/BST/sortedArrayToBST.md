Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

 

Example 1:


Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:

Example 2:


Input: nums = [1,3]
Output: [3,1]
Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.
 

Constraints:

1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums is sorted in a strictly increasing order.



Solution: 


        var sortedArrayToBST = function(nums) {
            
            function build(arr, s, e){
                if(s > e) return null;
                let m = parseInt((e+s)/2);
                let r = new TreeNode(arr[m]);
                
                r.left = build(arr, s, m-1);
                r.right = build(arr, m+1, e);
                
                return r;
            }
            
            return build(nums, 0, nums.length-1);
            
        };