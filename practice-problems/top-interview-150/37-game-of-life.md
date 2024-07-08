# 289. Game of Life

## Leetcode Problem
https://leetcode.com/problems/game-of-life/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The Game of Life is a cellular automaton devised by John Horton Conway in 1970. It consists of an m x n grid of cells, where each cell can be either `alive` (represented by `1`) or `dead` (represented by `0`). The state of each cell in the next generation is determined by the `states of its eight neighbors` according to the following rules:

- Any live cell with `fewer than two live` neighbors *dies*, as if by under-population.
- Any live cell with `two or three live` neighbors *lives* on to the next generation.
- Any live cell with `more than three` live neighbors *dies*, as if by over-population.
- Any dead cell with exactly three live neighbors becomes a *live* cell, as if by reproduction.

The goal is to return the next state of the board after applying these rules.

## Approach
To solve the problem, the solution involves two main steps:

- **First Pass:** Iterate through each cell and apply the rules to determine its next state. However, to ensure all updates happen simultaneously, we use temporary markers:
    - `2` to represent a `dead cell that will become live`.
    - `-1` to represent a `live cell that will become dead`.
- **Second Pass:** Finalize the states by converting the markers back to their *intended values*.

## Solution Code
```javascript
var gameOfLife = function (board) {
    // console.log('Original Matrix : ', board)
    for (let i = 0; i < board.length; i++) {
        for (let j = 0; j < board[0].length; j++) {
            let cell = board[i][j]
            let neighbours = getNeighbors(i, j, board);
            if (cell === 0 && neighbours === 3) {
                board[i][j] = 2; // reAlive
            }
            if (cell === 1 && (neighbours < 2 || neighbours > 3)) {
                board[i][j] = -1; // Died
            }
        }
    }

    for (let i = 0; i < board.length; i++) {
        for (let j = 0; j < board[0].length; j++) {
            if (board[i][j] === 2) board[i][j] = 1;
            if (board[i][j] === -1) board[i][j] = 0;
        }
    }

    // return board

};

var getNeighbors = function (r, c, board) {
    // console.log('r: ', r, ' c: ', c)
    let radius = [-1, 0, 1], count = 0;
    for (let i = 0; i < radius.length; i++) {
        for (let j = 0; j < radius.length; j++) {
            // console.log('board[r + radius[i]]: ', board[r + radius[i]], ' r + radius[i] ', r + radius[i])
            if (!(radius[i] === 0 && radius[j] === 0) && board[r + radius[i]] != null) {
                let neighbour = board[r + radius[i]][c + radius[j]];
                if (Math.abs(neighbour) === 1) count++;
            }
        }

    }
    return count
};

// Example usage:
console.log('Output: ',gameOfLife([[0,1,0],[0,0,1],[1,1,1],[0,0,0]])); // Output: [[0,0,0],[1,0,1],[0,1,1],[0,1,0]]
// console.log(gameOfLife([[1,1],[1,0]])); // Output: [[1,1],[1,1]]
```

