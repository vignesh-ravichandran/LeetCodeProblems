A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

 

Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
Example 3:

Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
 

Constraints:

1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.


Tags: Easy, Palindrome 

Solution: 

    var isPalindrome = function(s) {
        let fs='';
        for(let i=0; i<s.length; i++){
            if((s[i] <= 'z' && s[i] >= 'a') || (s[i]>='A' && s[i]<= 'Z') || (s[i]>='0' && s[i]<= '9')){
                fs+= String.fromCharCode(s[i].charCodeAt(0) | 32);
            }
        }
        let n = fs.length;
        for(let i=0; i<n/2; i++){
            if(fs[i] != fs[n-1-i]) return false;
        }
        
        return true;
        
    };