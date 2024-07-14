# 19. Remove Nth Node From End of List

## Leetcode Problem
https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of removing the nth node from the end of a linked list while adhering to `O(n)` time complexity and `O(1)` space complexity, we can use a `two-pointer technique`. This approach ensures that we can find and remove the node efficiently in a single pass through the list.

## Approach
### Edge Cases:
- If the list is empty (`head` is null), return null.
- If `n` equals the size of the list (sz), remove the head of the list.
- Handle cases where `n` is 1 separately since it involves removing the last node directly.

### Two-pointer Technique:
- Use two pointers, `fast` and `slow`, initially pointing to the `head` of the list.
- Move the `fast` pointer `n` steps ahead of the `slow` pointer. This positions `fast` at the node to be removed and `slow` at the node just before it.

### Remove the Node:
- Adjust pointers to bypass the `nth` node from the end:
- Update `slow.next` to `slow.next.next`, effectively removing the `nth` node from the end.

### Return the Modified Head:
- If `n` equals 1, `slow.next` would be null after removal, so return `head.next`.
- Otherwise, return `head`, which remains the `head` of the list.

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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    // Edge case: empty list
    if (!head) {
        return null;
    }
    
    let dummy = new ListNode(0);
    dummy.next = head;
    
    let fast = dummy;
    let slow = dummy;
    
    // Move fast pointer n steps ahead
    for (let i = 0; i <= n; i++) {
        fast = fast.next;
    }
    
    // Move both pointers until fast reaches the end
    while (fast !== null) {
        fast = fast.next;
        slow = slow.next;
    }
    
    // Remove the nth node from the end
    slow.next = slow.next.next;
    
    // Return the head of the modified list
    return dummy.next;
};
```

## Complexity Analysis:
### Time Complexity: `O(n)`
- We perform a single pass through the list with two pointers (`fast` and `slow`), which takes `O(n)` time where `n` is the number of nodes in the list.
### Space Complexity: `O(1)`
- We use only a constant amount of extra space for pointers (`dummy`, `fast`, `slow`), regardless of the input size.

## Conclusion:
This solution efficiently removes the `nth` node from the end of a linked list in one pass using the `two-pointer technique`. It handles all edge cases, including removing the head of the list and ensuring correct behavior when `n` equals 1. By maintaining `O(n)` time complexity and `O(1)` space complexity, it meets the problem's constraints and provides an optimal solution.
