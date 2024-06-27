# 57. Insert Interval

## Leetcode Problem
https://leetcode.com/problems/insert-interval/description/

## Problem Explanation
The problem is to insert a new interval into a sorted array of non-overlapping intervals and merge any overlapping intervals, returning the updated list of intervals.
#### Given:
- intervals: A sorted list of non-overlapping intervals.
- newInterval: An interval to insert into intervals.
The goal is to insert newInterval into intervals and merge any overlapping intervals while maintaining the order.

## Approach
The approach used in the above code is commonly known as the `two-pointer technique` or `sweep line algorithm`. Here's a breakdown of the approach:

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
console.log( insert([[1,3],[6,9]], [2,5]))
console.log( insert([[1,2],[3,5],[6,7],[8,10],[12,16]], [4,8]))
```

## Steps to Solve the Problem
- Initialization:
    - Create a list result to store the merged intervals.
    - Initialize an index variable i to iterate over the intervals.
- Add all intervals before newInterval:
    - Iterate over the intervals and add all intervals that end before newInterval starts to result.
- Merge overlapping intervals:
    - While there are intervals that overlap with newInterval (i.e., the current interval starts before newInterval ends), merge them into newInterval.
- Add the merged newInterval:
    - Add the merged newInterval to result.
- Add remaining intervals:
    - Add all remaining intervals (those that start after newInterval ends) to result.
- Return the result:
    - Return the result list containing the merged intervals.

## Time Complexity
- Sorting Step: Since the given intervals are already sorted by their start times, no additional sorting is required.
- Merging Step: Each interval is processed exactly once, leading to a time complexity of O(n).

Overall Time Complexity: `O(n)`
