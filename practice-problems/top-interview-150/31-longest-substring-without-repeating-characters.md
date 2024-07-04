# 3. Longest Substring Without Repeating Characters

## Leetcode Problem
https://leetcode.com/problems/longest-substring-without-repeating-characters/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of finding the length of the longest substring without repeating characters using the `sliding window approach`, let's break down the problem and the solution step by step.

Given a string `s`, we need to find the length of the longest substring that contains no repeating characters.

### Example Explanation
##### Example 1:
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```
Example 2:
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
Example 3:
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
```
Note: The answer must be a substring, not a subsequence.

## Constraints
- 0 <= s.length <= 5 * 10^4
- s consists of English letters, digits, symbols, and spaces.

## Approach
The `sliding window technique` is ideal for this problem as it allows us to efficiently keep track of the current substring and adjust it as we encounter repeated characters.

### Steps
- Initialize Variables:
    - `start` to keep track of the beginning of the current substring.
    - `maxLength` to store the length of the longest substring found.
    - `charIndexMap` to store the last seen index of each character.
- Iterate through the string with an `end` pointer (end):
    - If the character at `s[end]` has been seen before and its index is greater than or equal to `start`, move the start pointer to `charIndexMap[s[end]] + 1`.
    - Update `charIndexMap` with the current index of `s[end]`.
    - Calculate the length of the current substring (`end - start + 1`) and update `maxLength` if this length is greater than `maxLength`.
- Return `maxLength` after the loop.

## Solution Code
```javascript
function lengthOfLongestSubstring(s) {
    const n = s.length;
    let maxLength = 0;
    let start = 0;
    const charIndexMap = new Map();

    for (let end = 0; end < n; end++) {
        const char = s[end];

        if (charIndexMap.has(char) && charIndexMap.get(char) >= start) {
            start = charIndexMap.get(char) + 1;
        }

        charIndexMap.set(char, end);
        maxLength = Math.max(maxLength, end - start + 1);
    }

    return maxLength;
}

// Example usage
console.log(lengthOfLongestSubstring("pwwwkekewp")) // Output: 4
console.log(lengthOfLongestSubstring("abcabcbb")); // Output: 3
console.log(lengthOfLongestSubstring("bbbbb")); // Output: 1
console.log(lengthOfLongestSubstring("pwwkew")); // Output: 3
```

## Explanation of the Code
### Initialization:
- `n` is the length of the string `s`.
- `maxLength` is initialized to 0.
- `start` is initialized to 0.
- `charIndexMap` is a map to keep track of the last seen index of each character.
### Iterate with end pointer:
- For each character at index end, check if it has been seen before and if its index is within the current window.
- If so, move the `start` pointer to the index right after the last seen index of the current character.
- Update the last seen index of the current character in charIndexMap.
- Calculate the length of the current substring (`end - start + 1`) and update `maxLength` if necessary.
### Return the result:
- After iterating through the entire string, `maxLength` holds the length of the longest substring without repeating characters.
- This approach efficiently finds the desired length with a time complexity of `O(n)`.

## Time Complexity
The time complexity of this approach is `O(n)`, where `n` is the length of the string. Each character is visited at most twice (once by the `end` pointer and once by the `start` pointer).
