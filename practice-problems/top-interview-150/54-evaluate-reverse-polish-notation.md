# 150. Evaluate Reverse Polish Notation

## Leetcode Problem
https://leetcode.com/problems/evaluate-reverse-polish-notation/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To evaluate an arithmetic expression given in Reverse Polish Notation (RPN), we can use a `stack-based approach`. RPN, also known as `postfix notation`, places operators after their operands. This allows for easy evaluation using a stack to `store operands and apply operators` as they are encountered.

## Approach
### Stack-based Evaluation:
- Iterate through each token in the tokens array.
- If the token is an operand (integer), push it onto the stack.
- If the token is an operator (`+`, `-`, `*`, `/`), pop the necessary number of operands from the stack, apply the operator, and push the result back onto the stack.

### Operations:
- For addition (`+`), subtraction (`-`), and multiplication (`*`), pop two operands, perform the operation, and push the result.
- For division (`/`), ensure to handle integer division as specified (truncates towards zero).

### Edge Cases:
- Single operand tokens or single operator tokens.
- Division by zero is explicitly guaranteed not to occur.
- All calculations are within the range of a 32-bit signed integer.

## Solution Code
```javascript
function evalRPN(tokens) {
    const stack = [];
    
    for (let token of tokens) {
        if (token === '+' || token === '-' || token === '*' || token === '/') {
            const b = stack.pop();
            const a = stack.pop();
            
            if (token === '+') {
                stack.push(a + b);
            } else if (token === '-') {
                stack.push(a - b);
            } else if (token === '*') {
                stack.push(a * b);
            } else if (token === '/') {
                // JavaScript division rounds towards zero, so Math.trunc is not needed
                stack.push(Math.trunc(a / b));
            }
        } else {
            stack.push(parseInt(token)); // Push operand as integer
        }
    }
    
    return stack.pop(); // Result will be the final value left in the stack
}
```

- Math.trunc(): function in JavaScript returns the integer part of a number by removing any fractional digits. It effectively truncates towards zero.

### Example Usage:
```javascript
console.log(evalRPN(["2","1","+","3","*"])); // Output: 9
console.log(evalRPN(["4","13","5","/","+"])); // Output: 6
console.log(evalRPN(["10","6","9","3","+","-11","*","/","*","17","+","5","+"])); // Output: 22
```
### Explanation of Examples:
```css
Example 1: ["2","1","+","3","*"] evaluates to ((2 + 1) * 3) = 9.
Example 2: ["4","13","5","/","+"] evaluates to (4 + (13 / 5)) = 6.
Example 3: Complex expression evaluates step-by-step using the stack, handling operations in the correct order according to RPN rules.
```

## Complexity Analysis:
- Time Complexity: `O(n)` where `n` is the number of tokens. We iterate through each token once and perform constant-time operations with the stack.
- Space Complexity: `O(1)` additional space beyond the input tokens. We use a single stack to store operands, maintaining constant space.

