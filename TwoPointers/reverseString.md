Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array in-place with O(1) extra memory.

 

Example 1:

Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
Example 2:

Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
 

Constraints:

1 <= s.length <= 105
s[i] is a printable ascii character.
Accepted
1,593,565
Submissions
2,126,278


Solution: 


        var reverseString = function(s) {
            let n = s.length-1;
            for(let i=0; i< parseInt(s.length/2); i++){
                let j = n - i;
                let temp = s[i];
                s[i] = s[j];
                s[j] = temp;
            }
            
            return s;
            
        };