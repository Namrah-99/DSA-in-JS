# 57. Insert Interval

## Leetcode Problem
https://leetcode.com/problems/insert-interval/description/?envType=study-plan-v2&envId=top-interview-150

## Solution Code
```javascript
var insert = function (intervals, newInterval) {

    let result = [];
    let i = 0;

    while (i < intervals.length && newInterval[0] > intervals[i][1]) {
        result.push(intervals[i]);
        i++;
    }
    // merge overlapping intervals
    while (i < intervals.length && newInterval[1] >= intervals[i][0]) {
        newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
        newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
        i++;
    }

    result.push(newInterval);

    while (i < intervals.length) {
        result.push(intervals[i]);
        i++;
    }

    return result;
};
// Example usage:
console.log(insert([[1,3],[6,9]], [2,5])); // Output: [[1,5],[6,9]]
console.log(insert([[1,2],[3,5],[6,7],[8,10],[12,16]], [4,8])); // Output: [[1,2],[3,10],[12,16]]
```

The function `insert` is used to insert a new interval (`newInterval`) into a list of non-overlapping intervals (`intervals`), merging overlapping intervals as necessary. Let's break down the approach and analyze its complexity:

## Approach
1. Initialization:
    - Initialize an empty array result to store the merged intervals.
    - Initialize `i` to `0` to iterate through intervals.
2. Non-overlapping Intervals Before newInterval:
    - Iterate through `intervals` and push intervals from `intervals[i]` to `intervals[i-1]` into `result` until you find an interval in `intervals` that ends before `newInterval` starts (`newInterval[0] > intervals[i][1]`).
3. Merge Overlapping Intervals:
    - While there are more intervals in intervals and there is overlap between `newInterval` and `intervals[i]` (`newInterval[1] >= intervals[i][0]`):
        - Update `newInterval` start (`newInterval[0]`) to the minimum of `newInterval[0]` and `intervals[i][0]`.
        - Update `newInterval` end (`newInterval[1]`) to the maximum of `newInterval[1]` and `intervals[i][1]`.
        - Move to the next interval in `intervals`.
4. Insert newInterval:
    - Push the merged `newInterval` into `result`.
5. Remaining Intervals:
    - Push all remaining intervals in `intervals` into `result`.
6. Return:
    - Return `result`, which now contains the merged intervals with the new interval inserted.

## Complexity Analysis

### Time Complexity:
- **Traversal and Merging:** Traversing through intervals and merging intervals takes `O(n)`, where `n` is the number of intervals in intervals.
- **Copying:** Copying intervals into result also takes `O(n)`.
- Therefore, the overall time complexity is `O(n)`, where `n` is the number of intervals in intervals.

### Space Complexity:
- The space complexity is `O(n)` in the worst case due to the result array storing all merged intervals.
- Sorting is not needed in this approach, which optimizes space usage compared to other merging algorithms that use sorting.
