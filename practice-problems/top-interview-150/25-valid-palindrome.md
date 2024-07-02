# 125. Valid Palindrome

## Leetcode Problem
https://leetcode.com/problems/valid-palindrome/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
The approach used in the provided solution is a `two-pointer technique` combined with string preprocessing:
- **Preprocessing:** The string is transformed by removing all non-alphanumeric characters and converting it to lowercase.
- **Two-pointer technique:** Two pointers are initialized at the beginning and end of the processed string.
- **Comparison:** Characters at the pointers are compared moving towards the center. If any characters do not match, the function returns false.
- **Palindrome Check:** If all characters match, the function returns true, indicating the string is a palindrome.
This approach ensures an efficient `O(n)` time complexity for checking if a string is a palindrome.

## Solution Code
```javascript
var isPalindrome = function(s) {
   s=s.replace(/[^a-zA-Z0-9]/g,'').toLowerCase();
   let mid = Math.floor(s.length/2);
   let midPoint = s.length % 2 === 0 ? mid-1 : mid;
   let left=0,right=s.length-1;
   while(left<right){
       if(s[left]!==s[right]){
           return false;
       }
       left++;
       right--;
   }
   
   return true;
};

console.log(isPalindrome("A man, a plan, a canal: Panama")) // true
console.log(isPalindrome("race a car")) // false
console.log(isPalindrome(" ")) // true
```

## Complexity Analysis
#### Time Complexity:
The overall time complexity is `O(n)` because:
- The replacement and lowercase conversion is `O(n)`.
- The palindrome check using the two-pointer technique is `O(n)`.
#### Space Complexity:
The space complexity is `O(n)` due to the additional string created after removing non-alphanumeric characters and converting to lowercase.