## Output
```css
board:  0,1,0,0,0,1,1,1,1,0,0,0

i:  0  j:  0  board:  0,1,0,0,0,1,1,1,1,0,0,0

------------- radius.length:  3
r:  0  c:  0  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  
r:  0  c:  0  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  
r:  0  c:  0  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  0  board[r + radius[i]]:  
r:  0  c:  0  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,1,0
^^^^^^^^^^^^^^^  neighbor:  
r:  0  c:  0  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  0  board[r + radius[i]]:  0,1,0
r:  0  c:  0  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  0  board[r + radius[i]]:  0,1,0
^^^^^^^^^^^^^^^  neighbor:  1
r:  0  c:  0  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  
r:  0  c:  0  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  0  c:  0  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  0
-------------
neighbors:  1

_________

i:  0  j:  1  board:  0,1,0,0,0,1,1,1,1,0,0,0
------------- radius.length:  3
r:  0  c:  1  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  
r:  0  c:  1  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  
r:  0  c:  1  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  0  board[r + radius[i]]:  
r:  0  c:  1  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,1,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  0  c:  1  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  0  board[r + radius[i]]:  0,1,0
r:  0  c:  1  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  0  board[r + radius[i]]:  0,1,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  0  c:  1  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  0  c:  1  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  0  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  0  c:  1  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  0  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  1
-------------
neighbors:  1

_________

i:  0  j:  2  board:  0,-1,0,0,0,1,1,1,1,0,0,0
------------- radius.length:  3
r:  0  c:  2  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  
r:  0  c:  2  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  
r:  0  c:  2  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  0  board[r + radius[i]]:  
r:  0  c:  2  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  -1
r:  0  c:  2  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  1  board[r + radius[i]]:  0,-1,0
r:  0  c:  2  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  1  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  
r:  0  c:  2  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  0  c:  2  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  0  c:  2  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  2  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  
-------------
neighbors:  2

_________

i:  1  j:  0  board:  0,-1,0,0,0,1,1,1,1,0,0,0
------------- radius.length:  3
r:  1  c:  0  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  
r:  1  c:  0  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  1  c:  0  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  -1
r:  1  c:  0  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  
r:  1  c:  0  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  1  board[r + radius[i]]:  0,0,1
r:  1  c:  0  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  1  board[r + radius[i]]:  0,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  1  c:  0  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  1  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  
r:  1  c:  0  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  1  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  1  c:  0  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  2  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
-------------
neighbors:  3

_________

i:  1  j:  1  board:  0,-1,0,2,0,1,1,1,1,0,0,0
------------- radius.length:  3
r:  1  c:  1  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  1  c:  1  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  -1
r:  1  c:  1  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  1  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  1  c:  1  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  1  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  2
r:  1  c:  1  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  1  board[r + radius[i]]:  2,0,1
r:  1  c:  1  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  1  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  1  c:  1  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  2  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  1  c:  1  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  3  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  1  c:  1  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  4  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
-------------
neighbors:  5

_________

i:  1  j:  2  board:  0,-1,0,2,0,1,1,1,1,0,0,0
------------- radius.length:  3
r:  1  c:  2  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  -1
r:  1  c:  2  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  1  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  1  c:  2  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  1  board[r + radius[i]]:  0,-1,0
^^^^^^^^^^^^^^^  neighbor:  
r:  1  c:  2  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  1  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  1  c:  2  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  1  board[r + radius[i]]:  2,0,1
r:  1  c:  2  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  1  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  
r:  1  c:  2  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  1  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  1  c:  2  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  2  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  1  c:  2  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  3  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  
-------------
neighbors:  3

_________

i:  2  j:  0  board:  0,-1,0,2,0,1,1,1,1,0,0,0
------------- radius.length:  3
r:  2  c:  0  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  
r:  2  c:  0  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  2
r:  2  c:  0  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  0  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  0  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  
r:  2  c:  0  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  0  board[r + radius[i]]:  1,1,1
r:  2  c:  0  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  0  board[r + radius[i]]:  1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  2  c:  0  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  1  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  
r:  2  c:  0  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  1  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  0  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  1  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
-------------
neighbors:  1

_________

i:  2  j:  1  board:  0,-1,0,2,0,1,-1,1,1,0,0,0
------------- radius.length:  3
r:  2  c:  1  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  2
r:  2  c:  1  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  1  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  2  c:  1  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  1  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  -1
r:  2  c:  1  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  2  board[r + radius[i]]:  -1,1,1
r:  2  c:  1  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  2  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  2  c:  1  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  3  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  1  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  3  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  1  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  3  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
-------------
neighbors:  3

_________

i:  2  j:  2  board:  0,-1,0,2,0,1,-1,1,1,0,0,0
------------- radius.length:  3
r:  2  c:  2  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  2  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  2  c:  2  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  1  board[r + radius[i]]:  2,0,1
^^^^^^^^^^^^^^^  neighbor:  
r:  2  c:  2  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  1  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  2  c:  2  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  2  board[r + radius[i]]:  -1,1,1
r:  2  c:  2  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  2  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  
r:  2  c:  2  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  2  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  2  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  2  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  2  c:  2  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  2  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  
-------------
neighbors:  2

_________

i:  3  j:  0  board:  0,-1,0,2,0,1,-1,1,1,0,0,0
------------- radius.length:  3
r:  3  c:  0  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  
r:  3  c:  0  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  0  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  -1
r:  3  c:  0  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  1  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  3  c:  0  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  2  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  
r:  3  c:  0  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  2  board[r + radius[i]]:  0,0,0
r:  3  c:  0  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  2  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  3  c:  0  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  2  board[r + radius[i]]:  
r:  3  c:  0  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  2  board[r + radius[i]]:  
r:  3  c:  0  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  2  board[r + radius[i]]:  
-------------
neighbors:  2

_________

i:  3  j:  1  board:  0,-1,0,2,0,1,-1,1,1,0,0,0
------------- radius.length:  3
r:  3  c:  1  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  -1
r:  3  c:  1  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  1  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  3  c:  1  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  2  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  3  c:  1  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  3  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  3  c:  1  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  3  board[r + radius[i]]:  0,0,0
r:  3  c:  1  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  3  board[r + radius[i]]:  0,0,0
^^^^^^^^^^^^^^^  neighbor:  0
r:  3  c:  1  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  3  board[r + radius[i]]:  
r:  3  c:  1  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  3  board[r + radius[i]]:  
r:  3  c:  1  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  3  board[r + radius[i]]:  
-------------
neighbors:  3

_________

i:  3  j:  2  board:  0,-1,0,2,0,1,-1,1,1,0,2,0
------------- radius.length:  3
r:  3  c:  2  i:  0  j:  0  radius[i]:  -1  radius[j]:  -1 count:  0  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  3  c:  2  i:  0  j:  1  radius[i]:  -1  radius[j]:  0 count:  1  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  1
r:  3  c:  2  i:  0  j:  2  radius[i]:  -1  radius[j]:  1 count:  2  board[r + radius[i]]:  -1,1,1
^^^^^^^^^^^^^^^  neighbor:  
r:  3  c:  2  i:  1  j:  0  radius[i]:  0  radius[j]:  -1 count:  2  board[r + radius[i]]:  0,2,0
^^^^^^^^^^^^^^^  neighbor:  2
r:  3  c:  2  i:  1  j:  1  radius[i]:  0  radius[j]:  0 count:  2  board[r + radius[i]]:  0,2,0
r:  3  c:  2  i:  1  j:  2  radius[i]:  0  radius[j]:  1 count:  2  board[r + radius[i]]:  0,2,0
^^^^^^^^^^^^^^^  neighbor:  
r:  3  c:  2  i:  2  j:  0  radius[i]:  1  radius[j]:  -1 count:  2  board[r + radius[i]]:  
r:  3  c:  2  i:  2  j:  1  radius[i]:  1  radius[j]:  0 count:  2  board[r + radius[i]]:  
r:  3  c:  2  i:  2  j:  2  radius[i]:  1  radius[j]:  1 count:  2  board[r + radius[i]]:  
-------------
neighbors:  2

_________

Output:  0,0,0,1,0,1,0,1,1,0,1,0
```

