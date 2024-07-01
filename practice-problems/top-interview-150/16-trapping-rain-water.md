# 42. Trapping Rain Water

## Leetcode Problem
https://leetcode.com/problems/trapping-rain-water/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem you're describing is a classic "trapping rain water" problem. The task is to calculate how much water can be trapped between the bars of a given elevation map.

## Problem Explanation
Given an array `height` representing an elevation map where the width of each bar is 1, you need to compute how much water it can trap after raining.

Example 1:
```
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```
Explanation:
- The elevation map is represented by the array `[0,1,0,2,1,0,1,3,2,1,2,1]`.
- Water is trapped between the bars, with a total volume of 6 units.

Example 2:
```
Input: height = [4,2,0,3,2,5]
Output: 9
```
Explanation:
- The elevation map is represented by the array `[4,2,0,3,2,5]`.
- Water is trapped between the bars, with a total volume of 9 units.

### Constraints:
- n == height.length
- 1 <= n <= 2 * 10^4
- 0 <= height[i] <= 10^5

## Approach
To solve this problem in `O(n)` time complexity, you can use a `two-pointer approach`:

1. Initialize two pointers, `left` and `right`, at the start and end of the array, respectively.
2. Maintain two variables, `left_max` and `right_max`, to store the maximum heights seen so far from the left and right pointers.
3. Move the pointers towards each other. At each step:
    - Compare the heights at the `left` and `right` pointers.
    - If the height at `left` is less than or equal to the height at `right`, process the `left` pointer:
      - If `height[left]` is greater than or equal to `left_max`, update `left_max`.
      - Else, add the difference `left_max - height[left]` to the water trapped.
      - Move the `left` pointer one step to the right.
    - If the height at `right` is less than the height at `left`, process the `right` pointer:
      - If height[right] is greater than or equal to right_max, update right_max.
      - Else, add the difference `right_max - height[right]` to the water trapped.
      - Move the `right` pointer one step to the left.

## Solution Code
```javascript
var trap = function (height) {
    let left = 0, right = height.length - 1;
    let left_max = 0, right_max = 0;
    let water = 0;

    while (left < right) {
        if (height[left] < height[right]) {
            if (height[left] >= left_max) {
                left_max = height[left];
            } else {
                water += left_max - height[left];
            }
            left++;
        } else {
            if (height[right] >= right_max) {
                right_max = height[right];
            } else {
                water += right_max - height[right];
            }
            right--;
        }
    }
    
    return water;
}

// Example usage:
console.log(trap([0,1,0,2,1,0,1,3,2,1,2,1])); // Output: 6
console.log(trap([4,2,0,3,2,5])); // Output: 9
```

## Output
```
left index:  0  , right index:  11  , left_max val:  0  , right_max:  0
_________________________________________________________________________
go to left side as left= 0 < right= 11
set left_max to current height[left] if current is >= left_max:  0
_________________________________________________________________________
go to right side
set right_max to current height[right] if current is >= right_max:  0
_________________________________________________________________________
go to left side as left= 1 < right= 10
set left_max to current height[left] if current is >= left_max:  0
_________________________________________________________________________
go to left side as left= 2 < right= 10
add unit if current h[left]<left_max, then add left_max-height[left]
water units before:  0
after:  1
_________________________________________________________________________
go to right side
set right_max to current height[right] if current is >= right_max:  1
_________________________________________________________________________
go to right side
add unit if current h[righ]<right_max, then add right_max-height[right]
_________________________________________________________________________
go to right side
set right_max to current height[right] if current is >= right_max:  2
_________________________________________________________________________
go to left side as left= 3 < right= 7
set left_max to current height[left] if current is >= left_max:  1
_________________________________________________________________________
go to left side as left= 4 < right= 7
add unit if current h[left]<left_max, then add left_max-height[left]
water units before:  2
after:  3
_________________________________________________________________________
go to left side as left= 5 < right= 7
add unit if current h[left]<left_max, then add left_max-height[left]
water units before:  3
after:  5
_________________________________________________________________________
go to left side as left= 6 < right= 7
add unit if current h[left]<left_max, then add left_max-height[left]
water units before:  5
after:  6
_________________________________________________________________________
output:  6
```

## Complexity Analysis
- Time Complexity: `O(n)`, where n is the length of the array height - Each element is processed once.
- Space Complexity: `O(1)` - Uses constant extra space.
