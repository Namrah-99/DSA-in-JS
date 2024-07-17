# 224. Basic Calculator

## Leetcode Problem 
https://leetcode.com/problems/basic-calculator/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of evaluating a basic arithmetic expression given in string form (`s`), we can use the Shunting Yard algorithm combined with a `stack-based approach` for evaluation. This method allows us to handle operators and parentheses efficiently without using recursion or the `eval()` function, ensuring O(n) time complexity and O(1) space complexity (excluding the space used by input and output).

## Approach

### Initialization:
- Use a stack to store operands and operators as we parse through the string `s`.
- Use variables `sign` to track the current sign and `result` to accumulate the final result of the expression.
- Start with `sign` initialized to `1` (positive) and result initialized to `0`.

### Parsing the String:
- Iterate through each character of `s`.
- Handle digits to form complete numbers and update the `result`.
- Toggle the sign when encountering '+' or '-'.
- Use a stack to handle '(' and ')' to manage nested expressions.

### Algorithm Details:
- Digits: Accumulate digits to form numbers, considering the potential for multi-digit numbers.
- Operators: Update the current `sign` based on encountered '+' or '-'.
- Parentheses: Use the stack to handle nested expressions. Push current `result` and `sign` onto the stack when encountering '(', and pop and evaluate when encountering ')'.
- Whitespace: Skip whitespace characters.

### Final Calculation:
- After parsing through the string, ensure any remaining accumulated `result` is added to the final `result`.

### Edge Cases:
- Handle expressions with spaces.
- Handle expressions with nested parentheses.
- Ensure correct handling of unary '-' operators.
- Ensure correct accumulation and evaluation of the final `result`.

## Example Walkthrough:
Let's walkthrough the example `s = "(1+(4+5+2)-3)+(6+8)"`:

1. Initialize `sign = 1`, `result = 0`, and a stack.

2. Iterate through each character:
```lua
'(' - Push result (0) and sign (1) onto the stack, reset result to 0.
'1' - Parse number and update result to 1.
'+' - Update sign to 1.
'(' - Push result (1) and sign (1) onto the stack, reset result to 0.
'4' - Parse number and update result to 4.
'+' - Update sign to 1.
'5' - Parse number and update result to 9.
'+' - Update sign to 1.
'2' - Parse number and update result to 11.
')' - Evaluate sub-expression on the stack: result = 1 + 11 = 12.
'-' - Update sign to -1.
'3' - Parse number and update result to 3.
')' - Evaluate sub-expression on the stack: result = 0 - 3 = -3.
'+' - Update sign to 1.
'(' - Push result (-3) and sign (1) onto the stack, reset result to 0.
'6' - Parse number and update result to 6.
'+' - Update sign to 1.
'8' - Parse number and update result to 14.
')' - Evaluate sub-expression on the stack: result = -3 + 14 = 11.
```
3. The final result after parsing the entire string is `23`.

## Solution Code
```javascript
function calculate(s) {
    let result = 0;
    let sign = 1;
    let i = 0;
    const stack = [];
    
    while (i < s.length) {
        const char = s[i];
        
        if (char === ' ') {
            i++;
            continue;
        } else if (char === '+') {
            sign = 1;
            i++;
        } else if (char === '-') {
            sign = -1;
            i++;
        } else if (char === '(') {
            stack.push(result);
            stack.push(sign);
            result = 0;
            sign = 1;
            i++;
        } else if (char === ')') {
            result = stack.pop() * result + stack.pop();
            i++;
        } else {
            let num = 0;
            while (i < s.length && /[0-9]/.test(s[i])) {
                num = num * 10 + parseInt(s[i]);
                i++;
            }
            result += sign * num;
        }
    }
    
    return result;
}
```

## Complexity Analysis:
### Time Complexity: 
`O(n)`, where `n` is the length of the string `s`. We process each character of the string exactly once.
### Space Complexity: 
`O(1)`, excluding the space used by the input and output. We use a constant amount of extra space for variables and the stack.
