# 715. Range Module

## Leetcode Problem
https://leetcode.com/problems/range-module/description/

## Approach
The RangeModule class uses a combination of linear search and interval merging to manage and query intervals. 

### Explanation of the Code
Here's a breakdown of the approach used in the code:

#### 1. Initialization:
- The class initializes an empty list to store intervals.
- `constructor()`: Initializes the ranges array to an empty array.
#### 2. Adding a Range:
- `add(left, right)`: This method adds a new interval `[left, right)` to the ranges array.
- Steps:
    - 1. Iterate through each interval in ranges.
    - 2. Compare the new interval with each existing interval:
          - If the new interval is entirely to the left of the current interval, insert it before the current interval.
          - If the new interval is entirely to the right of the current interval, skip to the next interval.
          - If the new interval overlaps with the current interval, merge them by adjusting the left and right boundaries to encompass both intervals.
    - 3. After processing all intervals, if the new interval hasn't been added yet, append it to newRanges.
    - 4. Update ranges to newRanges.
#### 3. Removing a Range:
- `remove(left, right)`: This method removes the interval `[left, right)` from the ranges array.
- Steps:
    - 1. Iterate through each interval in ranges.
    - 2. Compare the interval to be removed with each existing interval:
          - If the interval to be removed is entirely to the left or right of the current interval, keep the current interval unchanged.
          - If the interval to be removed overlaps with the current interval, split the current interval into two (if necessary) and exclude the part that overlaps with `[left, right)`.
    - 3. Update ranges to newRanges.
#### 4. Querying a Range:
- `query(left, right)`: This method checks if the interval `[left, right)` is fully covered by any interval in ranges.
- Steps:
    - 1. Iterate through each interval in ranges.
    - 2. Check if the query interval is completely within any existing interval.
    - 3. If found, return true; otherwise, return false.

## Solution Code
```javascript
class RangeModule {
    constructor() {
         this.ranges=[];
    }
   // add a new interval range
   add(left,right){
       let newRanges = []; let isAdded = false;
       // iterate thru each element of this.ranges
       for(let [start,end] of this.ranges){
           // new interval on left side of current interval
           if(right < start){
               // now for placing the new interval first and then the current interval 
               if(!isAdded){
                   newRanges.push([left,right])
                   isAdded = true;
               }
                newRanges.push([start,end]);
           }
           // new interval on right side of current interval
           else if(left > end){
                newRanges.push([start,end]);
                // later on adding the new interval when checking if new interval added flag is false or true
           }
           // new interval on in between side of current interval
            else{
                left = Math.min(left, start);
                right = Math.max(right, end)
            }
       }
       // check if new interval gets added before or just set the left and right ranges
       if(!isAdded){
           newRanges.push([left,right]); 
           isAdded = true
       }
       
       this.ranges = newRanges;
       console.log(this.ranges)
   }
   // remove a new interval range
   remove(left,right){
       let newRanges = [];
       
       for (let [start,end] of this.ranges){
            // check if new interval lies within the current interval range
            if(end <= left || right <= start){
                newRanges.push([start,end])
            }
            // check if new interval lies in bewteen the current interval range
            else{
                // separate start to left interval range
                if(start < left){
                    newRanges.push([start,left])
                }
                // separate right to end interval range
                if(right < end){
                    newRanges.push([right,end])
                }
            }       
       }
       
       this.ranges = newRanges;
       console.log(this.ranges)
   }
   // query an interval
   query(left,right){
       for (let [start,end] of this.ranges){
           // if provided values lies in between the interval
           if(left >= start && right <= end){
               return true
           }
       }
         return false
   }
}

let range = new RangeModule();
range.add(10,20);
console.log(range.query(10, 14)); // true
range.remove(14, 16);
console.log(range.query(10, 14)); // true
console.log(range.query(13, 15)); // false
console.log(range.query(16, 17)); // true
```

## Example Dry Run
```
- 1. Adding [10, 20):
    - ranges = [] initially.
    - newRanges = [].
    - Since ranges is empty, add [10, 20) to newRanges.
    - ranges = [[10, 20]].

- 2. Querying [10, 14):
    - Check if [10, 14) is within any interval in ranges.
    - [10, 14) is within [10, 20).
    - Returns true.

- 3. Removing [14, 16):
    - ranges = [[10, 20]].
    - newRanges = [].
    - Split [10, 20) into [10, 14) and [16, 20).
    - ranges = [[10, 14], [16, 20]].

- 4. Querying [10, 14):
    - Check if [10, 14) is within any interval in ranges.
    - [10, 14) is within [10, 14].
    - Returns true.

- 5. Querying [13, 15):
    - Check if [13, 15) is within any interval in ranges.
    - [13, 15) is not fully within any interval.
    - Returns false.

- 4. Querying [16, 17):
    - Check if [16, 17) is within any interval in ranges.
    - [16, 17) is within [16, 20].
    - Returns true.
```

## Time Complexity

- Add Range:
    - Iterates through all intervals to find the correct place to add and potentially merge intervals.
    - Time complexity: `O(n)`, where n is the number of intervals.
- Remove Range:
    - Iterates through all intervals to remove the specified range and potentially split intervals.
    - Time complexity: `O(n)`.
- Query Range:
    - Iterates through all intervals to check if the specified range is covered.
    - Time complexity: `O(n)`.

In summary, the overall approach involves linear scans of the intervals for each operation (add, remove, query), making the time complexity `O(n)` for each operation.
