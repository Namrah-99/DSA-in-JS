# 3169. Count Days Without Meetings

## Leetcode Problem
https://leetcode.com/problems/count-days-without-meetings/description/

## Problem Statement
The problem requires finding the number of days an employee is available for work but has no scheduled meetings. The solution involves tracking the days covered by meetings and then calculating the days that are free.

---

# Easy Approach
#### Sort Meetings:
  - First, we sort the meetings based on their starting day. This helps in efficiently merging overlapping intervals.
#### Merge Overlapping Meetings:
  - Iterate through the sorted meetings and merge overlapping or adjacent meetings into a single interval.
  - Track the merged intervals to get the total range of days that are covered by meetings.
#### Count Free Days:
  - Calculate the total number of days covered by the merged intervals.
  - Subtract the total number of covered days from the given number of days to get the number of free days.

## Solution Code
```javascript
var countDays = function(days, meetings) {
    // Sort meetings by their starting time
    meetings.sort((a, b) => a[0] - b[0]);
console.log(meetings)
    // Initialize variables to keep track of covered days and the current range
    let coveredDays = 0;
    let currentStart = -1, currentEnd = -1;

    // Iterate through the meetings
    for (let [start, end] of meetings) {
        // If the current meeting starts after the current covered range
        if (start > currentEnd) {
            // Add the length of the current range to the covered days
            if (currentStart !== -1) {
                coveredDays += currentEnd - currentStart + 1;
            }
            // Reset the range to the current meeting
            currentStart = start;
            currentEnd = end;
        } else {
            // Extend the current range to include the current meeting
            currentEnd = Math.max(currentEnd, end);
        }
    }

    // Add the final range to the covered days
    if (currentStart !== -1) {
        coveredDays += currentEnd - currentStart + 1;
    }

    // Return the number of days that are not covered by any meeting
    return days - coveredDays;
};

// Example usage:
console.log(countDays(10, [[5,7],[1,3],[9,10]])); // Output: 2
console.log(countDays(5, [[2,4],[1,3]])); // Output: 1
console.log(countDays(6, [[1,6]])); // Output: 0
console.log(countDays(8, [[2,3],[3,5],[8,8]])); // Output: 3
console.log(countDays(33, [[3,9],[7,16],[21,23],[22,33],[5,13],[10,23],[1,15]])); // Output: 0
console.log(countDays(57, [[3,49],[23,44],[21,56],[26,55],[23,52],[2,9],[1,48],[3,31]])); // Output: 1
```

## Explanation of Code
#### Initialization:
  - Initialize variables to keep track of the start and end of the current interval.
  - Initialize a counter to keep track of the total number of covered days.
#### Iterate through Meetings:
  - For each meeting, if it starts after the end of the current interval, add the length of the current interval to the covered days and update the current interval to the new meeting.
  - If it overlaps or is adjacent to the current interval, extend the current interval to cover the new meeting.
#### Add the Final Interval:
  - After iterating through all meetings, add the length of the last interval to the covered days.
#### Calculate Free Days:
  - Subtract the total number of covered days from the total number of days to get the number of free days.

## Time Complexity
This approach ensures that the solution runs efficiently with a time complexity of `O(nlogn)` due to the sorting step, which is necessary to handle potential overlaps properly. The subsequent merging and counting steps run in linear time O(n).

---
# My Approach
The approach used in solving the above problem involves `sorting`, `greedy strategy`, and `merging intervals`. Let's break down each component of this approach:

####  1. Sorting:
  - First, the `meetings` array is sorted by the starting time of each meeting. Sorting helps in processing the meetings in chronological order, which simplifies the merging process.
#### 2. Greedy Strategy:
  - The greedy strategy is used to merge overlapping intervals. By always taking the next available meeting and trying to merge it with the current group, we ensure that we minimize the number of groups and thus maximize the number of non-overlapping intervals.
#### 3. Merging Intervals:
  - As we iterate through the sorted meetings, we either extend the current group if the meeting overlaps with the current group's end or close the current group and start a new group if the meeting does not overlap.
#### 4. Counting Covered Days:
  - After identifying the groups, the total number of days covered by all groups is calculated.
  - The result is then the difference between the total number of days and the number of days covered by the meetings.

## Solution Code
```javascript
var countDays = function(days, meetings) {
    // Sort meetings by their starting time
    meetings.sort((a, b) => a[0] - b[0]);

    // Initialize variables to keep track of groups and their start and end times
    let groups = [], startEle = meetings[0][0], end = meetings[0][1];

    // Iterate through the meetings
    for (let i = 0; i < meetings.length; i++) {
        // Check if the current meeting is non-overlapping with the last recorded group
        if (meetings[i][0] > end || i + 1 === meetings.length || meetings[i + 1][0] > end) {
            // Update the end time of the current group
            end = i + 1 === meetings.length || meetings[i][0] >= end || meetings[i][1] >= end ? Math.max(meetings[i][1], end) : end;
            // Push the current group to the groups array
            groups.push([startEle, end]);

            // Check if there are more meetings to process
            if (i + 1 < meetings.length) {
                // If the current group's end overlaps with the next meeting's start
                if (groups[groups.length - 1][1] >= meetings[i + 1][0]) {
                    startEle = groups[groups.length - 1][0]; // Continue the current group
                    groups.pop(groups[groups.length - 1]); // Remove the last group since it's being extended
                } else {
                    startEle = meetings[i + 1][0]; // Start a new group
                }
            }
        } else {
            // Extend the current group if the meeting overlaps
            end = Math.max(end, meetings[i][1]);
        }
    }

    // Calculate the total number of days covered by the groups
    let countDays = 0, i = 0;
    while (i < groups.length) {
        countDays += groups[i][1] - groups[i][0] + 1;
        i++;
    }

    // Return the number of days that are not covered by any meeting
    return days - countDays;
};

// Example usage:
console.log('output: ',countDays(10, [[5,7],[1,3],[9,10]])); // Output: 2
console.log('output: ',countDays(5,  [[2,4],[1,3]])); // Output: 1
console.log('output: ',countDays( 6, [[1,6]])); // Output: 0
console.log('output: ',countDays( 8, [[2,3],[3,5],[8,8]])); // Output: 3
console.log('output: ',countDays( 33, [[3,9],[7,16],[21,23],[22,33],[5,13],[10,23],[1,15]])); // Output: 0
console.log('output: ',countDays( 57, [[3,49],[23,44],[21,56],[26,55],[23,52],[2,9],[1,48],[3,31]])); // Output: 1
```

## Time Complexity
- Sorting takes O(nlogn), where n is the number of meetings.
- The main loop runs in O(n).
Overall, the time complexity is `O(nlogn)`.



