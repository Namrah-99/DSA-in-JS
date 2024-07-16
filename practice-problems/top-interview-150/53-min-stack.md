# 155. Min Stack

## Leetcode Problem
https://leetcode.com/problems/min-stack/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To design a MinStack that supports operations with constant time complexity (`O(1)`), including `push`, `pop`, `top`, and `getMin`, we need to leverage additional space to efficiently track the minimum element at any point in the stack.

## Approach:
### Using Two Stacks:
- We'll use two stacks:
  - One stack (`stack`) to store all elements pushed onto the MinStack.
  - Another stack (`minStack`) to keep track of the minimum values.
- Operations:
  - Push Operation:
    - Push the element onto the `stack`.
    - Update the `minStack` to push the current minimum value (or the new element if it's smaller) onto it.
  - Pop Operation:
    - Pop the top element from both `stack` and `minStack`.
  - Top Operation:
    - Return the top element of `stack` without modifying the stack.
  - GetMin Operation:
    - Return the top element of `minStack`, which always holds the current minimum element.

### Edge Cases:
- Operations on an empty stack should be handled gracefully as per problem constraints.
- Dealing with sequences where the minimum value changes dynamically due to pushes and pops.

## Complexity Analysis:
- Time Complexity: All operations (`push`, `pop`, `top`, `getMin`) are `O(1)`. This is achieved by using additional space (`minStack`) to store the minimum values.
- Space Complexity: `O(n)` where `n` is the number of elements pushed onto the stack. This is primarily due to the space used by `stack` and `minStack`, both growing with the number of elements pushed.

```javascript
class MinStack {
    constructor() {
        this.stack = [];
        this.minStack = [];
    }

    push(data) {
        this.stack.push(data);
        if (this.minStack.length === 0 || data <= this.getMin()) {
            this.minStack.push(data)
        }
    }

    pop() {
        let poppedEle = this.stack.pop();
        if (poppedEle === this.getMin()) {
            this.minStack.pop();
        }
    }

    top() {
        return this.stack[this.stack.length - 1]
    }

    getMin() {
        return this.minStack[this.minStack.length - 1]
    }
}
```
### Example Usage:
```javascript
const minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
console.log(minStack.getMin()); // Output: -3
minStack.pop();
console.log(minStack.top());    // Output: 0
console.log(minStack.getMin()); // Output: -2
```
### Explanation of Examples:
```css
- After pushing -2, 0, and -3, the minimum element in the stack is -3.
- After popping -3, the top element is 0.
- The minimum element remains -2 after popping -3.
```
This implementation efficiently manages the operations with constant time complexity by using an auxiliary stack (`minStack`) to track the minimum values at each point in the main stack (`stack`). It handles all specified edge cases and maintains optimal performance across all operations.
