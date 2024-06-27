# 986. Interval List Intersections

## Leetcode Problem
https://leetcode.com/problems/interval-list-intersections/description/

## Problem Explanation
You are given two lists of closed intervals, `firstList` and `secondList`. Each interval is represented as a pair `[start, end]`, where start and end are integers, and `start <= end`. The intervals within each list are disjoint and sorted in ascending order.

Your task is to find the intersection of these two lists of intervals. The intersection of two intervals `[a, b]` and `[c, d]` is defined as the set of numbers that are present in both intervals. This can be represented as a new interval `[max(a, c), min(b, d)]` if `max(a, c) <= min(b, d)`. If `max(a, c) > min(b, d)`, there is no intersection.

## Example Explanation

#### Example 1:
```
Input:
firstList = [[0,2],[5,10],[13,23],[24,25]]
secondList = [[1,5],[8,12],[15,24],[25,26]]
Output: [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
```

#### Explanation:
- The intersection of [0, 2] and [1, 5] is [1, 2].
- The intersection of [5, 10] and [1, 5] is [5, 5].
- The intersection of [5, 10] and [8, 12] is [8, 10].
- The intersection of [13, 23] and [15, 24] is [15, 23].
- The intersection of [24, 25] and [15, 24] is [24, 24].
- The intersection of [24, 25] and [25, 26] is [25, 25].

#### Example 2:
```
Input:
firstList = [[1,3],[5,9]]
secondList = []
Output: []
```

#### Explanation: 
Since secondList is empty, there are no intersections.

#### Constraints:
- The length of each list is between 0 and 1000.
- The combined length of both lists is at least 1.
- Intervals are closed and pairwise disjoint within each list.
- Intervals are in sorted order within each list.

## Approach
To find the intersection of two interval lists, you can use a two-pointer approach. Here is a step-by-step explanation:

#### 1. Initialization:
- Use two pointers, i and j, initialized to 0. These will traverse through firstList and secondList respectively.
- Create an empty list result to store the intersections.

#### Traversal:
- Traverse both lists using the pointers i and j.
- For each pair of intervals firstList[i] and secondList[j]:
- Compute the intersection, if it exists, using the formula:
- start = max(firstList[i][0], secondList[j][0])
- end = min(firstList[i][1], secondList[j][1])
- If start <= end, add the interval [start, end] to result.
- Move the pointer of the interval that ends first (i.e., if `firstList[i][1] < secondList[j][1]`, increment `i`, otherwise increment `j`).

#### End Condition:
- Continue the above steps until you have processed all intervals in either firstList or secondList.

## Solution Code
```javascript
var intervalIntersection = function(firstList, secondList) {
    let i = 0, j = 0;
    let result = [];
    
    while (i < firstList.length && j < secondList.length) {
        let start = Math.max(firstList[i][0], secondList[j][0]);
        let end = Math.min(firstList[i][1], secondList[j][1]);
        
        if (start <= end) {
            result.push([start, end]);
        }
        
        if (firstList[i][1] < secondList[j][1]) {
            i++;
        } else {
            j++;
        }
    }
    
    return result;
};
```

## Example Dry Run
Let's dry run the solution for the first example:

```javascript
let firstList = [[0,2],[5,10],[13,23],[24,25]];
let secondList = [[1,5],[8,12],[15,24],[25,26]];
console.log(intervalIntersection(firstList, secondList)); // [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]

Initial state: i = 0, j = 0
Compare [0, 2] and [1, 5]: Intersection is [1, 2]. Increment i.
State: i = 1, j = 0
Compare [5, 10] and [1, 5]: Intersection is [5, 5]. Increment j.
State: i = 1, j = 1
Compare [5, 10] and [8, 12]: Intersection is [8, 10]. Increment i.
State: i = 2, j = 1
Compare [13, 23] and [8, 12]: No intersection. Increment j.
State: i = 2, j = 2
Compare [13, 23] and [15, 24]: Intersection is [15, 23]. Increment i.
State: i = 3, j = 2
Compare [24, 25] and [15, 24]: Intersection is [24, 24]. Increment j.
State: i = 3, j = 3
Compare [24, 25] and [25, 26]: Intersection is [25, 25]. Increment i.
Result is [[1, 2], [5, 5], [8, 10], [15, 23], [24, 24], [25, 25]].
```

## Time Complexity
This solution ensures an `O(m+n)` time complexity where m and n are the lengths of firstList and secondList respectively.
