# 27. Remove Element

## Leetcode Problem
https://leetcode.com/problems/remove-element/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem requires you to remove all occurrences of a given integer val from an array nums, in-place, and return the number of elements that are not equal to val. The elements in the modified array can be in any order, and it is not necessary to consider the elements beyond the k valid elements (where k is the count of elements not equal to val).

## Approach
The solution employs the `two-pointer technique` to solve the problem in an efficient manner. Here's a detailed explanation of the approach used:

### Two-Pointer Technique
In this technique, two pointers (i and k) are used to traverse and modify the array nums in place. Here's a step-by-step breakdown of how the approach works:
#### Initialization:
  - `k` is initialized to 0. It acts as a pointer to track the position where the next element that is not equal to `val` should be placed.
#### Traverse the Array:
  - Use a for loop to iterate through each element in the array `nums` with the index `i`.
#### Check Condition:
  - For each element `nums[i]`, check if it is not equal to `val`.
#### Modify the Array:
  - If `nums[i]` is not equal to `val`, assign `nums[i]` to `nums[k]`.
  - Increment `k` by 1 to update the position for the next non-`val` element.
#### Continue Traversing:
  - Continue this process until all elements in the array have been checked.
#### Return Result:
  - After the loop, `k` will contain the number of elements in `nums` that are not equal to `val`.
  - The first `k` elements of `nums` will be those that are not equal to `val`.

## Solution Code
```javascript
var removeElement = function(nums, val) {
    let k = 0;
    
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== val) {
            nums[k] = nums[i];
            k++;
        }
    }
    
    return k;
};

// Example usage:
console.log(removeElement([3, 2, 2, 3], 3)); // Output: 2, nums = [2, 2, _, _]
console.log(removeElement([0, 1, 2, 2, 3, 0, 4, 2], 2)); // Output: 5, nums = [0, 1, 3, 0, 4, _, _, _]
```

## Steps to Solve the Problem
- Iterate through the Array: Use a loop to go through each element of the array nums.
- Check for val: For each element, check if it is not equal to val.
- Rearrange Elements: If the element is not equal to val, move it to the front of the array (to the position k).
- Count Valid Elements: Maintain a count of how many elements are not equal to val (this count is k).
- Return k: Return the count of elements that are not equal to val.

## Time Complexity
- This implementation has a time complexity of `O(n)` where n is the length of the array nums, and it works in-place without using extra space.
  - Efficiency: The two-pointer technique allows us to solve the problem in a single pass through the array, resulting in O(n) time complexity.
  - In-Place Modification: It modifies the array in place, requiring no additional space, thus achieving O(1) space complexity.
