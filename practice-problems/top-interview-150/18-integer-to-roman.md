# 12. Integer to Roman

## Leetcode Problem
https://leetcode.com/problems/integer-to-roman/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Understanding
The task is to convert a given integer into its Roman numeral representation. Roman numerals are constructed using the following seven symbols:

|    Symbol    |      Value   |
|--------------|--------------|
|       I      |       1      |
|       V      |       5      |
|       X      |       10     |
|       L      |       50     |
|       C      |       100    |
|       D      |       500    |
|       M      |       1000   |

#### Rules for Roman Numerals
- **General Rule:** Symbols are placed from largest to smallest from left to right. For example, the number 2 is written as II in Roman numerals, just two ones added together.
- **Subtractive Notation:** There are six instances where subtraction is used:
    - I can be placed before V (5) and X (10) to make 4 (IV) and 9 (IX).
    - X can be placed before L (50) and C (100) to make 40 (XL) and 90 (XC).
    - C can be placed before D (500) and M (1000) to make 400 (CD) and 900 (CM).
#### Examples
Example 1:
```
Input: num = 3749
Output: "MMMDCCXLIX"
```
Explanation:
- 3000 = MMM (M + M + M)
- 700 = DCC (D + C + C)
- 40 = XL (X less than L)
 -9 = IX (I less than X)

Example 2:
```
Input: num = 58
Output: "LVIII"
```
Explanation:
- 50 = L
- 8 = VIII (V + I + I + I)

Example 3:
```
Input: num = 1994
Output: "MCMXCIV"
```
Explanation:
- 1000 = M
- 900 = CM (C less than M)
- 90 = XC (X less than C)
- 4 = IV (I less than V)
#### Constraints
The input number num will be in the range `1 <= num <= 3999`.

## Approach
The approach involves iterating through the integer and appending the appropriate Roman numeral symbols. This can be efficiently done in O(n) time complexity by using predefined mappings of numbers to Roman numeral symbols.

## Solution Code
```javascript
var intToRoman = function (num) {
    // Define the mapping of integers to Roman numerals
    const values = [
        1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1
    ];
    const symbols = [
        "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"
    ];
    let roman = ''
    // Iterate through the values array
    values.forEach((value, index) => {
        while (num >= value) {
            // Append the corresponding symbol while num is greater than or equal to the current value
            roman += symbols[index]
            num -= value
        }
    })
    return roman
};
// Example usage:
console.log(intToRoman(9))
console.log(intToRoman(3)); // Output: "III"
console.log(intToRoman(58)); // Output: "LVIII"
console.log(intToRoman(1994)); // Output: "MCMXCIV"
```

## Complexity Analysis
- **Time Complexity:** The time complexity of the solution is `O(n)`, where n is the number of digits in the input number. This is because we iterate through each value in the values array, and for each value, we might append the corresponding symbol multiple times until the remaining number is less than the current value.
- **Space Complexity:** The space complexity is `O(1)` because we are using a constant amount of extra space to store the mappings and the resultant Roman numeral string. The space used by the output string is not considered extra space.
