# 1. Two Sum

## Leetcode Problem
https://leetcode.com/problems/two-sum/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
To solve the problem of finding two numbers in an array `nums` that add up to a `target` integer using a `hash map approach with O(n) time complexity`, follow these steps:

1. **Hash Map Usage:** Utilize a hash map to store the numbers encountered so far along with their indices. This allows for efficient look-up to check if the complement `(target - current number)` of the current number exists in the hash map.
2. **Algorithm Steps:**
    - Initialize an empty hash map `map` to store numbers and their indices.
    - Iterate through each number `num` in the array `nums`.
    - Calculate the `complement` as `target - num`.
    - Check if `complement` exists in the hash map:
        - If it does, return the indices `[map.get(complement), currentIndex]`.
        - If it doesn't, store `num` in the hash map with its index.
- **Output:** Since there is exactly one valid solution, the algorithm will always find and return the indices of the two numbers that add up to the `target`.

## Solution Code
```javascript
var twoSum = function(nums, target) {
    const map = new Map();
    
    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        const complement = target - num;
        
        if (map.has(complement)) {
            return [map.get(complement), i];
        }
        
        map.set(num, i);
    }
    
    // It is guaranteed that there is exactly one solution,
    // so we don't need to handle the case where no solution is found.
};
// Example usage:
console.log(twoSum([2,7,11,15], 9)); // Output: [0,1]
console.log(twoSum([3,2,4], target = 6)); // Output: [1,2]
```

## Complexity Analysis
### Time Complexity
- The time complexity of the solution is `O(n)`, where `n` is the length of the array nums.
- This is because each lookup and insertion operation in a hash map is average `O(1)`, making the overall complexity linear with respect to the size of the input array.

### Space Complexity
Utilizing a hash map to find two numbers adding up to a target integer, is `O(n)` due to potential storage of all nums elements if no pair is found. The hash map stores each number with its index, while auxiliary variables like `num` and `complement` use constant extra space `O(1)`, ensuring efficient handling of large inputs.
