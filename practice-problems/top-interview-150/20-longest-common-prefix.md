# 14. Longest Common Prefix

## Leetcode Problem
https://leetcode.com/problems/longest-common-prefix/description/?envType=study-plan-v2&envId=top-interview-150

## My Approach
```javascript
var longestCommonPrefix = function(strs) {
    let minSubstr = strs[0];
    for(let s of strs){
        if(s.length<minSubstr.length){
            minSubstr=s;
        }
    }
    for(let i=0;i<strs.length;i++){
        while(!strs[i].startsWith(minSubstr)){
            minSubstr= minSubstr.slice(0,-1)
        }
    }
    return minSubstr
};
// Example usage:
console.log(longestCommonPrefix(["flower","flow","flight"])); // Output: 'fl'
console.log(longestCommonPrefix(["dog","racecar","car"])); // Output: ''
```
#### Complexity Analysis
- Time Complexity: O(n×m), where n is the number of strings in the array and m is the length of the shortest string.
- Space Complexity: O(1)

## Horizontal Scanning Approach

To make the longestCommonPrefix function more efficient, we can use a horizontal scanning approach. Instead of finding the minimum substring and then repeatedly slicing it, we compare each string with a prefix to update the longest common prefix.

```javascript
var longestCommonPrefix = function(strs) {
    if (!strs.length) return "";

    let prefix = strs[0]; // Start with the first string as the initial prefix

    for (let i = 1; i < strs.length; i++) {
        // Compare the current prefix with each string in the array
        while (strs[i].indexOf(prefix) !== 0) {
            // Reduce the prefix until it's a common prefix for the current string
            prefix = prefix.slice(0, -1);
            if (prefix === "") return ""; // Early exit if there's no common prefix
        }
    }
    return prefix;
};

// Example usage:
console.log(longestCommonPrefix(["flower", "flow", "flight"])); // Output: 'fl'
console.log(longestCommonPrefix(["dog", "racecar", "car"])); // Output: ''
```

#### Complexity Analysis

##### Time Complexity:
- Let n be the number of strings in the array.
- Let m be the length of the shortest string in the array.
- In the worst case, we compare each character of the prefix with every string. The first string comparison takes O(m), the second takes O(m), and so on, up to O(m×n).
Therefore, the overall time complexity is `O(n×m)`.

##### Space Complexity:
The space complexity is `O(1)` because we are using a fixed amount of extra space regardless of the input size. The prefix variable does not count as extra space because it references the input strings.

##### Summary:
- Time Complexity: O(n×m)
- Space Complexity: O(1)
