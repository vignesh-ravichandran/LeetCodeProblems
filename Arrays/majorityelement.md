Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

 

Example 1:

Input: nums = [3,2,3]
Output: 3
Example 2:

Input: nums = [2,2,1,1,1,2,2]
Output: 2
 

Constraints:

n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109
 

Follow-up: Could you solve the problem in linear time and in O(1) space?


Tags: Easy, Moores voting algorithm

Solution: 

    var majorityElement = function(nums) {
        let me = null;
        let f = 0;
        
        for(let i=0; i<nums.length; i++){
            if(me==null){
                me = nums[i];
                f = 1;
            }else if(me == nums[i]){
                f++;
            }else{
                f--;
                if(f==0){
                    me = null;
                }
            }
        }
        
        return me;
    };