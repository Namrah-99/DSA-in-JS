# 242. Valid Anagram

## Leetcode Problem
https://leetcode.com/problems/valid-anagram/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Understanding
Given two strings `s` and `t`, we need to check if `t` is an anagram of `s`. An anagram means that `t` can be formed by rearranging the characters of `s` such that both strings contain exactly the same characters with the same frequencies.

## Constraints and Requirements
- `1≤length` of `s`,length of `t≤5×10^4`
- `𝑠` and `t` consist of lowercase English letters.

## Approaches
1. Using an Array as Buckets
```javascript
var isAnagram = function(s, t) {
    if (t.length !== s.length) return false;
    const counts = [];
    for (let c of s) {
        let i = c.charCodeAt(0) - 'a'.charCodeAt(0);
        counts[i] = (counts[i] || 0) + 1;
    }
    for (let c of t) {
        let i = c.charCodeAt(0) - 'a'.charCodeAt(0);
        if (!counts[i]) return false;
        counts[i]--;
    }
    return true;
};
```

2. Using a Map
```javascript
var isAnagram = function(s, t) {
    if (t.length !== s.length) return false;
    const counts = {};
    for (let c of s) {
        counts[c] = (counts[c] || 0) + 1;
    }
    for (let c of t) {
        if (!counts[c]) return false;
        counts[c]--;
    }
    return true;
};
```

## Complexity Analysis

### Time Complexity
- Both approaches have a time complexity of `O(n)`, where `n` is the length of the strings `s` and `t`.
- This complexity arises because each string is processed exactly twice: once to populate the counts (or buckets) and once to check and decrement them.

### Space Complexity
- Using an Array as Buckets: This approach uses a fixed-size array (counts) of size 26 (assuming only lowercase English letters), which gives it a space complexity of `O(1)` (constant space), as it doesn't depend on the input size.

### Using a Map: 
This approach uses a map (`counts`) that grows with the number of unique characters in `s`. In the worst case, if all characters are unique, the space complexity could be `O(n)`, where `n` is the number of unique characters in `s`.

### Adaptation to Unicode Characters
If the inputs could contain Unicode characters, you would need to extend the map approach because Unicode characters can have a much larger range than just lowercase English letters. JavaScript's Map data structure would be suitable for handling Unicode characters efficiently since Map can use any JavaScript value (including objects and primitives) as keys.

## Conclusion
Both the array as buckets and map approaches are effective for determining if two strings are anagrams, with the array approach being slightly more space-efficient assuming only lowercase English letters. The time complexity of `O(n)` ensures that the solution is efficient even for the upper limits of input sizes specified in the problem constraints.
