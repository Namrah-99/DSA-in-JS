# 56. Merge Intervals

## Leetcode Problem
https://leetcode.com/problems/merge-intervals/description/

## Problem Explanation
The problem is to merge all overlapping intervals from a given list of intervals and return a list of the merged, non-overlapping intervals.

Given an array of intervals where each interval is represented as [starti, endi], we need to merge overlapping intervals. Two intervals [a, b] and [c, d] overlap if b >= c.

## Approach
The approach used in the provided code is commonly referred to as the `Sorting and Merging Intervals` approach. Here’s a concise explanation of the approach:

### Explanation
#### Sorting:
- The intervals are first sorted based on their starting times. This ensures that overlapping intervals are positioned next to each other.
#### Initialization:
- A list, merged, is initialized with the first interval.
#### Iteration and Merging:
- Iterate through the sorted intervals and for each interval, check if it overlaps with the last interval in the merged list.
- If it overlaps, merge them by updating the end time of the last interval in the merged list.
- If it does not overlap, simply add the current interval to the merged list.

## Solution Code
```javascript
var merge = function(intervals) {
    // check if intervals length more than 1 or not
    if(intervals.length <= 1) return intervals;
    //sort the intervals by their start time
    intervals.sort((a,b)=> a[0] - b[0])
    // initialize the merged interval list
    let merged = [intervals[0]];
    // iterate through the elements of intervals
    for(let i=1; i<intervals.length; i++){
        // extract last merged interval
        let lastMerged = merged[merged.length - 1];
        let current = intervals[i];
        // if the current interval and lastMerged interval are overlapped
        if(current[0] <= lastMerged[1]){
            // if overlapped then merge the current with lastMerged interval
            lastMerged[1] = Math.max(lastMerged[1],current[1]);
        }else{
            // if not overlapped then push current to merged list
            merged.push(current)
        }
    }
    return merged;
};

Example 1:
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

Example 2:
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

## Time Complexity
- Sorting: The sorting step takes O(nlogn).
- Merging: The merging step takes O(n).

Thus, the overall time complexity is `O(nlogn)`. This approach ensures that we efficiently merge intervals with a time complexity of O(nlogn) due to the sorting step. The merging step itself is linear, O(n).
