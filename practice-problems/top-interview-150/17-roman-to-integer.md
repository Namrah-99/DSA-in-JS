# 13. Roman to Integer

## Leetcode Problem
https://leetcode.com/problems/roman-to-integer/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
Roman numerals are represented by seven symbols with specific values:

|    Symbol    |      Value   |
|--------------|--------------|
|       I      |       1      |
|       V      |       5      |
|       X      |       10     |
|       L      |       50     |
|       C      |       100    |
|       D      |       500    |
|       M      |       1000   |

Roman numerals are typically written from largest to smallest from left to right. However, certain numerals involve subtraction, where a smaller numeral precedes a larger one. These cases include:

- I before V (4) and X (9)
- X before L (40) and C (90)
- C before D (400) and M (900)
Given a string representing a Roman numeral, the goal is to convert it to an integer.

### Examples
```
Input: s = "III"
Output: 3
Explanation: III = 3
```
```
Input: s = "LVIII"
Output: 58
Explanation: L = 50, V = 5, III = 3
```
```
Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90, IV = 4
```
### Constraints
- 1 <= s.length <= 15
- s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M')
- It is guaranteed that s is a valid Roman numeral within the range [1, 3999]

## Approach
To convert a Roman numeral to an integer:

- Iterate through the characters of the string.
- Add the value of the current character to the result.
- If the current character is larger than the previous character, subtract twice the value of the previous character (to account for the previous addition).
This approach ensures that the subtraction cases are handled correctly.

## Solution Code
```javascript
function romanToInt(s) {
    const romanMap = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    };
    
    let total = 0;
    let prevValue = 0;
    
    for (let char of s) {
        let currentValue = romanMap[char];
        total += currentValue;
        
        // If previous value is less, subtract twice the previous value
        if (prevValue < currentValue) {
            total -= 2 * prevValue;
        }
        
        prevValue = currentValue;
    }
    
    return total;
}

// Example usage:
console.log(romanToInt("III")); // Output: 3
console.log(romanToInt("LVIII")); // Output: 58
console.log(romanToInt("MCMXCIV")); // Output: 1994
```

## Key Logic
```javascript
if (prevValue < currentValue) {
    total -= 2 * prevValue;
}
```
#### Explanation:
In Roman numerals, if a smaller numeral appears before a larger numeral, it indicates subtraction. This piece of logic ensures that we correctly handle these subtraction cases.

#### How It Works
- Current and Previous Values:
    - `currentValue` is the value of the current Roman numeral character.
    - `prevValue` is the value of the previous Roman numeral character.
- Subtraction Rule:
    - If `prevValue` is less than `currentValue`, it means the previous numeral should be subtracted instead of added.
    - To correct this, we subtract twice the `prevValue`. This effectively reverses the initial addition of `prevValue` and then subtracts it.

The logic if (`prevValue` < `currentValue`) { `total` -= 2 * `prevValue`; } ensures that when a smaller numeral precedes a larger numeral, the smaller numeral is subtracted. This logic handles cases where Roman numerals involve subtraction, such as `IV, IX, XL, XC, CD, and CM`. By reversing the addition and then subtracting the smaller numeral, we accurately calculate the integer value.

## Complexity Analysis
- Time Complexity: `O(n)`, where `n` is the length of the string `s`. Each character is processed exactly once.
- Space Complexity: `O(1)`, as we use a fixed amount of extra space for the map and a few integer variables.