## Explanation
### First Pass:
- Iterate through each cell `(i, j)` in the board.
- Count the number of live neighbors using the `getNeighbors` function.
### Apply the rules:
- If a dead cell has `exactly three live` neighbors, mark it with `2` (indicating it will become live).
- If a live cell has `fewer than two or more than three live` neighbors, mark it with `-1` (indicating it will become dead).
### Second Pass:
- Convert all temporary markers to their final states:
    - `2` to `1` (dead to live).
    - `-1` to `0` (live to dead).
### Complexity Analysis
#### Time Complexity: `O(m×n)`
- The algorithm iterates through each cell twice (first for applying rules, second for finalizing states).
- Counting neighbors for each cell also operates within `O(1)` since the maximum number of neighbors is fixed (8).
#### Space Complexity: `O(1)`
- The solution modifies the board in place without using additional space proportional to the input size.

### Visual Representation of Logic

Consider the following 3x3 board:

```lua
[[0, 1, 0],
 [0, 0, 1],
 [1, 1, 1]]
```
#### First Pass:
```
- (0, 0): 1 live neighbor → remains dead
- (0, 1): 1 live neighbor → dies (marked as -1)
- (0, 2): 2 live neighbors → remains dead
- (1, 0): 3 live neighbors → becomes live (marked as 2)
- (1, 1): 5 live neighbors → remains dead
- (1, 2): 3 live neighbors → remains live
- (2, 0): 1 live neighbor → dies (marked as -1)
- (2, 1): 3 live neighbors → remains live
- (2, 2): 2 live neighbors → remains live
```
##### Intermediate board after first pass:

