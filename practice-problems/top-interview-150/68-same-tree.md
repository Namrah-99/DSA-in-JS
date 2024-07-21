# 100. Same Tree

## Leetcode Problem
https://leetcode.com/problems/same-tree/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To determine if two binary trees `p` and `q` are identical, we need to check two conditions:
1. They must have the same structure.
2. Corresponding nodes in both trees must have the same values.

## Approach

We can achieve this using a recursive depth-first search (`DFS`) approach:

- Base Case: If both nodes `p` and `q` are null, they are identical.
- Recursive Case: If either `p` or `q` is null (but not both), or their values are not equal, they are not identical.
- Recursively check the left and right subtrees of both trees.

## Edge Cases
- Both trees are `null`.
- One tree is `null` while the other is not.
- Trees have different structures but might have the same values, which should return `false`.
- Trees with a single node should correctly compare their values.

## Complexity Analysis
### Time Complexity:
`O(n)`, where `n` is the number of nodes in the smaller tree. We visit each node exactly once.
### Space Complexity: 
`O(1)`, excluding the recursion stack. We use only a constant amount of extra space regardless of the input size.

## Solution Code
```javascript
class TreeNode {
    constructor(val = 0, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}

var isSameTree = function(p, q) {
    // Base cases: both nodes are null
    if (p === null && q === null) {
        return true;
    }
    
    // If one of the nodes is null and the other is not, they are not identical
    if (p === null || q === null) {
        return false;
    }
    
    // If values are not equal, they are not identical
    if (p.val !== q.val) {
        return false;
    }
    
    // Recursively check left and right subtrees
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
};

// Example usage:

// Example 1:
// Input: p = [1,2,3], q = [1,2,3]
let p1 = new TreeNode(1);
p1.left = new TreeNode(2);
p1.right = new TreeNode(3);

let q1 = new TreeNode(1);
q1.left = new TreeNode(2);
q1.right = new TreeNode(3);

console.log(isSameTree(p1, q1)); // Output: true

// Example 2:
// Input: p = [1,2], q = [1,null,2]
let p2 = new TreeNode(1);
p2.left = new TreeNode(2);

let q2 = new TreeNode(1);
q2.right = new TreeNode(2);

console.log(isSameTree(p2, q2)); // Output: false

// Example 3:
// Input: p = [1,2,1], q = [1,1,2]
let p3 = new TreeNode(1);
p3.left = new TreeNode(2);
p3.right = new TreeNode(1);

let q3 = new TreeNode(1);
q3.left = new TreeNode(1);
q3.right = new TreeNode(2);

console.log(isSameTree(p3, q3)); // Output: false
```

## Explanation of Implementation
- TreeNode Class: Defines the structure of each node in the binary tree.
- isSameTree Function: Recursively checks if two trees `p` and `q` are identical:
  - Handles base cases where both nodes are `null`.
  - Checks if values of current nodes are equal.
  - Recursively checks left and right subtrees of both trees.
