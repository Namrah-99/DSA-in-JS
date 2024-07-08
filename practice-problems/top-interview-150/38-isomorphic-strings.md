# 205. Isomorphic Strings

## LeetCode Problem
https://leetcode.com/problems/isomorphic-strings/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to determine if two strings `s` and `t` are isomorphic. Two strings are considered isomorphic if the characters in `s` can be replaced to get `t`. This implies that each character in `s` must map to a unique character in `t` while preserving the order of characters. No two characters in `s` may map to the same character in `t`, but a character can map to itself.

### Examples
#### Example 1:
```
Input: s = "egg", t = "add"
Output: true
Explanation: 'e' maps to 'a' and 'g' maps to 'd'. Both mappings are unique and preserve the order.
```
#### Example 2:
```
Input: s = "foo", t = "bar"
Output: false
Explanation: 'o' cannot map to both 'a' and 'r'.
```
#### Example 3:
```
Input: s = "paper", t = "title"
Output: true
Explanation: 'p' maps to 't', 'a' maps to 'i', 'p' (repeated) maps to 't', 'e' maps to 'l', and 'r' maps to 'e'.
```
## Constraints
- 1 <= s.length <= 5 * 10^4
- t.length == s.length
- s and t consist of any valid ASCII character.

## Approach
To solve this problem efficiently, we can use two hash tables (or dictionaries) to track the mappings:

- `mapST` to map characters from `s` to `t`.
- `mapTS` to map characters from `t` to `s`.

### For each character in the strings:
- Check if the character from `s` has been mapped to the corresponding character in `t`.
- Check if the character from `t` has been mapped to the corresponding character in `s`.
- If any of the mappings violate the uniqueness or order, return `false`.

## Solution Code
```javascript
var isIsomorphic = function (s, t) {
    if (t.length !== s.length) return false

    let mapST = {}, mapTS = {};

    for (let i = 0; i < s.length; i++) {
        let charS = s[i], charT = t[i];

        if (mapST[charS] && mapST[charS] !== charT) {
            return false
        }

        if (mapTS[charT] && mapTS[charT] !== charS) {
            return false
        }

        mapST[charS] = charT;
        mapTS[charT] = charS
    }
    return true
};
// Example usage:
console.log(isIsomorphic("egg", "add")); // Output: true
console.log(isIsomorphic("foo", "bar")); // Output: false
console.log(isIsomorphic("paper", "title")); // Output: true
```

## Complexity Analysis
### Time Complexity: 
- `O(n)`, where `n` is the length of the strings `s` and `t`. This is because we iterate through each character in the strings once.
### Space Complexity: 
- `O(n)`, for storing the mappings in the hash tables.
