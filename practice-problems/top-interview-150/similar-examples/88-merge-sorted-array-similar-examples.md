# 977. Squares of a Sorted Array

## Leetcode Problem
https://leetcode.com/problems/squares-of-a-sorted-array/description/

## Approach
The approach used in the above solution is the `two-pointer technique`. This method involves initializing pointers at both ends of the input array and iteratively comparing and placing the larger square value from either end into the result array, working from the end towards the beginning. This ensures that the array is processed in linear time, `O(n)`.

## Solution Code
```javascript
var sortedSquares = function(nums) {
    // Get the length of the input array
    let n = nums.length;

    // Create a new array to store the result
    let result = new Array(n);

    // Initialize two pointers: one at the start and one at the end of the array
    let left = 0;
    let right = n - 1;

    // Initialize the index for the result array starting from the end
    let index = n - 1;

    // Loop until the left pointer is greater than the right pointer
    while (left <= right) {
        // Calculate the square of the elements at both pointers
        let leftSquare = nums[left] * nums[left];
        let rightSquare = nums[right] * nums[right];

        // Compare the squares and place the larger one in the current position of the result array
        if (leftSquare > rightSquare) {
            result[index] = leftSquare;
            // Move the left pointer to the right
            left++;
        } else {
            result[index] = rightSquare;
            // Move the right pointer to the left
            right--;
        }

        // Move to the next position in the result array
        index--;
    }

    // Return the result array which contains the squares in sorted order
    return result;
};
```

## Explanation of the Code

- Initialization:
    - The length of the array n is determined.
    - A result array of the same length is created to store the squared values.
    - Two pointers, left and right, are initialized to point to the beginning and end of the input array nums.
    - An index pointer is initialized to the last position of the result array.
- Two-pointer technique:
    - The while loop runs as long as the left pointer is less than or equal to the right pointer.
    - In each iteration, the squares of the values at the left and right pointers are compared.
    - The larger of the two squared values is placed at the current position indicated by the index pointer in the result array.
    - The pointer (left or right) from which the squared value was taken is moved inward.
    - The index pointer is decremented to move to the next position in the result array.
 
## Time Complexity

This solution effectively sorts the squares of the elements from the input array in linear time O(n), leveraging the two-pointer technique to maintain efficiency.
