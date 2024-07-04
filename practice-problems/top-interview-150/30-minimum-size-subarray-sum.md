# 209. Minimum Size Subarray Sum

## Leetcode Problem
https://leetcode.com/problems/minimum-size-subarray-sum/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of finding the minimal length of a subarray whose sum is greater than or equal to a target using the `sliding window approach`, follow these steps:

Given an array of positive integers `nums` and a positive integer `target`, we need to find the minimal length of a subarray whose sum is greater than or equal to target. If no such subarray exists, return 0.

### Example
#### Example 1:
```css
Input: target = 7, nums = [2, 3, 1, 2, 4, 3]
Output: 2
Explanation: The subarray [4, 3] has the minimal length under the problem constraint.
```

#### Example 2:
```css
Input: target = 4, nums = [1, 4, 4]
Output: 1
```
#### Example 3:
```css
Input: target = 11, nums = [1, 1, 1, 1, 1, 1, 1, 1]
Output: 0
```

## Constraints
- 1 <= target <= 10^9
- 1 <= nums.length <= 10^5
- 1 <= nums[i] <= 10^4

## Approach
To achieve an `O(n)` solution, we can use the `sliding window (or two-pointer) approach`. This method involves maintaining a window that expands to include elements until the `sum` meets or exceeds the `target`, and then contracts from the left to find the minimal subarray length.

### Steps
- Initialize two pointers, `left` and `right`, both starting at the beginning of the array.
- Initialize a variable `current_sum` to keep track of the sum of elements in the current window and a variable `min_length` to keep track of the minimum length of a valid subarray.
- Expand the window by moving the right pointer and adding `nums[right]` to `current_sum` until `current_sum` is greater than or equal to the `target`.
- When the sum is sufficient, try to shrink the window from the left by moving the `left` pointer and subtracting `nums[left]` from `current_sum` to find the minimal length.
- Continue this process until the right pointer reaches the end of the array.

## Solution Code
```javascript
function minSubArrayLen(target, nums) {
    let left = 0;
    let right = 0;
    let current_sum = 0;
    let min_length = Infinity;

    while (right < nums.length) {
        current_sum += nums[right];
        while (current_sum >= target) {
            min_length = Math.min(min_length, right - left + 1);
            current_sum -= nums[left];
            left++;
        }
        right++;
    }

    return min_length === Infinity ? 0 : min_length;
}

// Example usage
console.log(minSubArrayLen(7, [2, 3, 1, 2, 4, 3])); // Output: 2
console.log(minSubArrayLen(4, [1, 4, 4])); // Output: 1
console.log(minSubArrayLen(11, [1, 1, 1, 1, 1, 1, 1, 1])); // Output: 0
```
## Explanation
- The `left` and `right` pointers represent the current window in the array.
- The `current_sum` keeps track of the sum of the elements in the current window.
- The `min_length` keeps track of the minimum length of the subarray found that meets the target sum.
- The inner while loop ensures that we shrink the window as much as possible once the `current_sum` meets or exceeds the `target`, which helps in finding the minimal length subarray.

## Time Complexity
The time complexity of this sliding window approach is `O(n)` because each element is processed at most twice (once when the right pointer moves and once when the left pointer moves).

---

# Follow-up: O(n log n) Solution
For an `O(n log n)` solution, we can use a `binary search approach`. We first create an auxiliary array `sums` where `sums[i]` is the sum of the subarray from the start of the array to index `i`. We then use binary search to find the smallest subarray that meets the target sum.

Here’s a brief outline:
- Compute the prefix sums for the array.
- For each starting index, use binary search to find the smallest ending index where the sum of the subarray meets or exceeds the target.

## Solution Code
```javascript
function minSubArrayLenBinarySearch(target, nums) {
    const n = nums.length;
    const sums = new Array(n + 1).fill(0);

    // Compute prefix sums
    for (let i = 1; i <= n; i++) {
        sums[i] = sums[i - 1] + nums[i - 1];
    }

    let min_length = Infinity;

    // Binary search for the smallest subarray that meets the target
    for (let i = 0; i < n; i++) {
        const to_find = target + sums[i];
        let left = i + 1;
        let right = n;

        while (left <= right) {
            const mid = Math.floor((left + right) / 2);
            if (sums[mid] >= to_find) {
                min_length = Math.min(min_length, mid - i);
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
    }

    return min_length === Infinity ? 0 : min_length;
}

// Example usage
console.log(minSubArrayLenBinarySearch(7, [2, 3, 1, 2, 4, 3])); // Output: 2
console.log(minSubArrayLenBinarySearch(4, [1, 4, 4])); // Output: 1
console.log(minSubArrayLenBinarySearch(11, [1, 1, 1, 1, 1, 1, 1, 1])); // Output: 0
```

