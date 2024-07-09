# 49. Group Anagrams

## Leetcode Problem
https://leetcode.com/problems/group-anagrams/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
To achieve a time complexity of `O(n)` without relying on sorting each string (which would involve `O(klogk)` time complexity per string), we can use a different approach involving character counting.

### Explanation
Instead of sorting each string, we can use a `hash map` where the key is a tuple representing the count of each character in the string. Anagrams will have identical tuples of character counts.

### Algorithm Steps
1. **Create a Hash Map:** Initialize an empty hash map (`map`) where the keys will be tuples and the values will be arrays of strings.
2. **Iterate Through Strings:**
    - For each string in `strs`, initialize an array `count` of size 26 (assuming lowercase English letters) to zero.
    - Count the frequency of each character in the string and store it in the `count` array.
    - Convert the `count` array to a tuple and use this tuple as a key in the hash map.
3. **Group Anagrams:**
    - If the tuple already exists as a key in the hash map, append the original string to the corresponding array.
    - If the tuple does not exist, create a new entry in the hash map with the tuple as the key and an array containing the current string.
4. **Output:** After iterating through all strings, return the values of the hash map as the grouped lists of anagrams.

## Solution Code
```javascript
var groupAnagrams = function(strs) {
    const map = new Map();
    
    for (let str of strs) {
        const count = Array(26).fill(0); // Array to count occurrences of each character
        
        // Count frequencies of characters in the current string
        for (let char of str) {
            count[char.charCodeAt(0) - 'a'.charCodeAt(0)]++;
        }
        
        // Create a key (tuple) for the hash map from the count array
        const key = count.toString();
        
        // If key exists, add current string to the corresponding array; otherwise, create a new array
        if (map.has(key)) {
            map.get(key).push(str);
        } else {
            map.set(key, [str]);
        }
    }
    
    // Return all values from the map (list of lists of anagrams)
    return Array.from(map.values());
};

// Example usage:
console.log(groupAnagrams(["eat","tea","tan","ate","nat","bat"])); // Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
console.log(groupAnagrams(["a"])); // Output: [["a"]]
```

## Explanation of the Code
- **Count Array:** `count` is an array of size 26 initialized with zeros, where each index corresponds to a character ('a' to 'z').
- **Counting Characters:** For each string `str`, iterate through its characters and increment the corresponding index in the `count` array.
- **Key Creation:** Convert the `count` array to a string `(count.toString())` to use as a key in the hash map.
- **Grouping:** Check if the key exists in the hash map. If it does, append the current string to the array associated with that key. If not, create a new array with the current string as its first element.
- **Output:** Convert and return all values from the hash map as the grouped lists of anagrams.

## Complexity Analysis

### Time Complexity
- **Character Counting:** Counting characters in each string is `O(k)`, where k is the length of the string.
- **Hash Map Operations:** Inserting and retrieving from a hash map on average is `O(1)`.
- **Iterating Through Strings:** Since we iterate through each string exactly once, the overall time complexity is `O(n)`, where `n` is the number of strings in `strs`.

### Space Complexity
- **Hash Map (map):** Used to store anagram groups; worst-case space complexity is `O(n)`, where `n` is the number of strings in `strs`.
- **Count Array (count):** Counts character occurrences in each string, fixed size of 26 (assuming lowercase English letters), thus `O(1)` space complexity per array.
- **Overall Space Complexity:** Besides strs, dominated by map, leading to `O(n)` space complexity.
- **Conclusion:** The solution efficiently handles anagrams in `O(n)` time and `O(n)` space, ideal for large inputs within memory constraints.

This approach ensures that we achieve the desired `O(n)` time complexity while efficiently grouping anagrams together using character counts and a hash map. It's optimal for the given problem constraints and efficiently handles large inputs.
