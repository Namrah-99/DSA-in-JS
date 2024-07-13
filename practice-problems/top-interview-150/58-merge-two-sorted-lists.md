# 21. Merge Two Sorted Lists

## Leetcode Problem
https://leetcode.com/problems/merge-two-sorted-lists/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To merge two sorted linked lists `list1` and `list2` into one sorted list while maintaining `O(n)` time complexity and `O(1)` space complexity, we can use an `iterative approach` that manipulates pointers.

## Approach:
- Initialization:
  - We'll maintain two pointers (`p1` for `list1` and `p2` for `list2`) to traverse through the lists.
  - Use a dummy node (`dummy`) to facilitate easy construction of the merged list.
- Iterative Merging:
  - Initialize `dummy` as a placeholder for the merged list.
  - Use `current` to keep track of the last node added to the merged list.
- Comparison and Merging:
  - Compare the values pointed by `p1` and `p2`.
  - Append the smaller (or equal, to maintain stable sorting) node to `current.next`.
  - Move the respective pointer (`p1` or `p2`) to the next node after appending.
- Completion:
  - Continue this process until either `list1` or `list2` is exhausted.
  - Append the remaining nodes (if any) of the non-exhausted list directly to `current.next`.

## Edge Cases:
- Both lists are empty (`list1` and `list2`).
- One list is empty while the other is not.
- Both lists have elements, requiring complete merging.

## Solution Code

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */

var mergeTwoLists = function(l1, l2) {
    // Dummy node to simplify handling the result
    let dummy = new ListNode(-1);
    let current = dummy;
    let p1 = l1;
    let p2 = l2;
    
    // Traverse both lists and merge
    while (p1 !== null && p2 !== null) {
        if (p1.val <= p2.val) {
            current.next = p1;
            p1 = p1.next;
        } else {
            current.next = p2;
            p2 = p2.next;
        }
        current = current.next;
    }
    
    // Append the remaining nodes of the non-empty list
    current.next = p1 !== null ? p1 : p2;
    
    // Return the merged list (dummy.next is the actual head)
    return dummy.next;
};
```
## Explanation
- We initialize `dummy` with `-1` to handle cases where both lists might be empty, ensuring `dummy.next` remains null.
- `current` is used to keep track of the last node added to the merged list.
- `p1` and `p2` are initialized to the heads of `list1` and `list2`, respectively.
- We iterate through both lists, comparing the values pointed by `p1` and `p2`, appending the smaller value (or equal) to `current.next`.
- After the loop, append any remaining nodes from the non-exhausted list (`p1` or `p2`) to `current.next`.
- Finally, return `dummy.next`, which points to the head of the merged sorted list.

## Complexity Analysis:
- Time Complexity: `O(n)`, where `n` is the total number of nodes in both lists. We iterate through each node exactly once.
- Space Complexity: `O(1)`, as we only use a constant amount of extra space regardless of the input size (only pointers and a few variables).
