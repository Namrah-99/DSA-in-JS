# 138. Copy List with Random Pointer

## Leetcode Problem
https://leetcode.com/problems/copy-list-with-random-pointer/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of making a deep copy of a linked list with random pointers, we need to ensure that each node in the copied list is a separate instance from the original list while maintaining the structure defined by the next and random pointers. Let's walk through the optimal approach using O(n) time complexity and O(1) space complexity.

## Approach:
- Iterative Deep Copy with Interleaving:
  - For each node in the `original` list, create a new node and insert it immediately following its corresponding original node.
  - This creates a structure where the `original` and `copied` nodes are interleaved in the list.
- Setting Random Pointers:
  - Traverse the list again. For each original node, adjust the `random` pointer of its corresponding copied node to point to the correct node.
  - Since nodes are interleaved, setting `copied_node.random` is straightforward: `copied_node.random = original_node.random.next` (if `original_node.random` is not null).
- Splitting the Lists:
  - After setting all `random` pointers, separate the `original` and `copied` lists.
  - Restore the `next` pointers of both original and copied lists to reconstruct the lists as they were.

## Edge Cases:
- Handle empty lists (`head` is null).
- Handle lists with nodes where `random` pointers may be null.
- Ensure correct handling of lists where every node has a random pointer.

## Solution Code
```javascript
/**
 * Definition for a Node.
 * function Node(val, next, random) {
 *    this.val = val;
 *    this.next = next;
 *    this.random = random;
 * };
 */

var copyRandomList = function(head) {
    if (!head) return null;
    
    // Step 1: Create interleaved copy nodes
    let current = head;
    while (current) {
        let copied = new Node(current.val, current.next, null);
        current.next = copied;
        current = copied.next;
    }
    
    // Step 2: Assign random pointers for copied nodes
    current = head;
    while (current) {
        if (current.random) {
            current.next.random = current.random.next;
        }
        current = current.next.next;
    }
    
    // Step 3: Separate original and copied lists
    let original = head;
    let copiedHead = head.next;
    let copied = copiedHead;
    
    while (original) {
        original.next = copied.next;
        original = original.next;
        if (original) {
            copied.next = original.next;
            copied = copied.next;
        }
    }
    
    return copiedHead;
};
```
## Explanation 
- Step 1:
  We iterate through the original list (`head`). For each node, create a new node (`copied`) with the same `val`, set its `next` to the `next` of `current`, and update `current.next` to point to `copied`. This creates the interleaved structure.

- Step 2:
  Traverse the list again. For each `original` node (`current`), if it has a `random` pointer, set the `random` pointer of its corresponding copied node (`current.next`) to `current.random.next`.

- Step 3:
  Restore the `original` and `copied` lists. Traverse through the list, separating the `original` and `copied` nodes by adjusting the `next` pointers accordingly.

This approach ensures that we achieve a deep copy of the linked list with random pointers in O(n) time complexity and O(1) space complexity, meeting the problem's requirements. Each node and its random pointer are correctly copied and linked without creating any additional data structures proportional to the input size.

## Complexity Analysis

- Time Complexity:
  - Traversal and Interleaving: `O(n)`
    - We traverse through each node once to create new nodes and interleave them with the original list.
  - Setting Random Pointers: `O(n)`
    - We traverse through each node once to set random pointers for the copied nodes.
  - Separating Lists: `O(n)`
    - We traverse through each node once to restore the original list structure.

  Overall Time Complexity: `O(n)`

- Space Complexity:
  - Additional Nodes: `O(n)`
  - We create a new node for each existing node in the original list.

  Overall Space Complexity: `O(n)`

---

## Example Linked List:
Consider the following linked list with random pointers:

```css
Original List:
Node1 -> Node2 -> Node3 -> Node4 -> Node5
|         |         |         |         |
v         v         v         v         v
null   -> Node3    null   -> Node1    Node2
```
### Step-by-Step Execution:
#### Initial Setup:
- Start with the head pointing to Node1.
- Step 1: Create Interleaved Copy Nodes:
  - Create a new node for each existing node and insert them immediately after their original nodes.
  ```css
  Before Step 1:
  head -> Node1 -> Node2 -> Node3 -> Node4 -> Node5
          |         |         |         |         |
          v         v         v         v         v
         null   -> Node3    null   -> Node1    Node2
  
  After Step 1:
  head -> Node1 -> Copy1 -> Node2 -> Copy2 -> Node3 -> Copy3 -> Node4 -> Copy4 -> Node5 -> Copy5
          |         |         |         |         |         |         |         |         |
          v         v         v         v         v         v         v         v         v
         null   -> Node3    null   -> Node1    null   -> Node3    null   -> Node1    null
  ```
  - Here, Copy1, Copy2, Copy3, Copy4, and Copy5 are newly created nodes with the same values as Node1, Node2, Node3, Node4, and Node5, respectively.
