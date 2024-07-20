# 104. Maximum Depth of Binary Tree

## Leetcode Problem
https://leetcode.com/problems/maximum-depth-of-binary-tree/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of finding the maximum depth of a binary tree with the given constraints (time complexity `O(n)` and space complexity `O(1)`), we can utilize a depth-first search (`DFS`) approach. Here’s a detailed explanation and the optimal solution:

Given a binary tree, the maximum depth is defined as the `number of nodes along the longest path from the root node down to the farthest leaf node`. We need to find this maximum depth using efficient algorithms.

## `Recursive DFS Approach`

We can use a recursive function to traverse the tree and calculate the depth:

- If the current node is `null` (indicating an empty subtree), we return 0`.
- Otherwise, we recursively calculate the maximum depth of the left and right subtrees.
- The maximum depth of the current node will be `1 + maxDepth(left subtree)` if it exists, or `1 + maxDepth(right subtree)` if it exists.

### Base Case 
If the root of the tree is `null`, the maximum depth is `0`.

### Edge Cases
- An empty tree (`root = null`), where the maximum depth should be `0`.
- Trees with only one node (either just the root or only one child).

## Complexity Analysis
### Time Complexity
`O(n)` where `n` is the number of nodes in the binary tree. We visit each node exactly once.
### Space Complexity
`O(1)` excluding the recursion stack. We use only a constant amount of extra space regardless of the input size.

## Solution Code
```javascript
class TreeNode {
    constructor(val = 0, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

var maxDepth = function(root) {
    // Base case: if root is null, depth is 0
    if (root === null) {
        return 0;
    }
    
    // Calculate the depth of the left subtree
    let leftDepth = maxDepth(root.left);
    
    // Calculate the depth of the right subtree
    let rightDepth = maxDepth(root.right);
    
    // Return the maximum depth of the current node
    return 1 + Math.max(leftDepth, rightDepth);
};

// Example usage:

// Example 1:
// Input: [3,9,20,null,null,15,7]
let root1 = new TreeNode(3);
root1.left = new TreeNode(9);
root1.right = new TreeNode(20);
root1.right.left = new TreeNode(15);
root1.right.right = new TreeNode(7);

console.log(maxDepth(root1)); // Output: 3

// Example 2:
// Input: [1,null,2]
let root2 = new TreeNode(1);
root2.right = new TreeNode(2);

console.log(maxDepth(root2)); // Output: 2
```

### Explanation of Implementation
- **TreeNode Class:** Defines the structure of each node in the binary tree.
- **maxDepth Function:** Recursively computes the maximum depth of the tree:
  - It checks if the `root` is `null`. If so, it returns `0`.
  - Otherwise, it recursively calculates the maximum depth of the left and right subtrees.
  - It returns `1` (for the current node) plus the maximum of the depths of the left and right subtrees.

