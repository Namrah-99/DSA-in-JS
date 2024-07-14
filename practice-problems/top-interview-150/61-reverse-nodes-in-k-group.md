# 25. Reverse Nodes in k-Group

## Leetcode Problem
https://leetcode.com/problems/reverse-nodes-in-k-group/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of reversing nodes in a linked list in groups of k while maintaining `O(n)` time complexity and `O(1)` space complexity, we can approach it using an `iterative method`. Let's break down the approach step-by-step and discuss how it handles different edge cases and the complexity analysis.

## Approach
### Edge Cases:
- If `k` is `1`, the list remains unchanged since reversing groups of 1 doesn't change the order.
- If the list is empty or head is null, return null.
- Handle scenarios where the number of nodes (`n`) is less than `k` by leaving nodes unchanged at the end.

### Iterative Reversal:
- Use `two pointers`: `prev` and `next` to keep track of the nodes before and after the current group of `k` nodes being reversed.
- Traverse through the list in chunks of `k` nodes.
- For each chunk:
  - Reverse the current group of `k` nodes.
  - Adjust pointers (`prev` and `next`) to connect the reversed group back into the main list.

### Reversing a Group of `k` Nodes:
- Maintain pointers (`start`, `end`) to mark the boundaries of the current group.
- Reverse the nodes in this group while traversing them.
- Adjust pointers (`prev.next` and `prev`) to properly link the reversed group with the rest of the list.

### Returning the Updated head:
- If `k` is greater than or equal to the number of nodes left, return the modified `head`.
- Otherwise, return the original head which would have been adjusted during the iteration.

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
var reverseKGroup = function(head, k) {
    // Edge case: if k is 1, no reversal needed
    if (k === 1) {
        return head;
    }
    
    let dummy = new ListNode(0);
    dummy.next = head;
    let prev = dummy;
    
    while (head) {
        let start = head;
        let end = head;
        
        // Check if there are at least k nodes remaining
        for (let i = 1; i < k && end; i++) {
            end = end.next;
        }
        
        if (!end) {
            break; // Less than k nodes remaining
        }
        
        // Record the next node after the current group
        let next = end.next;
        
        // Reverse the current group of k nodes
        end.next = null; // Separate the group from the rest of the list
        prev.next = reverseList(start); // Connect the reversed group
        
        // Move pointers for the next iteration
        start.next = next;
        prev = start;
        head = next;
    }
    
    return dummy.next;
};

// Function to reverse a linked list
function reverseList(head) {
    let prev = null;
    let current = head;
    
    while (current) {
        let next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }
    
    return prev;
}
```

## Complexity Analysis:
### Time Complexity: `O(n)`
- We traverse each node in the list once.
- Within each group of `k` nodes, we perform a constant amount of work for the reversal (`O(k)` operations). Since each node is visited once, the overall time complexity is `O(n)`.
### Space Complexity: `O(1)`
- We use only a constant amount of extra space, primarily for pointers (`dummy`, `prev`, `start`, `end`, etc.), regardless of the input size.

## Conclusion:
This approach efficiently reverses nodes in groups of `k` while maintaining optimal time and space complexities. It handles edge cases such as when `k` is `1` or when the number of nodes left is less than `k`. By leveraging an iterative approach and a helper function to reverse linked lists, it ensures that the list is modified correctly according to the problem requirements.
