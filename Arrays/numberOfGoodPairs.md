Given an array of integers nums, return the number of good pairs.

A pair (i, j) is called good if nums[i] == nums[j] and i < j.

 

Example 1:

Input: nums = [1,2,3,1,1,3]
Output: 4
Explanation: There are 4 good pairs (0,3), (0,4), (3,4), (2,5) 0-indexed.
Example 2:

Input: nums = [1,1,1,1]
Output: 6
Explanation: Each pair in the array are good.
Example 3:

Input: nums = [1,2,3]
Output: 0
 

Constraints:

1 <= nums.length <= 100
1 <= nums[i] <= 100
Accepted
295,466
Submissions
335,781


Solution: 


        var numIdenticalPairs = function(nums) {
            
            let hm = new Map();
            let goodPairs = 0;
            for(let i=0; i<nums.length; i++){
                if(hm.get(nums[i])){
                    goodPairs += hm.get(nums[i]);
                    hm.set(nums[i], hm.get(nums[i]) + 1);
                }else{
                    hm.set(nums[i], 1);
                }
            }
            
            return goodPairs;
        };