```lua
[[0, -1, 0],
 [2, 0, 1],
 [-1, 1, 1]]
```
#### Second Pass:
- Convert -1 to 0 and 2 to 1.
##### Final board:
```lua
[[0, 0, 0],
 [1, 0, 1],
 [0, 1, 1]]
```

## Complexity Analysis
This approach efficiently calculates the next state of each cell in the Game of Life by leveraging temporary markers to ensure all updates occur simultaneously, achieving `O(m×n)` time complexity and `O(1)` space complexity. The getNeighbors function accurately counts live neighbors, and the two-pass system converts markers to final states, adhering to the game's rules.

## Algorithm Breakdown
### 1. Initial State:
- Traverse each cell in the board.
- For each cell, count the number of live neighbors (using getNeighbors).
- Apply the rules using encoded states:
    - `2` for a dead cell that becomes live.
    - `-1` for a live cell that becomes dead.
### 2. Final State:
- Traverse the board again to convert encoded states back to final states:
    - `-1` to `0`.
    - `2` to `1`.
### Visual Representation
Let's consider a sample board:

```lua
Initial Board:
[[0, 1, 0],
 [0, 0, 1],
 [1, 1, 1],
 [0, 0, 0]]
```
### Step 1: Traverse and Encode States
```
1. Cell (0, 0):

Initial state: 0 (dead)
Neighbors: 1
No change (still dead)

2. Cell (0, 1):

Initial state: 1 (live)
Neighbors: 1
Changes to -1 (will become dead due to under-population)

3. Cell (0, 2):

Initial state: 0 (dead)
Neighbors: 2
No change (still dead)

4. Cell (1, 0):

Initial state: 0 (dead)
Neighbors: 3
Changes to 2 (will become live due to reproduction)

5. Cell (1, 1):

Initial state: 0 (dead)
Neighbors: 5
No change (still dead)

6. Cell (1, 2):

Initial state: 1 (live)
Neighbors: 3
No change (still live)

7. Cell (2, 0):

Initial state: 1 (live)
Neighbors: 1
Changes to -1 (will become dead due to under-population)

8. Cell (2, 1):

Initial state: 1 (live)
Neighbors: 3
No change (still live)

9. Cell (2, 2):

Initial state: 1 (live)
Neighbors: 2
No change (still live)

10. Cell (3, 0):

Initial state: 0 (dead)
Neighbors: 2
No change (still dead)

11. Cell (3, 1):

Initial state: 0 (dead)
Neighbors: 3
Changes to 2 (will become live due to reproduction)

12. Cell (3, 2):
Initial state: 0 (dead)
Neighbors: 2
No change (still dead)
```
### Board After Encoding States:
```lua
[[0, -1, 0],
 [2, 0, 1],
 [-1, 1, 1],
 [0, 2, 0]]
```
### Step 2: Finalize States
- Convert -1 to 0:
    - Live cells that became dead.
- Convert 2 to 1:
    - Dead cells that became live.
### Final Board:

```lua
[[0, 0, 0],
 [1, 0, 1],
 [0, 1, 1],
 [0, 1, 0]]
```
### Sumary
- **Initial State:** Traverse and apply rules, encoding state changes as `2` for `dead to live` and `-1` for `live to dead`.
- **Final State:** Traverse again to convert `2` to `1` and `-1` to `0`.

## Purpose of the getNeighbors Function
The function calculates the number of live neighbors (cells with value 1) around a given cell at position (r, c) on the board.

