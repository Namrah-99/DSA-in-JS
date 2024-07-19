# 387. First Unique Character in a String

## Leetcode Problem 
https://leetcode.com/problems/first-unique-character-in-a-string/description/

To solve the problem of finding the first non-repeating character in a string s with a time complexity of `O(n)` and space complexity of `O(1)`:

## Edge Cases Handled
- Empty String (`s.length == 0`): The code correctly returns `-1`.
- All Characters Repeated (`s = "aabbcc"`): The code correctly returns `-1`.
- All Unique Characters (`s = "abcdef"`): The code correctly returns `0`.

## Approach 01: Array Counting Approach

- Directly maps characters to array indices based on their ASCII values.
- May be slightly faster in practice due to simpler operations (array access vs. hashmap operations). 

```javascript
function firstUniqChar(s) {
    if (!s || s.length === 0) return -1;
    
    // Step 1: Count frequencies of each character
    const count = new Array(26).fill(0); // Since only lowercase English letters
    
    for (let i = 0; i < s.length; i++) {
        count[s.charCodeAt(i) - 'a'.charCodeAt(0)]++
    }
    
    // Step 2: Find the first non-repeating character
    for (let i = 0; i < s.length; i++) {
        if (count[s.charCodeAt(i) - 'a'.charCodeAt(0)] === 1) {
            return i
        }
    }
    
    return -1; // No non-repeating character found
}
console.log(firstUniqChar("leetcode"))
console.log(firstUniqChar("loveleetcode"))
console.log(firstUniqChar("aabb"))
```
### Complexity Analysis:
#### Time Complexity:
  - `O(n)` where `n` is the length of the string `s`.
  - This is because we make two passes over the string (`s`): one to count frequencies and another to find the first non-repeating character. Both passes are `O(n)`.
#### Space Complexity:
  - `O(1)` because the size of the count array (26 elements) does not depend on the input size `n`. It is constant and thus `O(1)` space complexity.

## Approach 02: HashMap Approach

- May be more intuitive for those familiar with using hashmaps.
- Handles any Unicode character (not just lowercase English letters).

```javascript
var firstUniqChar = function(s) {
    let mp = {};

    for (let a of s) {
        mp[a] = (mp[a] || 0) + 1;
    }

    for (let i = 0; i < s.length; i++) {
        if (mp[s[i]] === 1) {
            return i;
        }
    }

    return -1;
};
```

### Complexity Analysis

#### Time Complexity: 
The dominant operation is the loop through the string `s`, both for building the frequency map and for finding the first non-repeating character. Hence, the overall time complexity is `O(n)`, where `n` is the length of the string `s`.

#### Space Complexity: 
The space complexity is `O(1)` because the extra space used is constant and independent of the size of the input string `s`.
