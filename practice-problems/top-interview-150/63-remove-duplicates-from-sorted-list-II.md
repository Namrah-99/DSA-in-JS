# 82. Remove Duplicates from Sorted List II

## Leetcode Problem
https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of deleting nodes with duplicate values from a sorted linked list while maintaining `O(n)` time complexity and `O(1)` space complexity, we can use an `iterative approach` with careful handling of pointers. Let's break down the approach step-by-step and discuss how it handles different edge cases.

## Approach

### Edge Cases:
- Handle an empty list (`head` is null) by returning null.
- Ensure correct behavior when the list has only one node, as there are no duplicates to remove.

### Iterative Traversal:
- Use two pointers: `dummy` and `current`.
- `dummy` is used to handle cases where the head itself might change due to duplicates being removed.
- `current` traverses through the list to identify and remove duplicates.

### Identifying Duplicates:
- Move `current` through the list while checking if there are any duplicates.
- If a duplicate is found (i.e., `current.next` has the same value as `current`), continue to move `current` until the last occurrence of the duplicate.

### Removing Duplicates:
- Update `dummy.next` to skip over the section of nodes that contain duplicates.
- Ensure proper linking of nodes when moving through the list.

### Returning the Modified List:
- Return `dummy.next`, which represents the head of the modified list after removing duplicates.

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
 * @return {ListNode}
 */
var deleteDuplicates = function(head) {
    // Edge case: empty list
    if (!head || !head.next) {
        return head;
    }
    
    let dummy = new ListNode(0);
    dummy.next = head;
    let prev = dummy;
    let current = head;
    
    while (current) {
        // Check for duplicates
        while (current.next && current.val === current.next.val) {
            current = current.next;
        }
        
        // No duplicates found, move prev and current forward
        if (prev.next === current) {
            prev = prev.next;
        } else {
            // Remove duplicates by bypassing them
            prev.next = current.next;
        }
        
        current = current.next;
    }
    
    return dummy.next;
};
```

## Complexity Analysis:

### Time Complexity: `O(n)`
- We traverse each node in the list once.
- Inside the main while loop, for each node, we may skip over a sublist of nodes that are duplicates, but each node and its duplicates are only processed once.

### Space Complexity: `O(1)`
- We use only a constant amount of extra space for pointers (`dummy`, `prev`, `current`), regardless of the input size.

## Conclusion:
This solution efficiently removes nodes with duplicate values from a sorted linked list while maintaining the sorted order. It handles edge cases such as an empty list or a list with no duplicates gracefully. By using an `iterative approach` with careful pointer management, it ensures optimal performance with `O(n)` time complexity and `O(1)` space complexity.
