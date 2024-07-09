# 128. Longest Consecutive Sequence

## Problem Explanation
To solve the problem of finding the length of the longest consecutive elements sequence in an unsorted array nums using a hash table approach with `O(n)` time complexity in JavaScript, follow these steps:

Given an array `nums`, we need to find the longest sequence of consecutive integers in the array and return the length of that sequence.

## Approach
- **Hash Set Usage:** Utilize a hash set (`numSet`) to store each unique number in `nums` for efficient look-up.
- **Algorithm Steps:**
    - Initialize a hash set `numSet` and add all elements of `nums` to it.
    - Iterate through each number in `nums`. For each number:
        - Check if it is the start of a new sequence (i.e., the previous number `num - 1` does not exist in `numSet`).
        - If it is the start, continue counting consecutive numbers `(num, num + 1, num + 2, ...)` until a number is not found in `numSet`.
        - Update the maximum length of consecutive sequence found.
- **Output:** Return the maximum length of consecutive elements sequence found.

## Solution Code
```javascript
var longestConsecutive = function(nums) {
    const numSet = new Set(nums);
    let maxLength = 0;
    
    for (let num of numSet) {
        if (!numSet.has(num - 1)) { // Only start counting from the smallest number in the sequence
            let currentLength = 1;
            let currentNum = num + 1;
            
            while (numSet.has(currentNum)) {
                currentLength++;
                currentNum++;
            }
            
            maxLength = Math.max(maxLength, currentLength);
        }
    }
    
    return maxLength;
};

// Example usage:
console.log(longestConsecutive([0,3,7,2,5,8,4,6,0,1])); // Output: 9
console.log(longestConsecutive([100,4,200,1,3,2])); // Output: 4
```

## Complexity Analysis
### Time Complexity:
- Inserting all elements into the hash set numSet takes `O(n)` time, where `n` is the number of elements in `nums`.
- Iterating through each element and counting the consecutive sequence takes `O(n)` time in the worst case.
- Therefore, the overall time complexity is `O(n)`.
### Space Complexity:
- The space complexity is `O(n)` due to the hash set numSet potentially storing all elements of `nums`.
- Auxiliary space used by other variables (like `currentLength` and `currentNum`) is constant `O(1)` space.
