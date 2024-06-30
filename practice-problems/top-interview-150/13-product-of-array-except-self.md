# 238. Product of Array Except Self

## Leetcode Problem
https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
Given an integer array `nums`, we need to return an array `answer` such that `answer[i]` is equal to the product of all elements of nums except `nums[i]`. The solution should run in `O(n)` time complexity and should not use the division operation.

### Example
Example 1:
```
Input: nums = [1,2,3,4]
Output: answer = [24,12,8,6]
```
Explanation:
```
answer[0] = 2 * 3 * 4 = 24
answer[1] = 1 * 3 * 4 = 12
answer[2] = 1 * 2 * 4 = 8
answer[3] = 1 * 2 * 3 = 6
```
Example 2:
```
Input: nums = [-1,1,0,-3,3]
Output: answer = [0,0,9,0,0]
```
Explanation:
```
answer[0] = 1 * 0 * (-3) * 3 = 0
answer[1] = -1 * 0 * (-3) * 3 = 0
answer[2] = -1 * 1 * (-3) * 3 = 9
answer[3] = -1 * 1 * 0 * 3 = 0
answer[4] = -1 * 1 * 0 * (-3) = 0
```
### Constraints
```
- 2 <= nums.length <= 10^5
- -30 <= nums[i] <= 30
```
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

## Approach
- **Left Pass:** Create an array `left` where `left[i]` contains the product of all elements to the left of `i`.
- **Right Pass:** Create an array `right` where `right[i]` contains the product of all elements to the right of `i`.
- **Combine:** The final result `answer[i]` is obtained by multiplying `left[i]` and `right[i]`.
This approach ensures `O(n)` time complexity.

## Solution Code
```javascript
var productExceptSelf = function(nums) {
    let n = nums.length;
    let answer=new Array(n).fill(1); 
    let left=1;

    for(let i=0;i<n;i++){
        answer[i]=left;
        left*=nums[i];
    }
    console.log(answer)
    let right=1;
    for(let i=n-1;i>=0;i--){
        answer[i]*=right;
        right*=nums[i];
    }

    return answer;
};

// Example usage:
console.log(productExceptSelf([1, 2, 3, 4])); // Output: [24, 12, 8, 6]
console.log(productExceptSelf([-1, 1, 0, -3, 3])); // Output: [0, 0, 9, 0, 0]
```

## Explanation of Code
##### 1. Initialization:
- `answer` array initialized with 1s to hold the final result.
- `leftProduct` and `rightProduct` initialized to 1.
##### 2. Left Pass:
- Iterate from left to right.
- For each index `i`, set `answer[i]` to `leftProduct`.
- Update `leftProduct` to include `nums[i]`.
##### 3. Right Pass:
- Iterate from right to left.
- For each index `i`, multiply `answer[i]` with `rightProduct`.
- Update `rightProduct` to include `nums[i]`.

## Complexity Analysis
This approach ensures that we do not use any extra space other than the output array, achieving `O(n)` time complexity and `O(1)` extra space complexity.
