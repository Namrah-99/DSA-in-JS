# 48. Rotate Image

## Leetcode Problem
https://leetcode.com/problems/rotate-image/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
To rotate an `n×n` matrix by 90 degrees clockwise in-place, you can follow these steps:
- Transpose the matrix: Swap elements across the main diagonal.
- Reverse each row: Reverse the order of elements in each row.

### Example:


Given matrix:
```css
matrix = [ 1 2 3
           4 5 6
           7 8 9 ]
```


Step 1: Transpose the matrix
```css
matrix= [ 1 4 7
​          2 5 8 
          3 6 9 ] 
​
```

Step 2: Reverse each row
```css
result= [ 7 4 1
          8 5 2
          9 6 3 ]
```

## Solution Code
```javascript
var rotate = function (matrix) {

    // transpose matrix
    for (let i = 0; i < matrix.length; i++) {
        for (let j = i + 1; j < matrix.length; j++) {
            let t = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = t;
        }
    }

    // reverse matrix
    for (let i = 0; i < matrix.length; i++) {
        matrix[i].reverse()
    }

    return matrix
};

// Example usage
let matrix1 = [[1,2,3],[4,5,6],[7,8,9]];
rotate(matrix1);
console.log(matrix1); // Output: [[7,4,1],[8,5,2],[9,6,3]]

let matrix2 = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]];
rotate(matrix2);
console.log(matrix2); // Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
```

## Complexity Aanlysis

### Space Complexity:
- The algorithm operates in-place, so it only uses a constant amount of extra space for the swaps. Therefore, the space complexity is `O(1)`.

### Time Complexity:
- Transpose Step: The transpose step involves a nested loop that iterates over half the elements of the matrix (excluding the diagonal). This takes `O(n^2)` time.
- Reverse Step: Reversing each row takes `O(n)` for each of the n rows, which results in `O(n^2)` time.

Overall, the time complexity of the solution is `O(n^2)`.

### Detailed Analysis
#### Step 1: Transpose the Matrix
To transpose the matrix, you swap elements across the main diagonal. This means for each element at position `(i,j)` where `i<j`, you swap it with the element at position `(j,i)`.

```javascript
for (let i = 0; i < n; i++) {
    for (let j = i + 1; j < n; j++) {
        [matrix[i][j], matrix[j][i]] = [matrix[j][i], matrix[i][j]];
    }
}
```
- The outer loop runs `n` times.
- The inner loop runs approximately `𝑛(𝑛−1)/2` times in total (it avoids the diagonal and elements below the diagonal).
- So, the number of operations in this step is roughly `𝑛^2/2`, which is `O(n^2)`.

#### Step 2: Reverse Each Row
To reverse each row, you need to swap the elements in each row from the beginning to the middle.

```javascript
for (let i = 0; i < n; i++) {
    matrix[i].reverse();
}
```
- The outer loop runs n times.
- Each call to reverse() operates on an array of length n, which takes `O(n)` time.
- Thus, the number of operations in this step is `n×n=n^2` , which is `O(n^2)`.

#### Total Time Complexity
Combining both steps, the total time complexity is `O(n^2)+O(n^2)=O(n^2)`.

#### Conclusion
The solution's time complexity is `O(n^2)` because both the transpose and the reverse steps involve iterating over all `n^2` elements of the matrix. This is typical for problems involving operations on all elements of a 2D matrix, where `n` is the number of rows or columns. It cannot be `O(n)` since that would imply a linear relationship with respect to one dimension of the matrix, which is not sufficient to cover all elements in a 2D matrix.
