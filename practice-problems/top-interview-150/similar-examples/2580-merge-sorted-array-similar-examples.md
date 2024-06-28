# 2580. Count Ways to Group Overlapping Ranges

## Leetcode Problem
https://leetcode.com/problems/count-ways-to-group-overlapping-ranges/description/

## Approach

The approach used in the countWays function involves a combination of sorting and a greedy algorithm to determine the number of non-overlapping groups, followed by a modular arithmetic calculation to determine the number of ways to split the ranges into groups. 

## Steps and Approach

### 1. Sorting:
- The function starts by sorting the `ranges` array. The sorting is done first by the starting point (`starti`) of each range, and if two ranges have the same starting point, they are sorted by their ending point (`endi`).
- This sorting step ensures that we can process the ranges in a sequential manner to determine overlaps efficiently.
### 2. Greedy Algorithm to Count Non-overlapping Groups:
- Initialize `groups` to count the number of distinct non-overlapping groups.
- Initialize `end` to keep track of the end point of the last added range in the current group.
- Iterate through the sorted ranges:
    - If the current range's start point is greater than the `end` of the last range, it indicates a new non-overlapping group, so increment `groups` and update `end` to the end of the current range.
    - If the current range overlaps with the last range (i.e., its start point is less than or equal to `end`), update `end` to the maximum of the current range's end point and the last range's end point.
- This step ensures that any overlapping ranges are kept in the same group, while non-overlapping ranges start a new group.
### 3. Calculating Number of Ways Using Modular Arithmetic:
- The number of ways to split `G` groups into two groups is 2^G , as each group can independently be in either of the two groups.
- To avoid overflow and adhere to the problem's constraints, compute `2^G mod (10^9 + 7)`
    - Initialize `result` to 1.
    - Multiply `result` by 2 for `G` times, taking the modulus `MOD` at each step to keep the result within bounds.

## Solution Code
```javascript
function countWays(ranges) {
    const MOD = 1_000_000_007;
    let groups = 0, end = -1;
    
    // Sorting ranges by their starting point and then by their ending points
    ranges.sort((a,b)=>a[0]-b[0] || a[1]-b[1]);

    // Count the number of non-overlapping groups
    for(let [start,stop] of ranges){
        if(start > end){
            groups++;
            end = stop;
        }else{
            end = Math.max(end, stop)
        }
    }

    // Number of ways to split the ranges into groups: (2^groups) % MOD 
    let result = 1;
    for(let i =0; i<groups; i++){
        result = (result * 2) % MOD;
    }

    return result;
}

// Example usage:
console.log(countWays([[6,10],[5,15]])); // Output: 2
console.log(countWays([[1,3],[10,20],[2,5],[4,8]])); // Output: 4
```

## Explanation of Approach
The approach can be classified as follows:
- **Sorting:** The initial sorting step helps in efficiently processing the ranges in a way that makes it easier to detect overlaps and non-overlapping groups.
- **Greedy Algorithm:** The greedy part of the algorithm is in how it processes each range and determines whether it should be part of the current group or start a new group. By always extending the current group to include overlapping ranges, we ensure the minimum number of groups is formed.
- **Modular Arithmetic:** This step ensures that the large numbers resulting from 2^𝐺 are managed within the limits specified by the problem using the modulus operation.

## Complexity Analysis
### Time Complexity: `O(nlogn)`
- Sorting the ranges takes O(nlogn) time.
- The subsequent iteration through the ranges is O(n).
### Space Complexity: `O(1)`
- The algorithm uses a constant amount of additional space for variables like groups and end.
By combining sorting and a greedy algorithm, this approach efficiently groups overlapping ranges and calculates the number of ways to split them into two groups, adhering to the constraints of the problem.
