# 80. Remove Duplicates from Sorted Array II

## Leetcode Problem
https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
You are given an integer array `nums` sorted in non-decreasing order. Your task is to modify the array in place so that each unique element appears at most twice. The relative order of the elements should be maintained. After modifying the array, you need to return the length `k` of the modified array where the first `k` elements contain the desired result.

## Constraints
- You cannot use extra space for another array.
- You must modify the input array in place with `O(1)` extra memory.
- The input array is sorted in non-decreasing order.
- `1 <= nums.length <= 30,000`
- `-10^4 <= nums[i] <= 10^4`

## Approach
- Use a pointer `i` to keep track of the position to insert the next valid element.
- Iterate through the array with another pointer `j`.
- Allow the first two occurrences of each element, and skip any further occurrences.
- Copy valid elements to the position indicated by `i` and increment `i`.

## Solution Code
```javascript
var removeDuplicates = function(nums) {
    // If the array is empty, return 0 as there are no elements.
   if(!nums.length) return 0
   if(nums.length<=2) return nums.length
    // Initialize a pointer i to keep track of the position of the last unique element.
    let i = 2;
    
    // Iterate through the array starting from the second element.
    for (let j = 2; j < nums.length; j++) {
        // If the current element is not equal to the element at position i-2,
        // it means we have found a new unique element.
        if (nums[j] !== nums[i-2]) {
            // Update the position i with the new unique element.
            nums[i] = nums[j];
            // Move the pointer i to the next position.
            i++;
        }
    }
    
    // Return the count of unique elements, which is i.
    return i;
};

// Example usage:
console.log(removeDuplicates([1,1,1,2,2,3])); // Output: 5
console.log(removeDuplicates([0,0,1,1,1,1,2,3,3])); // Output: 7
```

## Complexity Analysis

#### Time Complexity
  - `O(n)` where n is the length of the array. Each element is processed at most twice.
#### Space Complexity
  - `O(1)` extra space is used.
