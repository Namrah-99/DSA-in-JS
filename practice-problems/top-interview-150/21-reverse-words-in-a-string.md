# 151. Reverse Words in a String

## Leetcode Problem
https://leetcode.com/problems/reverse-words-in-a-string/description/?envType=study-plan-v2&envId=top-interview-150

## Solution Code
```javascript
var reverseWords = function(s) {
    return s.trim().split(/\s+/).reverse().join(' ');
};
// Example usage:
console.log(reverseWords("the sky is blue")); // Output: "blue is sky the"
console.log(reverseWords("  hello world  ")); // Output: "world hello"
console.log(reverseWords("a good   example")); // Output: "example good a"
```

## Edge Cases Handled:
- Strings with leading/trailing spaces.
- Strings with multiple spaces between words.
- Strings with different combinations of spaces and words.

## Complexity Analysis
- Time Complexity: `O(n)`, where n is the length of the string s. This is because we iterate over the string once to split and reverse the words.
- Space Complexity: `O(n)`, where n is the length of the string s in the worst case (if every character is a space). This is due to storing the array of words and the final output string.

