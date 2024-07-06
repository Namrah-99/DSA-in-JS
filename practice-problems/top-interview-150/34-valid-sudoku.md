# 36. Valid Sudoku

## Leetcode Problem
https://leetcode.com/problems/valid-sudoku/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To determine if a given 9x9 Sudoku board is valid, we need to ensure that all the filled cells (i.e., cells containing digits 1-9) adhere to the following rules:
- Each row must contain the digits 1-9 without repetition.
- Each column must contain the digits 1-9 without repetition.
- Each of the nine 3x3 sub-boxes must contain the digits 1-9 without repetition.
We can implement this validation using a straightforward approach by utilizing sets to keep track of seen digits in each row, column, and 3x3 sub-box. Here’s how we can do it:

## Steps:
- Create three sets for each row, each column, and each 3x3 sub-box to store the seen digits.
- Traverse each cell in the board:
  
     - For each digit, check if it already exists in the corresponding row, column, or sub-box set.
     - If it does, the board is invalid.
     - If it doesn’t, add the digit to the respective sets.

- If no duplicates are found in any row, column, or sub-box, the board is valid.


## Solution Code
```javascript
var isValidSudoku = function(board) {
    const rows = Array.from({length:9},()=>new Set())
    const cols = Array.from({length:9},()=>new Set())
    const boxes = Array.from({length:9},()=>new Set())

    for(let r=0; r<9; r++){
        for(let c=0; c<9; c++){
            let char = board[r][c];
            
            if(char==='.') continue;
            
            let boxesIndex = Math.floor(r/3) * 3 + Math.floor(c/3);
            
            if(rows[r].has(char) || cols[c].has(char) || boxes[boxesIndex].has(char)){
                console.log('Duplicate Found (Invalid Sudoku)')
                return false
            }
            
            rows[r].add(char);
            cols[c].add(char);
            boxes[boxesIndex].add(char);
        }
    }
    
    return true
};

// Example usage
const board1 = [
    ["5", "3", ".", ".", "7", ".", ".", ".", "."],
    ["6", ".", ".", "1", "9", "5", ".", ".", "."],
    [".", "9", "8", ".", ".", ".", ".", "6", "."],
    ["8", ".", ".", ".", "6", ".", ".", ".", "3"],
    ["4", ".", ".", "8", ".", "3", ".", ".", "1"],
    ["7", ".", ".", ".", "2", ".", ".", ".", "6"],
    [".", "6", ".", ".", ".", ".", "2", "8", "."],
    [".", ".", ".", "4", "1", "9", ".", ".", "5"],
    [".", ".", ".", ".", "8", ".", ".", "7", "9"]
];

const board2 = [
    ["8", "3", ".", ".", "7", ".", ".", ".", "."],
    ["6", ".", ".", "1", "9", "5", ".", ".", "."],
    [".", "9", "8", ".", ".", ".", ".", "6", "."],
    ["8", ".", ".", ".", "6", ".", ".", ".", "3"],
    ["4", ".", ".", "8", ".", "3", ".", ".", "1"],
    ["7", ".", ".", ".", "2", ".", ".", ".", "6"],
    [".", "6", ".", ".", ".", ".", "2", "8", "."],
    [".", ".", ".", "4", "1", "9", ".", ".", "5"],
    [".", ".", ".", ".", "8", ".", ".", "7", "9"]
];

console.log('Output: ',isValidSudoku(board1)); // Output: true
console.log('Output: ',isValidSudoku(board2)); // Output: false
```

## Visual representation of the board with sub-box indices:
In a 9x9 Sudoku board, there are 9 sub-boxes of size 3x3. These sub-boxes can be indexed from 0 to 8 as follows:
```css
0 1 2
3 4 5
6 7 8
```
Each cell in the Sudoku board can be mapped to one of these sub-boxes based on its row (`r`) and column (`c`) indices. The board can be visualized as a grid of `3x3` sub-boxes, and each sub-box can be identified by its position in this grid.

