# 56. Merge Intervals

## Leetcode Problem
https://leetcode.com/problems/merge-intervals/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
The given JavaScript function merge is designed to merge overlapping intervals in an array `intervals` and return the merged intervals. Let's break down the approach and analyze its complexity:

### Explanation
1. Edge Case Check:
- If the length of intervals is `0 or 1`, return `intervals` itself since no merging is needed.
2. Sorting:
- Sort the intervals array based on the start time of each interval (`a[0] - b[0]`). This ensures that intervals are processed in ascending order of their `start` times.
3. Merging Process:
- Initialize an array merged with the first interval from the sorted intervals.
- Iterate through the sorted intervals starting from the second interval.
- For each interval:
    - Check if it overlaps with the last interval in merged (`lastMerged`).
    - If there is an overlap (i.e., `current[0] <= lastMerged[1]`), merge the intervals by updating the end time of `lastMerged` to the maximum of `lastMerged[1]` and `current[1]`.
    - If there is no overlap, push current as a new interval into merged.
- Return:
    - Return the merged array which now contains the merged intervals.

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
// Example usage:
console.log(merge([[1,3],[2,6],[8,10],[15,18]])); // Output: [[1,6],[8,10],[15,18]]
console.log(merge([[1,4],[4,5]])); // Output: [[1,5]]
```

## Complexity Aanlysis

### Time Complexity:
- Sorting: Sorting intervals takes `O(n log n)` time, where n is the number of intervals. This dominates the time complexity.
- Merging: After sorting, iterating through the intervals array takes `O(n)` time because each interval is processed once.
- Therefore, the overall time complexity is `O(n log n)` due to the sorting step.

### Space Complexity:
- The space complexity is `O(n)` in the worst case. This is because the merged array can potentially store all n intervals if none of them overlap significantly.
- Sorting typically requires `O(log n)` additional space for the call stack, making the total auxiliary space usage `O(n)` including merged and other variables.
