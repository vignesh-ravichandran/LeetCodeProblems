Given the array nums, for each nums[i] find out how many numbers in the array are smaller than it. That is, for each nums[i] you have to count the number of valid j's such that j != i and nums[j] < nums[i].

Return the answer in an array.

 

Example 1:

Input: nums = [8,1,2,2,3]
Output: [4,0,1,1,3]
Explanation: 
For nums[0]=8 there exist four smaller numbers than it (1, 2, 2 and 3). 
For nums[1]=1 does not exist any smaller number than it.
For nums[2]=2 there exist one smaller number than it (1). 
For nums[3]=2 there exist one smaller number than it (1). 
For nums[4]=3 there exist three smaller numbers than it (1, 2 and 2).
Example 2:

Input: nums = [6,5,4,8]
Output: [2,1,0,3]
Example 3:

Input: nums = [7,7,7,7]
Output: [0,0,0,0]
 

Constraints:

2 <= nums.length <= 500
0 <= nums[i] <= 100


Solution 1: ( n log n )

        var smallerNumbersThanCurrent = function(nums) {
            
            let num = [...nums];
            
            num = num.sort((a,b)=>a-b);
            
            let mp = new Map();
            let t=0;
            for(let i=0; i<num.length; i++){
                if(!mp.get(num[i]) && mp.get(num[i]) != 0) mp.set(num[i], t);
                t++;
            }
            
            let result = [];
            
            for(let i=0; i<nums.length; i++){
                result.push(mp.get(nums[i]));
            }
            
            return result;
            
        };

Solution 2: ( n ) but constant k of 100 iterations

        var smallerNumbersThanCurrent = function(nums) {
            
            let num = new Array(101).fill(0);
            
        for(let i=0; i<nums.length; i++){
            num[nums[i]]++;
        }
            
            let mp = new Map();
            let sofar = 0;
            for(let i=0; i<num.length; i++){
                if(num[i] != 0){
                    mp.set(i, sofar)
                }
                sofar += num[i];
            }
            
            let result = [];
            
            for(let i=0; i<nums.length; i++){
                result.push(mp.get(nums[i]));
            }
            
            return result;
            
        };