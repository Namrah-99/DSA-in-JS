# 219. Contains Duplicate II

## Leetcode Problem
https://leetcode.com/problems/contains-duplicate-ii/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of finding two distinct indices `i` and `j` in the array nums such that `nums[i] == nums[j]` and `|i - j| <= k`, we can efficiently use a `hash table approach` in JavaScript. Let's break down the problem and the solution approach:


Given an array `nums` and an integer `k`, we need to find if there exist two indices `i` and `j` (where `𝑖 ≠ 𝑗`) such that:
- The elements at these indices are equal: `nums[i] == nums[j]`
- The absolute difference between `i` and `j` is at most `k`.

## Approach
- **Hash Map Usage:** Utilize a hash map (`map`) to store each number encountered so far as keys and their corresponding index as values.
- **Algorithm Steps:**
    - Iterate through the array `nums`.
    - For each element `nums[i]`:
    - Check if `nums[i]` already exists in the hash map:
        - If it does and the absolute difference between the current index `i` and the stored index `map[nums[i]]` is less than or equal to `k`, return `true`.
        - If `nums[i]` does not exist in the hash map, store it along with its index `i`.
- **Output:** If no such pair is found throughout the iteration, return `false`.

## Solution Code
```javascript
var containsNearbyDuplicate = function (nums, k) {
    let map = new Map();
    for (let i = 0; i < nums.length; i++) {
        if (map.has(nums[i]) && i - map.get(nums[i]) <= k) {
            return true
        }
        map.set(nums[i], i)
    }
    return false;
};

// Example usage:
console.log(containsNearbyDuplicate([1,0,1,1], 1)); // Output: true
console.log(containsNearbyDuplicate([1,2,3,1,2,3], 2)); // Output: false
```

## Complexity Analysis
### Time Complexity:
- The algorithm iterates through the array `nums` exactly once, which takes `O(n)` time.
- Each hash map operation (insert and lookup) takes average `O(1)` time.
- Therefore, the overall time complexity is `O(n)`.
### Space Complexity:
- The space complexity is `O(min(n, k))`, where `n` is the size of the array `nums` and `k` is the value of the integer `k`.
- In the worst case, the hash map `map` can store up to `k` elements.
- Auxiliary space used by other variables (like `i` and `nums[i]`) is constant `O(1)` space.

