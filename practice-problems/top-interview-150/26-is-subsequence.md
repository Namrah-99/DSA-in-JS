# 392. Is Subsequence

## Leetcode Problem
https://leetcode.com/problems/is-subsequence/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
The approach used in this code is a `two-pointer technique in reverse order`. Here's how it works:
- **Iterate Backwards:** Start iterating through the string `t` from the end to the beginning.
- **Check Last Character:** If the current character in `t` matches the last character of `s`, remove the last character from `s`.
- **Check Subsequence:** After the iteration, if `s` is empty, it means all characters of `s` were found in `t` in the correct order, thus `s` is a subsequence of `t`.

## Solution Code
```javascript
var isSubsequence = function (s, t) {
    for (let i = t.length - 1; i >= 0; i--) {
        if (t[i] === s[s.length - 1]) {
            s = s.slice(0, -1)
        }
    }
    return s.length === 0 ? true : false
};

console.log(isSubsequence("abc", "ahbgdc")) // true
console.log(isSubsequence("axc", "ahbgdc")) // false
```

## Complexity Analysis

### Time Complexity:

- The loop runs `O(n)` times, where n is the length of t.
- Within each iteration, slicing s takes `O(m)` time in the worst case where m is the length of s.
- However, since slicing effectively decreases the size of s, it could be considered to amortize over the length of t.
- Therefore, the overall time complexity can be simplified to `O(n + m)`, where n is the length of t and m is the length of s.

### Space Complexity:
The space complexity is `O(1)` because no additional space proportional to the input size is used; only a few extra variables are utilized.
