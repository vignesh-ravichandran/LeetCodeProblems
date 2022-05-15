Given the root of a binary tree, return the average value of the nodes on each level in the form of an array. Answers within 10-5 of the actual answer will be accepted.
 

Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].
Example 2:


Input: root = [3,9,20,15,7]
Output: [3.00000,14.50000,11.00000]
 

Constraints:

The number of nodes in the tree is in the range [1, 104].
-231 <= Node.val <= 231 - 1
Accepted
269,816
Submissions
392,429


Solution: 


        var averageOfLevels = function(root) {
            
            let result = [];
            
            let q = [];
            q.push(root);
            
            
            while(q.length > 0){
                
                let len = q.length; 
                let sum = 0;
                for(let i=0; i<len; i++){
                    let curr = q.shift();
                    sum = sum + curr.val;
                    if(curr.left) q.push(curr.left);
                    if(curr.right) q.push(curr.right);
                }
                
                let avg = sum / len;
                result.push(avg);
            }
            
            return result;
            
        };