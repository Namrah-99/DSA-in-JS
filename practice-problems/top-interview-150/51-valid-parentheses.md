# 20. Valid Parentheses

## Leetcode Problem 
https://leetcode.com/problems/valid-parentheses/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To determine if a given string of parentheses, brackets, and braces is valid according to the specified rules, we can use a stack-based approach. This approach ensures O(n) time complexity and O(1) space complexity (excluding the input string space).

## Approach:
- Using a Stack:
  - We can utilize a stack to keep track of opening brackets as we traverse the string.
- Matching Logic:
  - When encountering an opening bracket (`(`, `{`, `[`), push it onto the stack.
  - When encountering a closing bracket (`)`, `}`, `]`):
    - Check if the stack is not empty.
    - Pop the top of the stack and ensure it matches the corresponding opening bracket (`(` for `)`, `{` for `}`, `[` for `]`).
    - If it doesn't match or the stack is empty when a closing bracket is encountered, the string is invalid.
- Completion Check:
  - After processing the string, if the stack is empty, all brackets have been matched correctly.

## Edge Cases Handled:
- Strings with odd lengths (where one bracket cannot have a pair).
- Strings where brackets are not properly nested or closed.
- Strings with only opening or closing brackets.
- Strings with multiple valid nested brackets.

## Complexity Analysis:
- Time Complexity: `O(n)` where `n` is the length of the input string. We iterate through the string once and perform constant-time operations with the stack.
- Space Complexity: `O(1)` excluding the input string space because we use a fixed-size stack (maximum size determined by the number of opening brackets).

## Solution Code
```javascript
var isValid = function(s) {
    let stack = [];
    let matchMap= {
        ')': '(',
        '}': '{',
        ']': '['
    }
    for(let ch of s){
        if(ch === '(' || ch === '{' || ch === '['){
            // push
            stack.push(ch);
        }else{
            // pop
            let popEle = stack.pop();
            if(popEle !== matchMap[ch]){
                return false
            }
        }
    }

    return stack.length === 0
};
```
### Example Usage:
```css
console.log(isValid("()"));        // Output: true
console.log(isValid("()[]{}"));    // Output: true
console.log(isValid("(]"));        // Output: false
console.log(isValid("([)]"));      // Output: false
console.log(isValid("{[]}"));      // Output: true
```
### Explanation:
- Example 1: "()" is valid because every opening parenthesis has a corresponding closing parenthesis in the correct order.
- Example 2: "()[]{}" is valid because every opening bracket type has a corresponding closing bracket type in the correct order.
- Example 3: "(]" is invalid because the closing bracket ] does not match the opening bracket ( in correct order.

This approach efficiently checks the validity of the bracket string using a stack to ensure that each opening bracket has a matching and correctly ordered closing bracket. It handles all specified edge cases and maintains optimal time and space complexity.
