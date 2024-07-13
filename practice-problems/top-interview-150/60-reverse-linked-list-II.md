# 92. Reverse Linked List II

## Leetcode Problem
https://leetcode.com/problems/reverse-linked-list-ii/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of reversing a linked list from position left to right, while maintaining `O(n)` time complexity and `O(1)` space complexity, we can follow a structured approach. Let's break down the solution step-by-step and discuss its complexities and edge cases.

## Approach
### Edge Cases:
- If the list has only one node (`left = right`), the list remains unchanged.
- The problem guarantees that `1 <= left <= right <= n`, ensuring valid indices.

### Traversal to Reach the Reversal Point:
- Traverse the list until reaching the node just before `left`. This allows us to properly link the reversed section later.

### Reversing the Section Between left and right:
#### Maintain references to:
- `prev_left`: Node before `left` (null initially or head if left = 1).
- `left_node`: Node at position `left`.
- `right_node`: Node at position `right`.
- `next_right`: Node immediately after `right` (null if right is the last node).

### Performing the Reversal:
- Reverse the `left` to `right` segment in-place by adjusting next pointers.
- Properly connect `prev_left` to `right_node` and `left_node` to `next_right` to maintain continuity.

### Return the Updated Head:
- If `left > 1`, return the original head (no change before `left`).
- If `left = 1`, return `right_node` as the new head of the reversed list segment.

## Solution Code
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */

/**
 * @param {ListNode} head
 * @param {number} left
 * @param {number} right
 * @return {ListNode}
 */
var reverseBetween = function(head, left, right) {
    // Edge case: if left == right, no reversal needed
    if (left === right) {
        return head;
    }
    
    let dummy = new ListNode(0); // Dummy node to handle cases where left > 1
    dummy.next = head;
    let prev_left = dummy;
    
    // Move prev_left to the node just before left
    for (let i = 1; i < left; i++) {
        prev_left = prev_left.next;
    }
    
    let left_node = prev_left.next;
    let right_node = left_node;
    
    // Move right_node to the node at position right
    for (let i = left; i < right; i++) {
        right_node = right_node.next;
    }
    
    let next_right = right_node.next; // Node immediately after right_node
    
    // Reverse the segment from left_node to right_node
    let prev = next_right;
    let current = left_node;
    while (current !== next_right) {
        let next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }
    
    // Connect the reversed segment with the rest of the list
    prev_left.next = right_node;
    left_node.next = next_right;
    
    // Return appropriate head of the modified list
    return dummy.next;
};
```
## Complexity Analysis:
### Time Complexity: `O(n)`
- We traverse the list once to find `prev_left`, `left_node`, and `right_node`.
- We reverse a portion of the list from `left` to `right`, which takes `O(right - left + 1)` operations.
- Thus, the overall time complexity is `O(n)`.
### Space Complexity: `O(1)`
- We use only a constant amount of extra space for pointers (dummy, prev_left, etc.), regardless of the input size.

## Conclusion:
This solution efficiently reverses a segment of a linked list in one pass, adhering to the constraints of `O(n)` time complexity and `O(1)` space complexity. It handles edge cases such as reversing the entire list or a single node, ensuring the linked list structure is maintained throughout the operation.
