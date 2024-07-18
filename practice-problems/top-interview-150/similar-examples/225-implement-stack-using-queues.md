# 225. Implement Stack using Queues

## Leetcode Problem
https://leetcode.com/problems/implement-stack-using-queues/description/

## Problem Explanation
To implement a last-in-first-out (`LIFO`) stack using two queues, and optionally with one queue, we need to simulate the stack operations using standard queue operations efficiently. Let's walk through the solution and how it handles various operations and edge cases.

## Approach
### Using Two Queues
##### For the implementation using two queues:
- Queue1 (`q1`) is used for pushing elements and also to simulate the stack's top operation efficiently.
- Queue2 (`q2`) is used temporarily during the pop operation to reverse the order of elements such that the last pushed element becomes the front of `q1`.

## Solution Code
```javascript
class MyStack {
    constructor() {
        this.q1 = [];  // Primary queue
        this.q2 = [];  // Temporary queue for pop operation
    }
    
    push(x) {
        this.q1.push(x);
    }
    
    pop() {
        while (this.q1.length > 1) {
            this.q2.push(this.q1.shift());
        }
        const popped = this.q1.shift();
        [this.q1, this.q2] = [this.q2, this.q1]; // Swap q1 and q2
        return popped;
    }
    
    top() {
        while (this.q1.length > 1) {
            this.q2.push(this.q1.shift());
        }
        const top = this.q1[0];
        this.q2.push(this.q1.shift());
        [this.q1, this.q2] = [this.q2, this.q1]; // Swap q1 and q2
        return top;
    }
    
    empty() {
        return this.q1.length === 0;
    }
}
```
## Explanation of Operations:
### Push Operation (`push(x)`):
- Simply push the element `x` into `q1`. This is efficient as it directly adds elements to the end of the queue.
### Pop Operation (`pop()`):
- Move all elements from `q1` except the last one to `q2`. The last element in `q1` is then removed and returned as the popped element.
- Swap `q1` and `q2` to restore the original state.
### Top Operation (`top()`):
- Similar to `pop()`, move all elements from `q1` except the last one to `q2`. Peek at the last element in `q1` and save it.
- Push this last element back into `q2` and return it as the top element.
- Swap `q1` and `q2` to restore the original state.
### Empty Operation (`empty()`):
- Simply checks if `q1` is empty.

## Complexity Analysis:

### Time Complexity:
- Push Operation (`push(x)`): `O(1)` since it directly appends to `q1`.
- Pop Operation (`pop()`) and Top Operation (`top()`): `O(n)` in worst case where `n` is the number of elements in `q1`, due to moving elements between queues. However, on average, both operations are `O(1)` amortized.
- Empty Operation (`empty()`): `O(1)` since it checks the length of `q1`.

### Space Complexity:
- `O(n)` where `n` is the number of elements in the stack, due to the space used by `q1` and `q2`.

## Edge Cases Handled:
- Operations when the stack is empty (`pop()` and `top()`).
- Handling of multiple consecutive operations (`pop()` or `top()`) without any `push()` operations in between.
- Sequence of operations ensuring that all elements are correctly transferred between `q1` and `q2` when needed.

## Follow-up: Implementing with One Queue
Implementing the stack using only one queue while maintaining `O(1)` time complexity for all operations is more challenging and involves using recursive operations or maintaining additional state. This involves using recursive `push()` operations to achieve the desired order of elements, which is more complex to implement and manage efficiently in JavaScript due to its single-threaded nature and event-driven environment.

