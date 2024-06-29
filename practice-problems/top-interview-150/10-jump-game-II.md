# 45. Jump Game II

## Problem Explanation
The problem requires finding the minimum number of jumps needed to reach the last index of an array, where each element represents the maximum jump length from that position.

### Problem Breakdown
##### Input:
- A 0-indexed array nums of length n, where each element nums[i] represents the maximum length of a forward jump from index i.
##### Output:
- The minimum number of jumps required to reach the last index nums[n - 1].
##### Constraints:
- 1 <= nums.length <= 10^4
- 0 <= nums[i] <= 1000
- It is guaranteed that you can reach the last index.

### Example
Example 1:
```
Input: nums = [2,3,1,1,4]
Output: 2
Explanation:
- Start at index 0 (value 2). You can jump to index 1 or 2.
- From index 1 (value 3), you can jump directly to the last index (index 4).
- So, the minimum number of jumps required is 2.
```
Example 2:
```
Input: nums = [2,3,0,1,4]
Output: 2
Explanation:
- Start at index 0 (value 2). You can jump to index 1 or 2.
- From index 1 (value 3), you can jump directly to the last index (index 4).
- So, the minimum number of jumps required is 2.
```

## Approach
To solve this problem efficiently, we can use a `greedy algorithm`. The idea is to keep track of the furthest index that can be reached with the current number of jumps and to determine when we need to make an additional jump to continue progressing towards the end of the array.

### Steps:
##### Initialization:
- `jumps`: Counts the number of jumps made.
- `currentEnd`: The furthest index that can be reached with the current number of jumps.
- `farthest`: The furthest index that can be reached with one more jump.
##### Iteration:
- Traverse through the array.
- Update `farthest` to the maximum index that can be reached from the current index.
- When the current index reaches `currentEnd`, increment the jump count and update `currentEnd` to `farthest`.
##### Return:
- The total number of jumps needed to reach the last index.

## Solution Code
```javascript
function jump(nums) {
    let jumps = 0; // Number of jumps made
    let currentEnd = 0; // The furthest index reachable with the current number of jumps
    let farthest = 0; // The furthest index reachable with one more jump

    for (let i = 0; i < nums.length - 1; i++) {
        // Update the farthest index reachable
        farthest = Math.max(farthest, i + nums[i]);

        // If we've reached the end of the current jump, we need to make another jump
        if (i == currentEnd) {
            jumps++;
            currentEnd = farthest;

            // If the current end reaches or exceeds the last index, we can stop
            if (currentEnd >= nums.length - 1) {
                break;
            }
        }
    }

    return jumps;
}

// Example usage:
console.log(jump([2, 3, 1, 1, 4])); // Output: 2
console.log(jump([2, 3, 0, 1, 4])); // Output: 2
```

## Explanation of the Code
#### Initialization:
- `jumps` starts at 0 because no jumps have been made initially.
- `currentEnd` starts at 0, representing the initial index.
- `farthest` also starts at 0.
#### Iteration:
- For each index `i`, update `farthest` to the maximum of the current `farthest` and `i + nums[i]`.
- If `i` reaches `currentEnd`, increment `jumps` and set `currentEnd` to `farthest`.
- If `currentEnd` reaches or exceeds the last index during the iteration, break out of the loop.
#### Return:
The number of `jumps` required to reach the last index.

## Complexity Analysis
#### Time Complexity
- The time complexity of this solution is `O(n)`, where n is the length of the array. This is because we are making a single pass through the array.
#### Space Complexity
- The space complexity of this solution is `O(1)`, as we are using a constant amount of extra space regardless of the input size.

This `greedy approach` ensures that we find the minimum number of jumps required to reach the last index efficiently.
