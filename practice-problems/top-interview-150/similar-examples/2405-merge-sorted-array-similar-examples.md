# 2405. Optimal Partition of String

## Leetcode Problem
https://leetcode.com/problems/optimal-partition-of-string/description/

## Problem Statement
Given a string s, partition the string into one or more substrings such that the characters in each substring are unique (i.e., no letter appears in a single substring more than once). Return the minimum number of substrings in such a partition.
```
Example
Input: s = "abacaba"

Output: 4
```
Explanation: Two possible partitions are ("a","ba","cab","a") and ("ab","a","ca","ba"). Both result in 4 substrings, which is the minimum number required.
```
Input: s = "ssssss"

Output: 6
```
Explanation: The only valid partition is ("s","s","s","s","s","s"), resulting in 6 substrings.

## Approach
To solve the problem of partitioning a string such that each substring has unique characters and returning the minimum number of substrings required, we can use a `greedy approach`. This approach involves iterating through the string and partitioning it whenever we encounter a duplicate character within the current substring. 

#### 1. Initialize variables:
  - `partitions` to count the number of partitions.
  - `seen` as a set to keep track of characters in the current substring.

#### 2. Iterate through the string:
  - For each character in the string, check if it is already in the `seen` set.
  - If it is, it means we need to start a new partition, so increment the `partitions` count, and reset the `seen` set.
  - Add the current character to the `seen` set.
#### 3. Edge Cases:
  - If the string is empty or has only one character, it will result in one partition.
- All characters in the string being the same will result in each character being in its own partition.

## Solution Code
```javascript
var partitionString = function(s) {
    let partitions = 1; // Start with at least one partition
    let seen = new Set();

    // Iterate thru each character of str
    for (let char of s) {
        // If the character is already in the current partition, start a new partition
        if (seen.has(char)) {
            partitions++;
            seen.clear();
        }
        // Add the character to the current partition's set
        seen.add(char);
    }
    // Return minimum no. of substrings 
    return partitions;
};

console.log(partitionString("abacaba"));
console.log(partitionString("ssssss"))
```

## Code Explanation
#### Initialization:
  - `partitions` is initialized to 1 because there will be at least one partition.
  - `seen` is an empty set used to track characters in the current partition.
#### Iteration:
  - For each character in the string, check if it is already in the `seen` set.
  - If it is, increment the `partitions` counter and clear the `seen` set, indicating the start of a new partition.
  - Add the current character to the `seen` set.
#### Result:
  - The value of `partitions` at the end of the iteration gives the minimum number of substrings required where each substring has unique characters.

This solution efficiently partitions the string with a linear time complexity, making it suitable for large inputs up to the constraint limit.

## Time Complexity
The time complexity is `O(n)`, where n is the length of the string. This is because we are iterating through the string once and performing constant time operations for each character.
