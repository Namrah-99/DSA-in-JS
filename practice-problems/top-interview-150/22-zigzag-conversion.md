# 6. Zigzag Conversion

## Leetcode Problem
https://leetcode.com/problems/zigzag-conversion/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to convert a given string `s` into a zigzag pattern when written in `numRows` rows, and then concatenate the `rows` to form the resulting string.

### Example of Zigzag Conversion:
For example, if s = "PAYPALISHIRING" and numRows = 3, the zigzag pattern would look like this:

```css
P   A   H   N
A P L S I I G
Y   I   R
```
The resulting string obtained by reading line by line would be "PAHNAPLSIIGYIR".

## Approach
To solve this problem, we can simulate the zigzag pattern by iterating through the string and determining the correct row for each character based on its position and the current direction of traversal (down or up). Here's the step-by-step approach:

#### 1. Initialization:
- Create `numRows` arrays to hold characters for each row.
- Track the current row and the direction of traversal (`down` or `up`).
#### 2. Traversal:
- Iterate through each character in the string `s`.
- Append each character to the corresponding row array based on the current direction.
- Update the current row and direction appropriately:
    - If moving `down`, increment the current row.
    - If moving `up`, decrement the current row.
#### 3. Concatenation:
- After processing all characters, concatenate all rows to form the resulting string.

## Solution Code
```javascript
var convert = function (s, numRows) {
    if (numRows === 1) return s; // No change if numRows is 1

    let rows = new Array(numRows).fill(''); // [ '', '', '' ]
    let goingDown = false, currentRow = 0; // row index to which s[i] will be added

    for (let i = 0; i < s.length; i++) {
        rows[currentRow] += s[i]
        // when at 1st row, set direction of traversal to down 
        // when at last row, set direction of traversal to up
        if (currentRow === 0 || currentRow === numRows - 1) {
            goingDown = !goingDown;
        }
        // when direction of traversal set to down, increment the currentRow
        // when direction of traversal set to up, decrement the currentRow
        currentRow += goingDown ? 1 : -1;
    }
    // join all rows elements into single string
    return rows.join('')
};

// Example usage:
console.log('output: ',convert("PAYPALISHIRING", 3)); // Output: "PAHNAPLSIIGYIR"
console.log(convert("PAYPALISHIRING", 4)); // Output: "PINALSIGYAHRPI"
console.log(convert("A", 1)); // Output: "A"
```

## Output
```css
rows:  [ '', '', '' ]
i  0 , gD  false , cR  0 , rows[ 0 ] , rows  [ 'P', '', '' ]
gD:  true  , currentRow:  1
i  1 , gD  true , cR  1 , rows[ 1 ] , rows  [ 'P', 'A', '' ]
gD:  true  , currentRow:  2
i  2 , gD  true , cR  2 , rows[ 2 ] , rows  [ 'P', 'A', 'Y' ]
gD:  false  , currentRow:  1
i  3 , gD  false , cR  1 , rows[ 1 ] , rows  [ 'P', 'AP', 'Y' ]
gD:  false  , currentRow:  0
i  4 , gD  false , cR  0 , rows[ 0 ] , rows  [ 'PA', 'AP', 'Y' ]
gD:  true  , currentRow:  1
i  5 , gD  true , cR  1 , rows[ 1 ] , rows  [ 'PA', 'APL', 'Y' ]
gD:  true  , currentRow:  2
i  6 , gD  true , cR  2 , rows[ 2 ] , rows  [ 'PA', 'APL', 'YI' ]
gD:  false  , currentRow:  1
i  7 , gD  false , cR  1 , rows[ 1 ] , rows  [ 'PA', 'APLS', 'YI' ]
gD:  false  , currentRow:  0
i  8 , gD  false , cR  0 , rows[ 0 ] , rows  [ 'PAH', 'APLS', 'YI' ]
gD:  true  , currentRow:  1
i  9 , gD  true , cR  1 , rows[ 1 ] , rows  [ 'PAH', 'APLSI', 'YI' ]
gD:  true  , currentRow:  2
i  10 , gD  true , cR  2 , rows[ 2 ] , rows  [ 'PAH', 'APLSI', 'YIR' ]
gD:  false  , currentRow:  1
i  11 , gD  false , cR  1 , rows[ 1 ] , rows  [ 'PAH', 'APLSII', 'YIR' ]
gD:  false  , currentRow:  0
i  12 , gD  false , cR  0 , rows[ 0 ] , rows  [ 'PAHN', 'APLSII', 'YIR' ]
gD:  true  , currentRow:  1
i  13 , gD  true , cR  1 , rows[ 1 ] , rows  [ 'PAHN', 'APLSIIG', 'YIR' ]
gD:  true  , currentRow:  2
output:  PAHNAPLSIIGYIR
```

## Explanation:
#### 1. Initialization: 
- We initialize an array `rows` of length `numRows` to store characters for each row. `currentRow` keeps track of the current row we are filling, and `goingDown` indicates whether we are currently moving downward or upward in rows.
#### 2. Traversal: 
- We iterate through each character in the string `s`. For each character:
- Append it to `rows[currentRow]`.
- Toggle the direction (`goingDown`) when we reach the topmost or bottommost `row` (`currentRow === 0` or `currentRow === numRows - 1`).
- Update `currentRow` based on the direction.
#### 3. Concatenation: 
After filling `rows` with characters, join all rows into a single string and return it as the result.

## Complexity Analysis
- Time Complexity: `O(n)`, where n is the length of the string s. We iterate through each character exactly once.
- Space Complexity: `O(n)`, for the rows array which stores the characters. In the worst case, all characters could belong to a single row (`numRows = 1`).

This solution efficiently converts the input string into the zigzag pattern specified and concatenates the rows to form the final output string.
