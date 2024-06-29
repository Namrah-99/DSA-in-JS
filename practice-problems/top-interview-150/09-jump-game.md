# 55. Jump Game

## Leetcode Problem
https://leetcode.com/problems/jump-game/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to determine if you can reach the last index of an array starting from the first index, where each element in the array represents the maximum jump length at that position. You need to return true if you can reach the last index, and false otherwise.

Example 1
```
Input: nums = [2,3,1,1,4]
Output: true
Explanation:
- Start at index 0, where the value is 2, so you can jump to index 1 or 2.
- From index 1, where the value is 3, you can jump to index 2, 3, or 4.
- Jump to index 4, which is the last index, so the output is true.
```
Example 2
```
Input: nums = [3,2,1,0,4]
Output: false
Explanation:
- Start at index 0, where the value is 3, so you can jump to index 1, 2, or 3.
- From index 1, where the value is 2, you can jump to index 2 or 3.
- From index 2, where the value is 1, you can jump to index 3.
- From index 3, where the value is 0, you cannot jump to any further index.
- Since you cannot reach the last index (4), the output is false.
```
Constraints
- 1 <= nums.length <= 10^4
- 0 <= nums[i] <= 10^5

## Approach
To solve this problem efficiently, we can use a `greedy approach`. The key is to keep track of the furthest index we can reach as we iterate through the array. If at any point, the current index is beyond the furthest index we can reach, then it is impossible to reach the last index.

- Initialize a variable `maxReach` to 0, which keeps track of the maximum index we can reach so far.
- Iterate through the array using a for loop.
- At each index `i`, if `i` is greater than `maxReach`, it means we can't reach this index, so return `false`.
- Update `maxReach` to be the maximum of `maxReach` and `i + nums[i]`.
- If `maxReach` is greater than or equal to the last index by the end of the loop, return `true`.

## Solution Code
```javascript
var canJump = function (nums) {
    let maxReach = 0;
    for (let i = 0; i < nums.length; i++) {
        if (i > maxReach) {
            return false
        }
        maxReach = Math.max(maxReach, i + nums[i])
        if (maxReach >= nums.length - 1) {
            return true
        }
    }
};

// Example usage:
console.log(canJump([2,3,1,1,4])); // Output: true
console.log(canJump([3,2,1,0,4])); // Output: false
```

## Complexity Analysis
##### Time Complexity
- The time complexity of this solution is `O(n)`, where n is the length of the array, as we make a single pass through the array.
##### Space Complexity
- The space complexity of this solution is `O(1)`, as we are using only a few extra variables regardless of the input size.

This solution efficiently determines whether the last index is reachable using a `greedy strategy`, ensuring both time and space efficiency.
