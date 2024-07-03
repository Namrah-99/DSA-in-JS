# 11. Container With Most Water

## Leetcode Problem
https://leetcode.com/problems/container-with-most-water/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Breakdown:
The goal is to find two lines such that they, together with the x-axis, form a container that can store the maximum amount of water. The area formed between two lines is determined by the shorter line, as water cannot exceed the height of the shorter line. The width between the lines is simply the difference in their indices.

## Approach
To solve this problem efficiently, we can use the `two-pointer approach`, which is suitable for achieving linear time complexity `O(n)`.
- **Initialize Two Pointers:** Start with one pointer at the beginning (left = 0) and the other at the end (right = height.length - 1).
- **Calculate Area:** Compute the `area` formed between the lines pointed by `left` and `right` using the formula: `area=min(height[left],height[right])×(right−left)`
- **Move Pointers:** To try and find a larger area, move the pointer that points to the shorter line:
    - If `height[left] < height[right]`, increment the `left` pointer to possibly find a taller line.
    - If `height[left] >= height[right]`, decrement the `right` pointer to possibly find a taller line.
- **Continue Until Pointers Meet:** Repeat the calculation and pointer movement until `left` and `right` pointers meet.
- **Track Maximum Area:** Keep track of the maximum area found during the iterations.

## Solution Code
```javascript
var maxArea = function (height) {
    let left = 0, right = height.length - 1; let maxArea = 0;
    while (left < right) {
        let width = right - left, minHeight = Math.min(height[left], height[right]);
        let area = minHeight * width;
        maxArea = Math.max(area, maxArea)
        if (height[left] < height[right]) {
            left++
        } else {
            right--
        }
    }
    return maxArea;
};

console.log(maxArea([1, 1])) // 1
console.log(maxArea([1, 8, 6, 2, 5, 4, 8, 3, 7])) // 49
```

## Complexity Analysis
- **Time Complexity:** `O(n)`. Each element in the array is processed at most once by the `left` and `right` pointers.
- **Space Complexity:** `O(1)`. No extra space is used other than a few variables for tracking pointers and the maximum area.
