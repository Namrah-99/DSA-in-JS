# 167. Two Sum II - Input Array Is Sorted

## Leetcode Problem
https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
Using the `two-pointer approach`. This approach takes advantage of the sorted nature of the input array to efficiently find the two numbers that sum up to the target.

#### Two Pointers:
- Initialize two pointers, `left` starting at the beginning (index 0) and `right` starting at the end (index numbers.length - 1) of the array.
#### Iterate and Check Sum:
- Calculate the sum of the elements at the `left` and `right` pointers.
- If the `sum` equals the `target`, return the indices incremented by 1 (since the array is 1-indexed).
- If the `sum` is less than the `target`, increment the `left` pointer to increase the `sum`.
- If the `sum` is greater than the `target`, decrement the `right` pointer to decrease the `sum`.
#### Loop Until Solution Found:
- Continue this process until the two pointers meet. The problem guarantees that there is exactly one solution, so the loop will always find and return the correct indices.

## Solution Code
```javascript
var twoSum = function(numbers, target) {
    let left = 0, right = numbers.length - 1;
    let sum = 0;
    while(left<right){
        sum = numbers[left] + numbers[right]
        if(sum === target){
            return [left+1,right+1]
        }else if(sum < target){
            left++;
        }else{
            right--;
        }
    }
};

console.log(twoSum([2,7,11,15], 9)) // [1,2]
console.log(twoSum([2,3,4], 6)) // [1,3]
console.log(twoSum([-1,0], -1)) // [1,2]
```

## Complexity Analysis
- Time Complexity: `O(n)` because each element in the array is processed at most once by the `left` and `right` pointers.
- Space Complexity: `O(1)` because no extra space is used other than a few variables.