### Code Explanation
```javascript
var getNeighbors = function(r, c, board) {
    let radius = [-1, 0, +1], count = 0;
    for (let i = 0; i < radius.length; i++) {
        for (let j = 0; j < radius.length; j++) {
            if (!(radius[i] == 0 && radius[j] == 0) && board[r + radius[i]] != null) {
                let neighbor = board[r + radius[i]][c + radius[j]];
                if (Math.abs(neighbor) == 1) count += 1; 
            }
        }
    }
    return count;
};
```
### Explanation with Visual Representation
1. Initialize the radius array:
    - `radius = [-1, 0, +1]` helps in checking the surrounding cells (top, bottom, left, right, and diagonals).

2. Initialize the count variable:
    - `count = 0` to keep track of the number of live neighbors.

3. Nested loops to iterate through neighbors:
    - The outer loop iterates through radius for rows `(i)`.
    - The inner loop iterates through radius for columns `(j`).

4. Check for current cell:
    - Skip checking the cell itself by ensuring `!(radius[i] == 0 && radius[j] == 0)`.

5. Check for valid neighbor cells:
    - Ensure the neighboring cell is within the board's bounds using `board[r + radius[i]] != null`.

6. Count live neighbors:
    - Check if the neighbor is alive `(Math.abs(neighbor) == 1)`, then increment `count`.

### Visual Representation
Consider a cell at position `(r, c)` in a 3x3 grid:

```lua
+---+---+---+
|   |   |   |
|   | r |   |  --> `r, c` is the cell we are checking
|   |   |   |
+---+---+---+
```
Surrounding cells:
```diff
+---+---+---+
| a | b | c |
+---+---+---+
| d | r | e |
+---+---+---+
| f | g | h |
+---+---+---+
```

```css
    j        0       1      2
i
         +-------+------+------+
0        | -1,-1 | -1,0 | -1,1 |
         +-------+------+------+
1        |  0,-1 | 0,0  |  0,1 |
         +-------+------+------+
2        |  1,-1 | 1,0  |  1,1 |
         +-------+------+------+

radius = [ -1 , 0 , 1 ]
radius[i] = radius[0] = -1
radius[j] = radius[2] =  1
```

- radius array [-1, 0, +1] corresponds to the relative positions of the neighbors.
- The nested loop checks all these positions around (r, c).
### Step-by-Step Neighbor Checking
#### Initialize:
```
radius = [-1, 0, +1]
count = 0
```
#### Iterate through radius:
```
i = -1, j = -1: Check board[r-1][c-1] (cell a)
i = -1, j = 0: Check board[r-1][c] (cell b)
i = -1, j = 1: Check board[r-1][c+1] (cell c)
i = 0, j = -1: Check board[r][c-1] (cell d)
i = 0, j = 0: Skip (it's the cell r itself)
i = 0, j = 1: Check board[r][c+1] (cell e)
i = 1, j = -1: Check board[r+1][c-1] (cell f)
i = 1, j = 0: Check board[r+1][c] (cell g)
i = 1, j = 1: Check board[r+1][c+1] (cell h)
```
Example
- For the cell (1, 1) in the following board:

```lua
[[0, 1, 0],
 [0, 0, 1],
 [1, 1, 1]]
```
Neighbors:
```
a = 0, b = 1, c = 0
d = 0, e = 1
f = 1, g = 1, h = 1
```
Neighbor Counting
```
1. Cell (0, 0) (a):
- Value: 0 (dead)
- Count: 0

2. Cell (0, 1) (b):
- Value: 1 (live)
- Count: 1

3. Cell (0, 2) (c):
- Value: 0 (dead)
- Count: 1

4. Cell (1, 0) (d):
- Value: 0 (dead)
- Count: 1

5. Skip Cell (1, 1) (r):
- It's the current cell itself

6. Cell (1, 2) (e):
- Value: 1 (live)
- Count: 2

7. Cell (2, 0) (f):
- Value: 1 (live)
- Count: 3

8. Cell (2, 1) (g):
- Value: 1 (live)
- Count: 4

9. Cell (2, 2) (h):
- Value: 1 (live)
- Count: 5
```
Thus, the getNeighbors function counts `5` live neighbors for the cell `(1, 1)` in this example.
