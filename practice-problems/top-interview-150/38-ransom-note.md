# 383. Ransom Note

## Leetcode Problem
https://leetcode.com/problems/ransom-note/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to determine if a string ransomNote can be constructed using the letters from another string magazine. Each letter from magazine can only be used once. The task is to return true if the ransom note can be constructed and false otherwise.

## Examples

### Example 1:
```
Input: ransomNote = "a", magazine = "b"
Output: false
```
- Explanation: The letter "a" is not present in magazine.

### Example 2:
```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```
- Explanation: There are not enough "a"s in magazine to form ransomNote.

### Example 3:
```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```
- Explanation: There are enough "a"s in magazine to form ransomNote.

## Constraints
- 1 <= ransomNote.length, magazine.length <= 10^5
- Both ransomNote and magazine consist of lowercase English letters.

## Approach
The approach involves using a `hash map (or dictionary)` to count the occurrences of each character in the `magazine` and then checking if the `ransomNote` can be constructed using those counts.

### Steps
#### Count Characters in Magazine:
- Use a dictionary to count the occurrences of each character in `magazine`.
#### Check Characters in Ransom Note:
- For each character in `ransomNote`, check if it exists in the dictionary with a count greater than or equal to the required count.
- If any character is missing or has an insufficient count, return `false`.
- If all characters are sufficiently available, return `true`.

## Solution Code
```javascript
function canConstruct(ransomNote, magazine) {
    let charCount = {};
    
    // Count characters in magazine
    for (let char of magazine) {
        if (!charCount[char]) {
            charCount[char] = 0;
        }
        charCount[char]++;
    }
    
    // Check characters in ransomNote
    for (let char of ransomNote) {
        if (!charCount[char] || charCount[char] <= 0) {
            return false;
        }
        charCount[char]--;
    }
    
    return true;
}

// Example usage:
console.log(canConstruct("a", "b")); // Output: false
console.log(canConstruct("aa", "ab")); // Output: false
console.log(canConstruct("aa", "aab")); // Output: true
```

## Complexity Analysis

###  Time Complexity:
`O(n)` , where `𝑛` is the length of the magazine. This is because we process each character in the magazine to build the hash map and each character in the ransomNote to check against the hash map.

### Space Complexity:
`O(1)`, since the hash map will store at most 26 key-value pairs (for each lowercase English letter).