## Output
```css
sums:  [ 0,  2,  5, 6, 8, 12, 15 ]
________________________________________
i:  0  to_find:  7  left:  1  right:  6
mid:  3  sums[mid] =  6
update left  4
mid:  5  sums[mid] =  12
update right  4  and min_length = 5
mid:  4  sums[mid] =  8
update right  3  and min_length = 4
________________________________________
i:  1  to_find:  9  left:  2  right:  6
mid:  4  sums[mid] =  8
update left  5
mid:  5  sums[mid] =  12
update right  4  and min_length = 4
________________________________________
i:  2  to_find:  12  left:  3  right:  6
mid:  4  sums[mid] =  8
update left  5
mid:  5  sums[mid] =  12
update right  4  and min_length = 3
________________________________________
i:  3  to_find:  13  left:  4  right:  6
mid:  5  sums[mid] =  12
update left  6
mid:  6  sums[mid] =  15
update right  5  and min_length = 3
________________________________________
i:  4  to_find:  15  left:  5  right:  6
mid:  5  sums[mid] =  12
update left  6
mid:  6  sums[mid] =  15
update right  5  and min_length = 2
________________________________________
i:  5  to_find:  19  left:  6  right:  6
mid:  6  sums[mid] =  15
update left  7
________________________________________
Output  2
```

Explanation of the Code
### 1. Initialization
```javascript
const n = nums.length;
const sums = new Array(n + 1).fill(0);
```
- `n` is the length of the input array `nums`.
- `sums` is an array of length `n + 1` initialized with zeros. This array will be used to store prefix `sums`.

### 2. Compute Prefix Sums
```javascript
for (let i = 1; i <= n; i++) {
    sums[i] = sums[i - 1] + nums[i - 1];
}
```
- The prefix `sums` array sums is computed such that `sums[i]` holds the sum of the elements from the start of nums up to the `(i-1)th` element.
- For example, if `nums = [2, 3, 1, 2, 4, 3]`, then `sums = [0, 2, 5, 6, 8, 12, 15]`.

### 3. Binary Search to Find the Minimal Subarray Length
```javascript
let min_length = Infinity;

for (let i = 0; i < n; i++) {
    const to_find = target + sums[i];
    let left = i + 1;
    let right = n;

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        if (sums[mid] >= to_find) {
            min_length = Math.min(min_length, mid - i);
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
}
```
- `min_length` is initialized to Infinity to keep track of the smallest subarray length found that meets the condition.
- The outer for loop iterates through each starting index `i` of the array nums.
- `to_find` is the value we need to find in the `sums` array. It's the sum we want from the prefix sum up to index `i` plus the `target`.
- The while loop performs a binary search within the `sums` array to find the smallest ending index `mid` such that the subarray sum from `i` to `mid` is at least `target`.
- If `sums[mid]` >= `to_find`, it means we have found a subarray that meets the condition, and we update `min_length` with the length of this subarray `(mid - i)`.
- If `sums[mid]` < `to_find`, it means we need to search further to the `right`, so we adjust the `left` pointer.
- This process continues until we find the minimal subarray length or exhaust all possibilities.

### 4. Return the Result
```javascript
return min_length === Infinity ? 0 : min_length;
```
- If min_length is still Infinity, it means no valid subarray was found, so we return 0.
- Otherwise, we return the minimal length of the subarray found.

## Example Usage
Let's run through the examples provided:
Example 1
```javascript
console.log(minSubArrayLenBinarySearch(7, [2, 3, 1, 2, 4, 3])); // Output: 2
```
- The function identifies [4, 3] as the subarray with the minimal length that sums to 7.
Example 2
```javascript
console.log(minSubArrayLenBinarySearch(4, [1, 4, 4])); // Output: 1
```
- The function identifies [4] as the subarray with the minimal length that sums to 4.
Example 3
```javascript
console.log(minSubArrayLenBinarySearch(11, [1, 1, 1, 1, 1, 1, 1, 1])); // Output: 0
```
- The function does not find any subarray that sums to 11 and returns 0.
## Summary
This solution uses prefix sums and binary search to efficiently find the minimal subarray length whose sum is greater than or equal to target. The use of prefix sums allows quick calculation of subarray sums, and binary search ensures the time complexity is O(n log n).

In conclusion, both approaches provide efficient solutions to the problem within their respective time complexities, making them suitable for handling the given constraints.
