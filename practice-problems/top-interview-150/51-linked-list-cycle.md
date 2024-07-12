# 141. Linked List Cycle

## Leetcode Problem
https://leetcode.com/problems/linked-list-cycle/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of detecting a cycle in a linked list, we can use `Floyd's Tortoise and Hare algorithm`, which is efficient with `O(n)` time complexity and `O(1)` space complexity. This algorithm uses `two pointers` moving at different speeds to determine if there is a cycle in the list.

## Approach
- Initialization:
  - Use two pointers, `slow` and `fast`. Initially, both pointers are set to the head of the list.
- Move Pointers:
  - Move `slow one step` at a time.
  - Move `fast two steps` at a time.
- Check for Cycle:
  - If there is a cycle, the `fast` pointer will eventually meet the `slow` pointer within the cycle.
  - If `fast` reaches the end of the list (`fast` or `fast.next` becomes null), there is no cycle in the list.
- Return Result:
  - If `slow` and `fast` meet, return `true` (cycle detected).
  - If `fast` reaches the end of the list, return `false` (no cycle).

## Edge Cases
- **Empty List:** If the list is empty (head is null), return false.
- **Single Node:** If the list has only one node, it can't have a cycle unless pos is 0.
- **General Case:** Handle typical cases with cycles and without cycles.

## Implementation

```javascript
var hasCycle = function(head) {
    if (head === null || head.next === null) return false;

    let slow = head;
    let fast = head;

    while (fast !== null && fast.next !== null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow === fast) return true;
    }

    return false;
};
```
## Explanation
- Initialization:
  - Both slow and fast pointers start at the head of the list.
- Move Pointers:
  - slow pointer moves one step at a time.
  - fast pointer moves two steps at a time.
  - If there is a cycle, slow and fast will eventually meet inside the cycle.
- Check for Cycle:
  - If slow and fast meet, a cycle is detected, and the function returns true.
  - If fast reaches the end of the list, the function returns false because no cycle is present.

## Dry Run with Examples
### Example 1: head = [3, 2, 0, -4], pos = 1
- The list has a cycle where the tail connects to the 1st node.
- slow and fast pointers will eventually meet at node 2.
- Output: true

### Example 2: head = [1, 2], pos = 0
- The list has a cycle where the tail connects to the 0th node.
- slow and fast pointers will eventually meet at node 1.
- Output: true

### Example 3: head = [1], pos = -1
- The list has only one node and no cycle.
- slow and fast pointers can't meet as there is no cycle.
- Output: false


## Complexity Analysis

### Time Complexity
  - `O(n)`, where n is the number of nodes in the linked list. In the worst case, both pointers traverse the entire list.

### Space Complexity
  - `O(1)`, since we are using only two pointers and no additional data structures.
