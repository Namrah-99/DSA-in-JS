# 26. Remove Duplicates from Sorted Array

## Leetcode Problem
https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to remove duplicates from a sorted integer array nums in-place, ensuring that each unique element appears only once. The function should return the number of unique elements, k, while modifying the array such that the first k elements contain these unique elements in their original order

## Approach
The approach to solving this problem efficiently is to use the `two-pointer technique`. Here's a detailed explanation of the approach:

#### 1. Initialization:
- If the array `nums` is empty, return 0.
- Initialize two pointers: `i` and `j`. Set `i` to 0 (the first position) and `j` to 1 (the second position).
#### 2. Traverse the Array:
- Iterate through the array using pointer `j`.
#### 3. Compare Elements:
- For each element `nums[j]`, compare it with `nums[i]`.
- If `nums[j]` is different from `nums[i]`, it means we have found a new unique element.
#### 4. Modify the Array:
- Increment `i` and assign `nums[i]` to `nums[j]`. This ensures that the unique elements are moved to the front of the array.
- Continue this process until all elements have been checked.
#### 5. Return Result:
- The number of unique elements k is `i + 1` because `i` is zero-based.

## Solution Code
```javascript
var removeDuplicates = function (nums) {
    // If the array is empty, return 0 as there are no elements.
    if (!nums.length) return 0
    // Initialize a pointer i to keep track of the position of the last unique element.
    let i = 0;

    // Iterate through the array starting from the second element.
    for (let j = 1; j < nums.length; j++) {
        // If the current element is not equal to the element at position i,
        // it means we have found a new unique element.
        if (nums[j] !== nums[i]) {
            // Move the pointer i to the next position.
            i++;
            // Update the position i with the new unique element.
            nums[i] = nums[j];
        }
    }

    // Return the count of unique elements, which is i + 1.
    return i + 1;
};

// Example usage:

// Test case 1:
// Input array has duplicates: [1, 1, 2]
// After removing duplicates: [1, 2, _]
// Output: 2 (number of unique elements)
console.log(removeDuplicates([1, 1, 2])); // Output: 2

// Test case 2:
// Input array has duplicates: [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
// After removing duplicates: [0, 1, 2, 3, 4, _, _, _, _, _]
// Output: 5 (number of unique elements)
console.log(removeDuplicates([0, 0, 1, 1, 1, 2, 2, 3, 3, 4])); // Output: 5
```
## Complexity Analysis
#### Time Complexity
The time complexity of the given solution is `O(n)`, where n is the length of the input array `nums`.
- Explanation:
  Traversal and Modification: The for loop iterates over the array exactly once, performing constant time operations (O(1)) for each element. Therefore, the total time complexity is O(n).
#### Space Complexity:
The space complexity is `O(1)` because the solution uses only a constant amount of extra space.
