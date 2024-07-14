# 61. Rotate List

## Leetcode Problem
https://leetcode.com/problems/rotate-list/description/?envType=study-plan-v2&envId=top-interview-150

##  Problem Explanation
To solve the problem of rotating a linked list to the right by `k` places, let's break down the approach step-by-step, considering edge cases and ensuring the solution meets the specified time and space complexities.

## Problem Understanding:
Given a singly linked list and an integer `k`, rotate the list to the right such that each node moves right by `k` places. If `k` is greater than or equal to the length of the list, rotations should wrap around effectively.

## Example Walkthroughs:
Let's walkthrough the examples to understand the rotation:

### Example 1:
```
Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]
Rotate the list [1,2,3,4,5] to the right by 2 places.
```
Example 2:
```
Input: head = [0,1,2], k = 4
Output: [2,0,1]
Rotate the list [0,1,2] to the right by 4 places.
```

## Approach:

### Edge Cases:
- If the list is empty (`head === null`), return `null`.
- If `k` is `0`, the list remains unchanged.

### Calculate Length:
- Traverse the linked list to find its length `n`.

### Adjust Rotation:
- Normalize `k` to `k % n` to handle cases where `k` is larger than the length of the list, effectively reducing unnecessary rotations.

### Find New Tail and Break the List:
- Traverse to the `k`-th node from the end (`newTail`). Set its `next` to `null` and adjust the current tail to point to the current head, forming a circular list temporarily.

### Update Head:
- The new head becomes the node right after `newTail`.

### Return New Head:
- Return the new head of the modified list.

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
 * @param {number} k
 * @return {ListNode}
 */
var rotateRight = function(head, k) {
    if (!head || k === 0) {
        return head;
    }
    
    // Step 1: Calculate the length of the linked list
    let length = 1;
    let current = head;
    while (current.next) {
        current = current.next;
        length++;
    }
    
    // Step 2: Adjust k if it's larger than the length
    k = k % length;
    if (k === 0) {
        return head;
    }
    
    // Step 3: Find the new tail and break the list
    let newTail = head;
    for (let i = 0; i < length - k - 1; i++) {
        newTail = newTail.next;
    }
    
    let newHead = newTail.next;
    newTail.next = null;
    current.next = head; // Connect the original tail to the original head to form a circular list
    
    return newHead;
};
```

## Complexity Analysis:
### Time Complexity: 
`O(n)`, where `n` is the number of nodes in the linked list. We traverse the list twice: once to find the length and once to find the new tail.
### Space Complexity: 
`O(1)`, as we only use a constant amount of extra space for variables.

This implementation efficiently handles rotations by leveraging the properties of linked lists and ensures the solution meets the specified constraints and edge cases.
