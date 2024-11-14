# 226. Invert Binary Tree

## Leetcode Problem
https://leetcode.com/problems/invert-binary-tree/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation


## Approach


## Edge Cases


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

var invertTree = function (root) {
    if (root === null) {
        return null;
    }

    let t = root.left;
    root.left = root.right;
    root.right = t;

    invertTree(root.left);
    invertTree(root.right);

    return root;
};

// Example usage:

// Example 1:
// Input: p = [4,7,2,9,6,3,1]
let p = new TreeNode(4);
p.left = new TreeNode(7);
p.right = new TreeNode(2);

console.log(invertTree(p)); // Output: [4,7,2,9,6,3,1]
```

## Explanation of Implementation

