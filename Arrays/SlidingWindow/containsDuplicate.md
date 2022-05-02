Given an integer array nums and an integer k, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.

 

Example 1:

Input: nums = [1,2,3,1], k = 3
Output: true
Example 2:

Input: nums = [1,0,1,1], k = 1
Output: true
Example 3:

Input: nums = [1,2,3,1,2,3], k = 2
Output: false
 

Constraints:

1 <= nums.length <= 105
-109 <= nums[i] <= 109
0 <= k <= 105


Solution: 


        var containsNearbyDuplicate = function(nums, k) {
            
            let hm = new Map();
            
            for(let i=0; i<nums.length; i++){
            // console.log(hm.get(nums[i]) > 1);
                if(hm.get(nums[i]) > 0 && nums[i] <= k){
                    return true;
                }else if(hm.get(nums[i])){
                    hm.set(nums[i],hm.get(nums[i]) + 1);
                }else{
                    hm.set(nums[i], 1);
                }
            }
            
        // console.log(hm);
            
            return false;
            
        };