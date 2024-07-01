# 28. Find the Index of the First Occurrence in a String

## Leetcode Problem
https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/?envType=study-plan-v2&envId=top-interview-150

## Solution Code
```javascript
var strStr = function(haystack, needle) {
    return haystack.indexOf(needle)
};

// Example usage:
console.log('output: ',strStr("sadbutsad","sad")); // Output: 0
console.log('output: ',strStr("leetcode","leeto")); // Output: -1
```

## Complexity Analysis
- Time Complexity: indexOf in JavaScript typically operates with a time complexity of `O(m * n)`, where:
    - `m` is the length of the haystack string.
    - `n` is the length of the needle string.
This complexity arises because `indexOf` needs to potentially check each character in the `haystack` against the characters in `needle`. In the worst case, `indexOf` may need to backtrack and check characters multiple times, leading to this quadratic time complexity.

Space Complexity: `O(1)`. The function uses a constant amount of extra space, regardless of the inputs, since it does not use additional data structures that grow with input size.