- Step 2: Assign Random Pointers:
  - Traverse through the list again to set the random pointers for the copied nodes based on the original nodes' random pointers.
  ```css
  After Step 2:
  head -> Node1 -> Copy1 -> Node2 -> Copy2 -> Node3 -> Copy3 -> Node4 -> Copy4 -> Node5 -> Copy5
          |         |         |         |         |         |         |         |         |
          v         v         v         v         v         v         v         v         v
         null   -> Node3    null   -> Node1    null   -> Node3    null   -> Node1    null
  
  Copy1.random = Node1.random.next = Copy2
  Copy2.random = Node2.random.next = null
  Copy3.random = Node3.random.next = Copy1
  Copy4.random = Node4.random.next = Node3.next = Copy3
  Copy5.random = Node5.random.next = Node2.next = Copy2
  ```
  - For example, Copy1.random points to Copy2 because Node1.random points to Node2, and Node2's next in the copied list is Copy2.

- Step 3: Separate Original and Copied Lists:
  - Restore the original list's next pointers and extract the copied list.
  ```css
  After Step 3:
  head -> Node1 -> Node2 -> Node3 -> Node4 -> Node5
          |         |         |         |         |
          v         v         v         v         v
         null   -> Node3    null   -> Node1    Node2
  
  copiedHead -> Copy1 -> Copy2 -> Copy3 -> Copy4 -> Copy5
                  |         |         |         |         |
                  v         v         v         v         v
                null   -> Node3    null   -> Node1    null
  ```
  - head now points to the original list, and copiedHead points to the copied list.

- Return:
  - Return copiedHead, which is the head of the copied linked list.

---

## Step 2 Explanation
```javascript
// Step 2: Assign random pointers for copied nodes
current = head;
while (current) {
    if (current.random) {
        current.next.random = current.random.next;
    }
    current = current.next.next;
}
```

## Detailed Explanation:
### Initialization:
- `current = head;`: Start traversal from the head of the original list. head points to the first node in the original list.
- While Loop Explanation:
  - `while (current) { ... }`: Iterate through the original list nodes. The loop continues until current becomes null, indicating the end of the list.

### Checking Random Pointer:
- `if (current.random) { ... }`: Check if the random pointer of the current node (current.random) exists and is not null.
- Inside this block:
  - `current.next.random = current.random.next;`: Set the random pointer of the corresponding copied node (current.next) to point to current.random.next.
  - This line ensures that the copied node's random pointer correctly points to the node in the copied list that corresponds to the node pointed to by current.random in the original list.

### Advancing the Pointer:
- `current = current.next.next;`: Move current to the next original node. Since we have interleaved the original and copied nodes (`current.next` points to the copied node), we skip over the copied node (`current.next.next`) to move to the next original node.
- This step effectively allows us to correctly link the copied list nodes with their corresponding random pointers without disrupting the original list's structure.

## Example Clarification:
Let's use an example to clarify how this works:

- Original List:
```css
Node1 -> Node2 -> Node3
|         |         |
v         v         v
Node3    null      Node1
```
- After Interleaving (Step 1):
```css
Linked List:
Node1 -> Copy1 -> Node2 -> Copy2 -> Node3 -> Copy3
|         |         |         |         |         |
v         v         v         v         v         v
Node3    null      null     Node1     null      Node1
```
- During Step 2 (Assign random pointers for copied nodes):
- Start with current pointing to Node1.
- Node1.random points to Node3. So, current.next.random (which is Copy1.random) should point to Node3.next (which is Copy3).
- Therefore, Copy1.random points to Copy3.
- Move current to Node2, skipping over Copy1.
- Node2.random is null, so no assignment is made for Copy2.
- Move current to Node3, skipping over Copy2.
- Node3.random points to Node1. So, current.next.random (which is Copy3.random) should point to Node1.next (which is Copy1).
- Therefore, Copy3.random points to Copy1.

Final Copied List:
```css
Copied List:
Copy1 -> Copy2 -> Copy3
|         |         |
v         v         v
Copy3    null      Copy1
```
