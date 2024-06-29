# 169. Majority Element

## Leetcode Problem
https://leetcode.com/problems/majority-element/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to find the majority element in an array. The majority element is defined as the element that appears more than ⌊n / 2⌋ times in the array. You are guaranteed that such an element always exists in the array.
### Examples
##### Example 1:
```
Input: nums = [3,2,3]
Output: 3
```
- Explanation: The element 3 appears more than ⌊3/2⌋ = 1.5 times, which means more than once.
##### Example 2:
```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```
Explanation: The element 2 appears more than ⌊7/2⌋ = 3.5 times, which means more than three times.
### Constraints
- n == nums.length
- 1 <= n <= 5 * 10^4
- -10^9 <= nums[i] <= 10^9

### Follow-up
The problem can be solved in linear time and with constant space using the `Boyer-Moore Voting Algorithm`.

## Approach
The `Boyer-Moore Voting Algorithm` is an efficient way to find the majority element with the following steps:
##### Initialize a candidate and count:
- Start with candidate as null and count as 0.
##### Iterate through the array:
- For each element in the array, if count is 0, set the candidate to the current element and set count to 1.
    - If the current element is the same as the candidate, increment the count.
    - If the current element is different from the candidate, decrement the count.
##### Return the candidate:
- By the end of the array, the candidate will be the majority element.

## Solution Code
```javascript
// var majorityElement = function(nums) {
//     let majority = nums.length/2;
//     let mapNums = new Map();
//     let max={'val':0,'count':0}
//     for(let j=0;j<nums.length;j++){
//         mapNums[nums[j]] = (mapNums[nums[j]] || 0) + 1;
//         if(mapNums[nums[j]] >= majority || max['count']<=mapNums[nums[j]]){
//             max['val']=nums[j]; max['count']=mapNums[nums[j]];
//         }
//     }
//     return max['val']
// };
var majorityElement = function(nums) {
     let candidate = null;
    let count = 0;

    // Phase 1: Find a candidate
    for (let num of nums) {
        if (count === 0) {
            candidate = num;
        }
        count += (num === candidate) ? 1 : -1;
    }

    // Phase 2: The candidate is guaranteed to be the majority element
    return candidate;
}

// Example usage:
console.log(majorityElement([3,2,3])); // Output: 3
console.log(majorityElement([2,2,1,1,1,2,2])); // Output: 2
console.log(majorityElement([1, 1, 1, 2, 2, 3])); // Output: 1
console.log(majorityElement([0, 0, 1, 1, 1, 1, 2, 3, 3])); // Output: 1
```

## Complexity Analysis
#### Time Complexity
- The algorithm runs in `O(n)` time because it makes a single pass through the array.
#### Space Complexity
- The algorithm uses `O(1)` extra space because it only uses a few variables for counting and storing the candidate.

This approach guarantees finding the majority element efficiently with respect to both time and space.
