# 54. Spiral Matrix

## Problem Explanation
To solve the problem of returning all elements of an `m×n` matrix in spiral order, we can follow a systematic approach to `traverse the matrix layer by layer` in a spiral pattern.

### Explanation
A spiral traversal of a matrix involves visiting the outermost layer of the matrix first, then the next inner layer, and so on until all elements are visited. This can be done by `maintaining boundaries for the current layer` and adjusting these boundaries as we traverse.

## Steps to Solve
- Initialize Boundaries: We need four boundaries: top, bottom, left, and right. These boundaries will help us keep track of the current layer of the matrix we are traversing.
- Traverse the Matrix: We traverse the matrix in four steps corresponding to the four directions: left to right, top to bottom, right to left, and bottom to top.
- Adjust Boundaries: After completing a traversal in one direction, we adjust the corresponding boundary inward.
- Repeat Until All Elements Are Visited: We continue this process until all elements of the matrix have been visited.

## Example Walkthrough
For example, given the matrix:

```lua
[[1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]]
```
The traversal order will be: 1 → 2 → 3 → 6 → 9 → 8 → 7 → 4 → 5.

## Constraints
- 1≤m,n≤10
- −100≤matrix[i][j]≤100

Given the constraints, the time complexity should be `O(m×n)`, where `m` and `n` are the dimensions of the matrix. This ensures that each element is visited exactly once.

## Logic
```css
- left <= right && top <= bottom
- loop                      -->        L -> R        -->        result.push(matrix[Trow][i])         -->      Trow++
- loop                      -->        T -> B        -->        result.push(matrix[i][Rcol])         -->      Rcol--
- loop (top<=bottom)        -->        R -> L        -->        result.push(matrix[Brow][i])         -->      Brow--
- loop (left<=right)        -->        B -> T        -->        result.push(matrix[i][Lcol])         -->      Lcol++
```

## Solution Code
```javascript
var spiralOrder = function (matrix) {
    let result = [], Lc = 0, Rc = matrix[0].length - 1, Tr = 0, Br = matrix.length - 1;

    while (Lc <= Rc && Tr <= Br) {

        // Traverse from left to right along the top row
        for (let i = Lc; i <= Rc; i++) {
            result.push(matrix[Tr][i])
        }
        Tr++;  // Move the top boundary down

        // Traverse from top to bottom along the right column
        for (let i = Tr; i <= Br; i++) {
            result.push(matrix[i][Rc])
        }
        Rc--;  // Move the right boundary left

        if (Tr <= Br) {
            // Traverse from right to left along the bottom row
            for (let i = Rc; i >= Lc; i--) {
                result.push(matrix[Br][i])
            }
            Br--;  // Move the bottom boundary up
        }

        if (Lc <= Rc) {
            // Traverse from bottom to top along the left column
            for (let i = Br; i >= Tr; i--) {
                result.push(matrix[i][Lc])
            }
            Lc++;  // Move the left boundary right
        }
    }

    return result
};

// Example usage
console.log(spiralOrder([[1, 2, 3], [4, 5, 6], [7, 8, 9]])); // Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]
console.log(spiralOrder([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])); // Output: [1, 2, 3, 4, 8, 12, 11, 10, 9, 5, 6, 7]
```

## Complexity Analysis

### Time Complexity
- The time complexity for the above solution is `O(m×n)`, where `m` is the number of rows and `n` is the number of columns in the matrix.
- The total number of operations is directly proportional to the number of elements in the matrix, which is `m×n`. Therefore, the time complexity is `O(m×n)`.

### Space Complexity
The space complexity of the above solution is `O(1)` for extra space (excluding the output list), as we are only using a few additional variables to keep track of the boundaries and the result list.
