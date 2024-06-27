# 763. Partition Labels

## Leetcode Problem
https://leetcode.com/problems/partition-labels/description/

## Problem Statement
Given a string `s`, we want to partition the string into as many parts as possible so that each letter appears in at most one part. The concatenation of all parts in order should yield the original string `s`. We need to return a list of integers representing the size of these parts.
```
Example
Input: s = "ababcbacadefegdehijhklij"
Output: [9, 7, 8]

Explanation: The partitions are "ababcbaca", "defegde", "hijhklij".
```

## Approach
- Two Pointer Approach
    - Track the Last Occurrence of Each Character:
        - Create a map (`lastOccurrence`) to store the last index of each character in the string. This allows us to know the furthest point each character must be included in a partition.
        - For the string "ababcbacadefegdehijhklij", the dictionary would look like this:
          ```javascript
          {
            a: 8,
            b: 5,
            c: 7,
            d: 14,
            e: 15,
            f: 11,
            g: 13,
            h: 19,
            i: 22,
            j: 23,
            k: 20,
            l: 21
          }
          ```
    - Iterate Through the String with Two Pointers:
        - Use `start` to mark the beginning of the current partition.
        - Use end to mark the `end` of the current partition.
        - As we iterate through the string, we update `end` to be the maximum of its current value and the last occurrence of the current character. This ensures that the current partition includes all occurrences of characters seen so far.
    - Identify Partitions:
        - When the current index `i` reaches `end`, it means we have found a complete partition. We calculate the size of this partition, add it to the result list, and move `start` to `i + 1` to begin the next partition.
- Greedy Approach
    - The Greedy approach is evident in the way we extend the `end` pointer. By always choosing to extend `end` to the furthest necessary point for any character encountered, we ensure that we make the largest possible partitions without splitting any characters across partitions.
    - This greedy choice guarantees that once we decide to close a partition (when `i` equals `end`), we have made the largest possible partition, allowing us to make the next partition independently and optimally.

## Solution Code
```javascript
var partitionLabels = function(s) {
    // store the last index of each character in the string
    // track the last occurrence of each character
    let lastOccurences = {};
    for(let i=0;i<s.length;i++){
        lastOccurences[s[i]]=i;
    }

    // initialize variables for two-pointer technique
    let result=[]; let start = 0, end = 0;
    // iterate through the string
    for(let i=0;i<s.length;i++){
        // update the end pointer to the furthest last occurrence of the current character
        end = Math.max(end,lastOccurences[s[i]]);
        // when we reach the end of the current partition
        if(i===end){
            // calculate the size of the partition
            result.push(end-start+1);
            // move start to the next character after the current partition
            start = i + 1;
        }
    }
    return result;
};

console.log(partitionLabels("ababcbacadefegdehijhklij"))
```

## Explanation of Combined Approach
#### Initialization:
- `lastOccurrence` maps each character to its last position in the string.
- `start` and `end` pointers are initialized to mark the beginning and end of the first partition.
#### Iterating Through the String:
- For each character, update `end` to be the maximum of its current value and the last occurrence of the character (`lastOccurrence[s[i]]`). This ensures all necessary characters are included in the current partition.
#### Greedy Decision Making:
- By extending `end` to the furthest necessary point, we ensure that we don't split any characters across partitions.
- Once `i` reaches `end`, we know we have included all necessary characters for the current partition, so we add the partition size to `result` and move `start` to `i + 1` for the next partition.

## Conclusion
- Two Pointer Approach: Used to maintain and update the start and end of the current partition dynamically.
- Greedy Approach: Ensures that we always make the largest possible partition by extending end to the furthest point required by any character encountered.

## Time Complexity
The combination of these approaches results in an efficient solution with a time complexity of `O(n)`, where n is the length of the string. This efficiency is crucial for handling the upper constraint of the problem.
