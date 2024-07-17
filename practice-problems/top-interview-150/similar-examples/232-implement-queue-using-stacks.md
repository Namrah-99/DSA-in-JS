# 232. Implement Queue using Stacks

## Leetcode Problem
https://leetcode.com/problems/implement-queue-using-stacks/description/

## Problem Explanation
To implement a queue using two stacks and ensure that each operation is amortized `O(1)` time complexity, let's break down the approach and the operations involved:

## Approach:
We can implement a queue using two stacks to achieve `FIFO` (First-In-First-Out) behavior. Here's how:

1. Stack Usage:
- Input Stack (`inputStack`): Used for pushing elements in the order they are received. This stack will maintain the order of elements as they are added.
- Output Stack (`outputStack`): Used for popping and peeking elements in the order they would appear in a queue. This stack will help achieve `FIFO` behavior when elements are dequeued.

2. Operations:
- Push Operation (`push(x)`):
  - Simply push the element `x` onto `inputStack`.
- Pop Operation (`pop()`):
  - Check if `outputStack` is empty. If it is, transfer all elements from `inputStack` to `outputStack` while maintaining their order. Then pop the top element from `outputStack`.
  - If `outputStack` is not empty, directly pop the top element from `outputStack`.
- Peek Operation (`peek()`):
  - Similar to `pop()`, ensure outputStack has elements if it's empty by transferring elements from `inputStack`. Then peek at the top element of `outputStack`.
- Empty Operation (`empty()`):
  - Check if both `inputStack` and `outputStack` are empty. If both are empty, the queue is empty.

## Solution Code
```javascript
class MyQueue {
    constructor() {
        this.inputStack = [];
        this.outputStack = [];
    }

    push(x) {
        this.inputStack.push(x);
    }

    pop() {
        this._transferIfNeeded();
        return this.outputStack.pop();
    }

    peek() {
        this._transferIfNeeded();
        return this.outputStack[this.outputStack.length - 1];
    }

    empty() {
        return this.inputStack.length === 0 && this.outputStack.length === 0;
    }

    _transferIfNeeded() {
        if (this.outputStack.length === 0) {
            while (this.inputStack.length > 0) {
                this.outputStack.push(this.inputStack.pop());
            }
        }
    }
}
```
## Complexity Analysis:

### Time Complexity:
- Push Operation (`push(x)`): `O(1)` amortized time complexity. Each push operation involves simply adding an element to inputStack.
- Pop Operation (`pop()`) and Peek Operation (`peek()`): Amortized `O(1)` time complexity. While each element is transferred at most twice (once into `outputStack` and once back to `inputStack`), this happens infrequently relative to the number of operations, making the average time complexity `O(1)`.
- Empty Operation (`empty()`): `O(1)` time complexity, as it simply checks the lengths of `inputStack` and `outputStack`.

### Space Complexity:
`O(n)`, where n is the number of elements in the queue. This space is used to store elements in inputStack and outputStack.

## Edge Cases Handled:
- Operations when the queue is empty (`pop()` and `peek()`).
- Multiple consecutive operations of `pop()` or `peek()` without any `push()` operations in between.
- Sequence of operations ensuring that all elements are correctly transferred between `inputStack` and `outputStack` when needed.

