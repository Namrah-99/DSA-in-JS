# 290. Word Pattern

## Leetcode Problem
https://leetcode.com/problems/word-pattern/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to determine if a given string `s` follows the same pattern as a given pattern string `pattern`. To follow the same pattern, there must be a one-to-one correspondence (bijection) between each character in the pattern and each word in the string s. This means:

- Each character in the pattern maps to a unique word in s.
- Each word in s maps to a unique character in the pattern.

### Examples
#### Example 1:
```
Input: pattern = "abba", s = "dog cat cat dog"
Output: true
```
- Explanation: 'a' maps to "dog" and 'b' maps to "cat". The pattern "abba" is followed.

#### Example 2:
```
Input: pattern = "abba", s = "dog cat cat fish"
Output: false
```
- Explanation: 'a' maps to "dog" but 'b' does not consistently map to "cat" because 'b' should map to "cat" in both occurrences but maps to "fish" in the last word.

#### Example 3:
```
Input: pattern = "aaaa", s = "dog cat cat dog"
Output: false
```
- Explanation: All characters in the pattern are 'a', but the words in s are not all the same.

## Constraints
- `1 <= pattern.length <= 300`
- `pattern` contains only lowercase English letters.
- `1 <= s.length <= 3000`
- `s` contains only lowercase English letters and spaces.
- `s` does not contain any leading or trailing spaces.
- All words in `s` are separated by a single space.

## Approach
### Splitting the String:
- The string `s` is split into an array of words `sArray` using the split method with a regular expression that matches one or more spaces.
### Length Check:
- If the length of `pattern` is not equal to the length of `sArray`, return false immediately. This ensures that there is a one-to-one correspondence between characters in pattern and words in sArray.
### Unique Element Check:
- If the number of unique characters in `pattern` is not equal to the number of unique words in `sArray`, return false. This ensures that each character in `pattern` maps to a unique word in `s`.
### Mapping Characters to Words:
- Use a Map `mapPS` to store the mapping from characters in `pattern` to words in `sArray`.
- Iterate through the characters in `pattern` and the corresponding words in `sArray`.
- If the character `charP` is already in the map and does not map to the current word `charS`, return `false`.
- Otherwise, add the mapping from `charP` to `charS`.
### Return True:
- If all checks pass, return `true`, indicating that the string `s` follows the `pattern`.

## Solution Code
```javascript
var wordPattern = function (pattern, s) {
    let sArray = s.split(/\s+/); // Split the string into words by spaces

    if (pattern.length !== sArray.length) return false;
    if (new Set(pattern).size !== new Set(sArray).size) return false;

    let mapPS = new Map(); // Map to store pattern to string mapping

    for (let i = 0; i < pattern.length; i++) {
        let charS = sArray[i], charP = pattern[i];

        if (mapPS.has(charP) && mapPS.get(charP) !== charS) {
            return false;
        }

        mapPS.set(charP, charS);
    }

    return true;
};

// Example usage:
console.log(wordPattern("abba", "dog constructor constructor dog")); // Output: true
console.log(wordPattern("abba", "dog dog dog dog")); // Output: false
console.log(wordPattern("abba", "dog cat cat dog")); // Output: true
console.log(wordPattern("abba", "dog cat cat fish")); // Output: false
console.log(wordPattern("aaaa", "dog cat cat dog")); // Output: false
```

## Complexity Analysis
### Time Complexity:
- Splitting the string `s` into an array of words `sArray` takes `O(n)` time, where `n` is the length of `s`.
- Checking the length of `pattern` and `sArray` is `O(1)`.
- Creating sets to check the number of unique characters and words takes `O(m)`, where `m` is the length of pattern.
- Iterating through pattern and mapping characters to words takes `O(m)`.
- Thus, the total time complexity is `O(n+m)`, which simplifies to `O(n)` since `m` is proportional to `n`.

### Space Complexity:
- Storing sArray takes `O(k)`, where `k` is the number of words in `sArray`.
- The map `mapPS` uses `O(m)` space.
- Sets for unique elements take `O(m+k)` space.
- Thus, the total space complexity is `O(m+k)`, which simplifies to `O(n)` since `m` and `k` are proportional to `n`.

### Summary:
- The provided solution uses a `hash table approach` to map characters in `pattern` to words in `sArray`. The time complexity of the solution is `O(n)` and the space complexity is `O(n)`, where `n` is the length of the string `s`.