```css
[0, 0, 0, 1, 1, 1, 2, 2, 2]
[0, 0, 0, 1, 1, 1, 2, 2, 2]
[0, 0, 0, 1, 1, 1, 2, 2, 2]
[3, 3, 3, 4, 4, 4, 5, 5, 5]
[3, 3, 3, 4, 4, 4, 5, 5, 5]
[3, 3, 3, 4, 4, 4, 5, 5, 5]
[6, 6, 6, 7, 7, 7, 8, 8, 8]
[6, 6, 6, 7, 7, 7, 8, 8, 8]
[6, 6, 6, 7, 7, 7, 8, 8, 8]
```

Each sub-box index is calculated using the formula to map a cell to its respective sub-box.
```javascript
const boxIndex = Math.floor(r / 3) * 3 + Math.floor(c / 3);
```
## Board (Example 1):
```css
[
    ["5", "3", ".", ".", "7", ".", ".", ".", "."],
    ["6", ".", ".", "1", "9", "5", ".", ".", "."],
    [".", "9", "8", ".", ".", ".", ".", "6", "."],
    ["8", ".", ".", ".", "6", ".", ".", ".", "3"],
    ["4", ".", ".", "8", ".", "3", ".", ".", "1"],
    ["7", ".", ".", ".", "2", ".", ".", ".", "6"],
    [".", "6", ".", ".", ".", ".", "2", "8", "."],
    [".", ".", ".", "4", "1", "9", ".", ".", "5"],
    [".", ".", ".", ".", "8", ".", ".", "7", "9"]
];
```
### Output:
```css
r:  0 --------------------------------------------------------------------------------------------------------
c:  0 ______________
rows[r= 0 ]:  Set(0) {}  cols[c= 0 ]:  Set(0) {}  boxes[boxIndex= 0 ]:  Set(0) {}
c:  1 ______________
rows[r= 0 ]:  Set(1) { '5' }  cols[c= 1 ]:  Set(0) {}  boxes[boxIndex= 0 ]:  Set(1) { '5' }
c:  2 ______________
c:  3 ______________
c:  4 ______________
rows[r= 0 ]:  Set(2) { '5', '3' }  cols[c= 4 ]:  Set(0) {}  boxes[boxIndex= 1 ]:  Set(0) {}
c:  5 ______________
c:  6 ______________
c:  7 ______________
c:  8 ______________
r:  1 --------------------------------------------------------------------------------------------------------
c:  0 ______________
rows[r= 1 ]:  Set(0) {}  cols[c= 0 ]:  Set(1) { '5' }  boxes[boxIndex= 0 ]:  Set(2) { '5', '3' }
c:  1 ______________
c:  2 ______________
c:  3 ______________
rows[r= 1 ]:  Set(1) { '6' }  cols[c= 3 ]:  Set(0) {}  boxes[boxIndex= 1 ]:  Set(1) { '7' }
c:  4 ______________
rows[r= 1 ]:  Set(2) { '6', '1' }  cols[c= 4 ]:  Set(1) { '7' }  boxes[boxIndex= 1 ]:  Set(2) { '7', '1' }
c:  5 ______________
rows[r= 1 ]:  Set(3) { '6', '1', '9' }  cols[c= 5 ]:  Set(0) {}  boxes[boxIndex= 1 ]:  Set(3) { '7', '1', '9' }
c:  6 ______________
c:  7 ______________
c:  8 ______________
r:  2 --------------------------------------------------------------------------------------------------------
c:  0 ______________
c:  1 ______________
rows[r= 2 ]:  Set(0) {}  cols[c= 1 ]:  Set(1) { '3' }  boxes[boxIndex= 0 ]:  Set(3) { '5', '3', '6' }
c:  2 ______________
rows[r= 2 ]:  Set(1) { '9' }  cols[c= 2 ]:  Set(0) {}  boxes[boxIndex= 0 ]:  Set(4) { '5', '3', '6', '9' }
c:  3 ______________
c:  4 ______________
c:  5 ______________
c:  6 ______________
c:  7 ______________
rows[r= 2 ]:  Set(2) { '9', '8' }  cols[c= 7 ]:  Set(0) {}  boxes[boxIndex= 2 ]:  Set(0) {}
c:  8 ______________
r:  3 --------------------------------------------------------------------------------------------------------
c:  0 ______________
rows[r= 3 ]:  Set(0) {}  cols[c= 0 ]:  Set(2) { '5', '6' }  boxes[boxIndex= 3 ]:  Set(0) {}
c:  1 ______________
c:  2 ______________
c:  3 ______________
c:  4 ______________
rows[r= 3 ]:  Set(1) { '8' }  cols[c= 4 ]:  Set(2) { '7', '9' }  boxes[boxIndex= 4 ]:  Set(0) {}
c:  5 ______________
c:  6 ______________
c:  7 ______________
c:  8 ______________
rows[r= 3 ]:  Set(2) { '8', '6' }  cols[c= 8 ]:  Set(0) {}  boxes[boxIndex= 5 ]:  Set(0) {}
r:  4 --------------------------------------------------------------------------------------------------------
c:  0 ______________
rows[r= 4 ]:  Set(0) {}  cols[c= 0 ]:  Set(3) { '5', '6', '8' }  boxes[boxIndex= 3 ]:  Set(1) { '8' }
c:  1 ______________
c:  2 ______________
c:  3 ______________
rows[r= 4 ]:  Set(1) { '4' }  cols[c= 3 ]:  Set(1) { '1' }  boxes[boxIndex= 4 ]:  Set(1) { '6' }
c:  4 ______________
c:  5 ______________
rows[r= 4 ]:  Set(2) { '4', '8' }  cols[c= 5 ]:  Set(1) { '5' }  boxes[boxIndex= 4 ]:  Set(2) { '6', '8' }
c:  6 ______________
c:  7 ______________
c:  8 ______________
rows[r= 4 ]:  Set(3) { '4', '8', '3' }  cols[c= 8 ]:  Set(1) { '3' }  boxes[boxIndex= 5 ]:  Set(1) { '3' }
r:  5 --------------------------------------------------------------------------------------------------------
c:  0 ______________
rows[r= 5 ]:  Set(0) {}  cols[c= 0 ]:  Set(4) { '5', '6', '8', '4' }  boxes[boxIndex= 3 ]:  Set(2) { '8', '4' }
c:  1 ______________
c:  2 ______________
c:  3 ______________
c:  4 ______________
rows[r= 5 ]:  Set(1) { '7' }  cols[c= 4 ]:  Set(3) { '7', '9', '6' }  boxes[boxIndex= 4 ]:  Set(3) { '6', '8', '3' }
c:  5 ______________
c:  6 ______________
c:  7 ______________
c:  8 ______________
rows[r= 5 ]:  Set(2) { '7', '2' }  cols[c= 8 ]:  Set(2) { '3', '1' }  boxes[boxIndex= 5 ]:  Set(2) { '3', '1' }
r:  6 --------------------------------------------------------------------------------------------------------
c:  0 ______________
c:  1 ______________
rows[r= 6 ]:  Set(0) {}  cols[c= 1 ]:  Set(2) { '3', '9' }  boxes[boxIndex= 6 ]:  Set(0) {}
c:  2 ______________
c:  3 ______________
c:  4 ______________
c:  5 ______________
c:  6 ______________
rows[r= 6 ]:  Set(1) { '6' }  cols[c= 6 ]:  Set(0) {}  boxes[boxIndex= 8 ]:  Set(0) {}
c:  7 ______________
rows[r= 6 ]:  Set(2) { '6', '2' }  cols[c= 7 ]:  Set(1) { '6' }  boxes[boxIndex= 8 ]:  Set(1) { '2' }
c:  8 ______________
r:  7 --------------------------------------------------------------------------------------------------------
c:  0 ______________
c:  1 ______________
c:  2 ______________
c:  3 ______________
rows[r= 7 ]:  Set(0) {}  cols[c= 3 ]:  Set(2) { '1', '8' }  boxes[boxIndex= 7 ]:  Set(0) {}
c:  4 ______________
rows[r= 7 ]:  Set(1) { '4' }  cols[c= 4 ]:  Set(4) { '7', '9', '6', '2' }  boxes[boxIndex= 7 ]:  Set(1) { '4' }
c:  5 ______________
rows[r= 7 ]:  Set(2) { '4', '1' }  cols[c= 5 ]:  Set(2) { '5', '3' }  boxes[boxIndex= 7 ]:  Set(2) { '4', '1' }
c:  6 ______________
c:  7 ______________
c:  8 ______________
rows[r= 7 ]:  Set(3) { '4', '1', '9' }  cols[c= 8 ]:  Set(3) { '3', '1', '6' }  boxes[boxIndex= 8 ]:  Set(2) { '2', '8' }
r:  8 --------------------------------------------------------------------------------------------------------
c:  0 ______________
c:  1 ______________
c:  2 ______________
c:  3 ______________
c:  4 ______________
rows[r= 8 ]:  Set(0) {}  cols[c= 4 ]:  Set(5) { '7', '9', '6', '2', '1' }  boxes[boxIndex= 7 ]:  Set(3) { '4', '1', '9' }
c:  5 ______________
c:  6 ______________
c:  7 ______________
rows[r= 8 ]:  Set(1) { '8' }  cols[c= 7 ]:  Set(2) { '6', '8' }  boxes[boxIndex= 8 ]:  Set(3) { '2', '8', '5' }
c:  8 ______________
rows[r= 8 ]:  Set(2) { '8', '7' }  cols[c= 8 ]:  Set(4) { '3', '1', '6', '5' }  boxes[boxIndex= 8 ]:  Set(4) { '2', '8', '5', '7' }
________________________________________________________________________________________________________________________________________________________________________
rows:  [
  Set(3) { '5', '3', '7' },
  Set(4) { '6', '1', '9', '5' },
  Set(3) { '9', '8', '6' },
  Set(3) { '8', '6', '3' },
  Set(4) { '4', '8', '3', '1' },
  Set(3) { '7', '2', '6' },
  Set(3) { '6', '2', '8' },
  Set(4) { '4', '1', '9', '5' },
  Set(3) { '8', '7', '9' }
]  cols:  [
  Set(5) { '5', '6', '8', '4', '7' },
  Set(3) { '3', '9', '6' },
  Set(1) { '8' },
  Set(3) { '1', '8', '4' },
  Set(6) { '7', '9', '6', '2', '1', '8' },
  Set(3) { '5', '3', '9' },
  Set(1) { '2' },
  Set(3) { '6', '8', '7' },
  Set(5) { '3', '1', '6', '5', '9' }
]  boxes:  [
  Set(5) { '5', '3', '6', '9', '8' },
  Set(4) { '7', '1', '9', '5' },
  Set(1) { '6' },
  Set(3) { '8', '4', '7' },
  Set(4) { '6', '8', '3', '2' },
  Set(3) { '3', '1', '6' },
  Set(1) { '6' },
  Set(4) { '4', '1', '9', '8' },
  Set(5) { '2', '8', '5', '7', '9' }
]
Output:  true
```
## Board (Example 2):
```css
[
    ["8", "3", ".", ".", "7", ".", ".", ".", "."],
    ["6", ".", ".", "1", "9", "5", ".", ".", "."],
    [".", "9", "8", ".", ".", ".", ".", "6", "."],
    ["8", ".", ".", ".", "6", ".", ".", ".", "3"],
    ["4", ".", ".", "8", ".", "3", ".", ".", "1"],
    ["7", ".", ".", ".", "2", ".", ".", ".", "6"],
    [".", "6", ".", ".", ".", ".", "2", "8", "."],
    [".", ".", ".", "4", "1", "9", ".", ".", "5"],
    [".", ".", ".", ".", "8", ".", ".", "7", "9"]
];
```
### Output:
```css
r:  0 -------------------------------------------------------
c:  0 ______________ char:  8
rows[r= 0 ]:  Set(0) {}  cols[c= 0 ]:  Set(0) {}  boxes[boxIndex= 0 ]:  Set(0) {}
c:  1 ______________ char:  3
rows[r= 0 ]:  Set(1) { '8' }  cols[c= 1 ]:  Set(0) {}  boxes[boxIndex= 0 ]:  Set(1) { '8' }
c:  2 ______________ char:  .
c:  3 ______________ char:  .
c:  4 ______________ char:  7
rows[r= 0 ]:  Set(2) { '8', '3' }  cols[c= 4 ]:  Set(0) {}  boxes[boxIndex= 1 ]:  Set(0) {}
c:  5 ______________ char:  .
c:  6 ______________ char:  .
c:  7 ______________ char:  .
c:  8 ______________ char:  .
r:  1 -------------------------------------------------------
c:  0 ______________ char:  6
rows[r= 1 ]:  Set(0) {}  cols[c= 0 ]:  Set(1) { '8' }  boxes[boxIndex= 0 ]:  Set(2) { '8', '3' }
c:  1 ______________ char:  .
c:  2 ______________ char:  .
c:  3 ______________ char:  1
rows[r= 1 ]:  Set(1) { '6' }  cols[c= 3 ]:  Set(0) {}  boxes[boxIndex= 1 ]:  Set(1) { '7' }
c:  4 ______________ char:  9
rows[r= 1 ]:  Set(2) { '6', '1' }  cols[c= 4 ]:  Set(1) { '7' }  boxes[boxIndex= 1 ]:  Set(2) { '7', '1' }
c:  5 ______________ char:  5
rows[r= 1 ]:  Set(3) { '6', '1', '9' }  cols[c= 5 ]:  Set(0) {}  boxes[boxIndex= 1 ]:  Set(3) { '7', '1', '9' }
c:  6 ______________ char:  .
c:  7 ______________ char:  .
c:  8 ______________ char:  .
r:  2 -------------------------------------------------------
c:  0 ______________ char:  .
c:  1 ______________ char:  9
rows[r= 2 ]:  Set(0) {}  cols[c= 1 ]:  Set(1) { '3' }  boxes[boxIndex= 0 ]:  Set(3) { '8', '3', '6' }
c:  2 ______________ char:  8
rows[r= 2 ]:  Set(1) { '9' }  cols[c= 2 ]:  Set(0) {}  boxes[boxIndex= 0 ]:  Set(4) { '8', '3', '6', '9' }
Duplicate Found (Invalid Sudoku)
______________________________________________________________________________________________________________________
Output:  false
```

## Explanation:
- We create three arrays of sets: `rows`, `cols`, and `boxes` to store the digits we have encountered for each row, column, and 3x3 sub-box respectively.
- We iterate over each cell in the board:
        - If the cell is not empty (`.`), we compute the index for the corresponding 3x3 sub-box.
        - We check if the digit already exists in the corresponding row, column, or sub-box set.
        - If it does, the board is invalid.
        - Otherwise, we add the digit to the respective sets.
- If we complete the iteration without finding any duplicates, the board is valid and we return `true`.

## Complexity Analysis
### Time Complexity:
The time complexity of this solution is `O(n)`, where `n` is the total number of cells in the board. Since the board is always 9x9, `n=81`.

This solution effectively checks all the constraints for a valid Sudoku board with a time complexity of `O(n)` and space complexity of `O(1)`, considering the fixed size of the board (9x9).
