Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

 

Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
Example 2:

Input: root = [1]
Output: [[1]]
Example 3:

Input: root = []
Output: []
 

Constraints:

The number of nodes in the tree is in the range [0, 2000].
-1000 <= Node.val <= 1000


Solution: 


        class Queue2 {
            constructor(){
                this.q = [];
                this.start = 0;
                this.size = 0;
                this.end = 0;
            }
            
            enqueue(n){
                this.q.push(n);
                this.size = this.size + 1;
                this.end++
            }
            
            sizet(){
                return this.end - this.start;
            }
            
            dequeue(){
                
                let t = this.q[this.start];
                delete this.q[this.start];
                if(this.end >= this.start){
                    this.start++;
                this.size = this.size - 1;
                }
                
                
                return t;
            }
        }
        var levelOrder = function(root) {
            if(!root) return [];
            let r = root;
            let q1 = new Queue2();
            let result = [];
            q1.enqueue(root);
            
            while(q1.sizet() > 0){
                let l = q1.sizet();
                let level = [];
                for(let i=0; i<l; i++){
                    
                    let t = q1.dequeue();
                    if(t && t.left && t.left != undefined) q1.enqueue(t.left);
                    if(t && t.right && t.right!= undefined){
                        q1.enqueue(t.right);
                    } 
                    if(t) level.push(t.val);
                }
                result.push(level);
            }

            return result;
            
        };