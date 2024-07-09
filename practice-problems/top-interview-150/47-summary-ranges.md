# 228. Summary Ranges

## Leetcode Problem
https://leetcode.com/problems/summary-ranges/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of finding the smallest sorted list of ranges that cover all numbers in a sorted unique integer array `nums`, we can use a `hash table approach` in JavaScript. This approach ensures `O(n)` time complexity, where `n` is the number of elements in `nums`. Let's walk through the solution step-by-step:

Given a sorted unique integer array `nums`, we need to:
- Identify continuous ranges of numbers.
- Format these ranges as specified:
    - If a range consists of a single number, format it as "a".
    - If a range consists of more than one number, format it as "a->b".

## Approach
1. **Initialization:** Start with an empty array result to store formatted ranges.
2. **Iterate through nums:**
    - For each number `num`:
        - If it's the start of a new range (i.e., `num` is not consecutive with the previous `number + 1`):
            - If there was a previous range being built (`start !== undefined`), push it to `result`.
            - Set `start` to the current `num`.
        - Update `end` to `num` as long as `num` is consecutive with the previous number.
3. **Finalization:** After iterating through `nums`, push the last range (if any) to `result`.
4. **Output:** Return `result`, which contains the smallest sorted list of ranges covering all numbers in `nums`.

## Solution Code
```javascript
var summaryRanges = function (nums) {
    const result = [];
    let start, end;

    for (let i = 0; i < nums.length; i++) {
        if (start === undefined) {
            start = nums[i];
            end = nums[i];
        } else if (nums[i] === end + 1) {
            end = nums[i];
        } else {
            result.push(formatRange(start, end));
            start = nums[i];
            end = nums[i];
        }
    }

    if (start !== undefined) {
        result.push(formatRange(start, end));
    }

    return result;
};

function formatRange(start, end) {
    return start === end ? `${start}` : `${start}->${end}`;
}
// Example usage:
console.log(summaryRanges([0,1,2,4,5,7])); // Output: ["0->2","4->5","7"]
console.log(summaryRanges([0,2,3,4,6,8,9])); // Output: ["0","2->4","6","8->9"]
```

## Complexity Analysis

### Time Complexity:
- The algorithm iterates through `nums` exactly once, which takes `O(n)` time.
- Building and formatting each range operation is `O(1)`.
- Therefore, the overall time complexity is `O(n)`.
### Space Complexity:
- The space complexity is `O(1)` auxiliary space, as the algorithm only uses a constant amount of extra space for variables (`result`, `start`, `end`).
- The space used for result to store output ranges is `O(n)` in the worst case, where each element in `nums` could potentially be a separate range.
