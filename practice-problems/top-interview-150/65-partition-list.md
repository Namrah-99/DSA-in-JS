# 86. Partition List

## Leetcode Problem
https://leetcode.com/problems/partition-list/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to partition a linked list such that all nodes with values less than a given value `x` come before all nodes with values greater than or equal to `x`. The relative order of the nodes within each partition should be preserved.

## Approach
The provided solution uses a `two-pointer approach` to achieve the partitioning `in-place` with `O(1)` extra space complexity.

### Initialization:

- dummy: A dummy node is used to simplify the logic when inserting nodes at the beginning of the list.
- p1: This pointer tracks the end of the "before" partition, i.e., nodes less than `x`.
- p2: Initially points to the head of the list. It helps in iterating through nodes and managing the "after" partition.
- p3: A pointer used for traversal through the list.

### Finding the Partition Point:

- The while loop with p1 finds the first node that is greater than or equal to `x`. This ensures `p1` ends up just before the start of the "after" partition.

### Partitioning the List:

- After determining `p1` and `p2`, `p3` starts from `p2.next`.
- The second while loop iterates through the rest of the list (`p3`):
  - If `p3.val` is less than `x`, it moves `p3` to the "before" partition:
    - `p2.next = p3.next`: Removes `p3` from the "after" partition.
    - `p3.next = p1.next`: Inserts `p3` into the "before" partition.
    - `p1.next = p3`: Updates `p1` to point to `p3`.
    - Moves `p1` to `p3`, making `p3` the new end of the "before" partition.
    - Moves `p3` to `p2.next` to continue the traversal.
  - If `p3.val` is not less than `x`, simply moves `p3` forward in the "after" partition (`p2` and `p3` move forward).

### Returning the Result:
- Finally, `dummy.next` is returned as the head of the modified list, which ensures the correct head is returned even if `dummy` is used for insertion.

## Edge Cases Handled:
- If the list is empty or has only one node (`!head || !head.next`), it returns the list itself since no partitioning is necessary.
- Handles cases where all nodes are either less than `x` or all nodes are greater than or equal to `x`.

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
 * @param {number} x
 * @return {ListNode}
 */
var partition = function (head, x) {
    if (!head || !head.next) {
        return head;
    }

    let dummy = new ListNode(0);
    dummy.next = head;
    let p1 = dummy; // Pointer to the end of the "before" partition

    // Find the first node that is >= x
    while (p1.next && p1.next.val < x) {
        p1 = p1.next;
    }

    let p2 = p1.next; // Pointer to the first node of the "after" partition
    if (!p2) {
        return head; // No nodes >= x found, return the original list
    }

    let p3 = p2.next; // Iterator pointer for traversal

    while (p3) {
        if (p3.val < x) {
            // Move p3 node to the "before" partition
            p2.next = p3.next; // Remove p3 from the "after" partition
            p3.next = p1.next; // Insert p3 into the "before" partition
            p1.next = p3;      // Update p1 to point to p3
            p1 = p3;           // Move p1 to p3 (new end of the "before" partition)
            p3 = p2.next;      // Move p3 to the next node in the "after" partition
        } else {
            // p3.val >= x, just move p3 forward in the "after" partition
            p2 = p3;
            p3 = p3.next;
        }
    }

    return dummy.next; // Return the head of the modified list
};
```

```css
if (p3.val < x){
0    4    1
/\   /\   /\
p1   p2   p3

      < x     >= x  
---------   ______ 
0   2   1   4   5   1   3
        /\      /\  /\  
        p1      p2  p3
}

```

## Complexity Analysis:
### Time Complexity
- `O(n)`, where `n` is the number of nodes in the linked list. Both the initial traversal to find `p1` and the subsequent traversal through the list with `p3` contribute linearly to the time complexity.
### Space Complexity
- `O(1)`, since the solution uses only a constant amount of extra space regardless of the input size. The additional space is used for pointers (`dummy`, `p1`, `p2`, `p3`) and does not scale with `n`.
