# 202. Happy Number

## Leetcode Problem
https://leetcode.com/problems/happy-number/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
A happy number is defined by the following process:
- Starting with any positive integer `n`, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals `1` (where it will stay), or it loops endlessly in a cycle which does not include `1`.
- Numbers for which this process ends in 1 are considered happy.

## Approach
1. **Hash Set Usage:** Use a hash set (`visited`) to keep track of numbers that have already been processed to detect cycles.

2. **Algorithm Steps:**
- Implement a helper function `sumOfSquaresOfDigits` to compute the sum of the squares of the digits of a number.
- Initialize `n` as the current number to process.
- Use a loop to repeatedly compute the sum of squares of digits of `n` until `n` equals `1` or until `n` is detected in the `visited` set (indicating a cycle).
- If `n` becomes `1` during this process, return `true` (indicating `n` is a happy number).
- If a cycle is detected (i.e., `n` is already in `visited`), return `false`.

3. **Edge Cases:** The algorithm handles the edge case where `n=1` directly returns `true`, as 1 itself is a happy number.

## Solution Code
```javascript
var isHappy = function (n) {
    let visited = new Set();

    while (n !== 1 && !visited.has(n)) {
        visited.add(n);
        n = sumOfSqrOfDigits(n);
    }

    return n === 1;
};

function sumOfSqrOfDigits(n) {
    let sum = 0;
    while (n > 0) {
        let digit = n % 10;
        sum += digit * digit;
        n = Math.floor(n / 10);
    }
    return sum
}

// Example usage:
console.log(isHappy(19)); // Output: true
console.log(isHappy(2)); // Output: false
```

## Complexity Analysis
### Time Complexity:
- The `sumOfSquaresOfDigits` function runs in `O(log n)` time complexity, as it processes each digit of `n`.
- In the worst case, the while loop in `isHappy` iterates multiple times until either `n` becomes `1` or a cycle is detected.
- Therefore, the overall time complexity is `O(n)`, where `n` is the number of digits processed until determining the result.
### Space Complexity:
- The space complexity is `O(n)` due to the hash set visited potentially storing all numbers up to `n` in the worst case.
- Auxiliary space used by other variables (like `sum` and `digit`) is constant `O(1)` space.
