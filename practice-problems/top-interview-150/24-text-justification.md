# 68. Text Justification

## Leetcode Problem
https://leetcode.com/problems/text-justification/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
The approach used in the provided code for text justification is the `Greedy Approach` combined with `String Manipulation`. Here's a detailed explanation:

### Explanation
#### Initialization:
- `result`: An array to store the final justified lines.
- `currentLineWords`: An array to store words of the current line being processed.
- `remainingWidth`: A variable to track the remaining width available in the current line.
#### Greedy Packing:
- The code iterates through each word in the input `words` array.
- For each word, it checks if the word can fit in the current line along with the necessary spaces.
- If it fits, the word is added to `currentLineWords` and the `remainingWidth` is updated.
- If it doesn't fit, the current line is justified using the `addWordToResult` function, and then a new line is started with the current word.
#### Justifying Lines:
- `addWordToResult` function is called when a word doesn't fit in the current line.
- This function calculates the number of spaces needed to justify the line.
- If the line has only one word, spaces are added to the end.
- If the line has multiple words, spaces are distributed as evenly as possible between words.
- The justified line is then added to the result.
#### Final Line Processing:
- After processing all words, any remaining words in `currentLineWords` are left-justified and added to the result.

## Solution Code
```javascript
var fullJustify = function(words, maxWidth) {
    const result = [];
    let currentLineWords  = [];
    let remainingWidth = maxWidth;
    // Greedy pack each line
    // when that fails add the line to the result with the added padding
    // and start a new line
    words.forEach(word => {
        // Check if the word fits in the current line
        // A word fits if theres enough room for the word and
        // a space between it and the word to the left
        if (word.length <= (remainingWidth - currentLineWords.length)) {
            currentLineWords.push(word);
            remainingWidth -= word.length;
        } else {
            // The word did not fit on the line, send this line for padding
            addWordToResult(result, currentLineWords.slice(), maxWidth);
           
            // Start a new line with the current word
            currentLineWords = [word];
            // reset the current line remainingWidth
            remainingWidth = maxWidth - word.length;
            
        }
    });
    
    // Final lines processing
    // According the rules this should only be left justified
    // so add all padding to the right not between the words
    if (currentLineWords.length) {
        let finalLine = currentLineWords.join(' ');
        finalLine += ' '.repeat(maxWidth - finalLine.length);
        result.push(finalLine);
    }
    return result;
};

// Max words are on each line now pad them with spaces
function addWordToResult(result, currentLineWords, maxWidth) {
    
    // How many spaces are needed
    let spacesNeeded = maxWidth - currentLineWords.reduce((acc, cur) => cur.length + acc, 0);
    // If there is only one word on the line
    // then just add the padding to the end and return
    if (currentLineWords.length === 1) {
        currentLineWords[0] += ' '.repeat(spacesNeeded);
        result.push(currentLineWords[0]);
        return;
    }
    
    // If the line has more than one word,
    // decrement the spaces which are created during the currentLineWords.join(' ')
    // which is n - 1 spaces
    spacesNeeded -= currentLineWords.length - 1;
    
    // All words except the last should have spaces added to their string
    const lastIndex = currentLineWords.length - 1;
    let currentIndex = 0;
    // If there are spaces to distribute, distribute them
    // evenly looping back to the beginning of the buffer
    while (spacesNeeded-- > 0) {
        currentLineWords[currentIndex] += ' ';
        currentIndex = (currentIndex + 1) % lastIndex;
    }
    
    result.push(currentLineWords.join(' '))
}

console.log('output: ',fullJustify(["This", "is", "an", "example", "of", "text", "justification."], 16))
```

## Output

```css

words:  [ 'This', 'is', 'an', 'example', 'of', 'text', 'justification.' ]  maxWidth:  16
------------------------------------------------------------------------------------
word:  This  remainingWidth:  16  currentLineWords.length:  0
currentLineWords:  [ 'This' ]  remainingWidth:  12
------------------------------------------------------------------------------------
word:  is  remainingWidth:  12  currentLineWords.length:  1
currentLineWords:  [ 'This', 'is' ]  remainingWidth:  10
------------------------------------------------------------------------------------
word:  an  remainingWidth:  10  currentLineWords.length:  2
currentLineWords:  [ 'This', 'is', 'an' ]  remainingWidth:  8
------------------------------------------------------------------------------------
word:  example  remainingWidth:  8  currentLineWords.length:  3
_______________________________addWordToResult start_______________________________
result:  []  currentLineWords:  [ 'This', 'is', 'an' ]  maxWidth:  16
spacesNeeded:  8
spacesNeeded:  6  lastIndex:  2  currentIndex:  0
spacesNeeded:  6
*********************
spacesNeeded:  5  currentIndex:  0
currentLineWords:  [ 'This ', 'is', 'an' ]
currentIndex:  1
*********************
spacesNeeded:  4  currentIndex:  1
currentLineWords:  [ 'This ', 'is ', 'an' ]
currentIndex:  0
*********************
spacesNeeded:  3  currentIndex:  0
currentLineWords:  [ 'This  ', 'is ', 'an' ]
currentIndex:  1
*********************
spacesNeeded:  2  currentIndex:  1
currentLineWords:  [ 'This  ', 'is  ', 'an' ]
currentIndex:  0
*********************
spacesNeeded:  1  currentIndex:  0
currentLineWords:  [ 'This   ', 'is  ', 'an' ]
currentIndex:  1
*********************
spacesNeeded:  0  currentIndex:  1
currentLineWords:  [ 'This   ', 'is   ', 'an' ]
currentIndex:  0
_____________________________addWordToResult ennd_______________________________
result:  [ 'This    is    an' ]  currentLineWords:  [ 'This', 'is', 'an' ]
currentLineWords:  [ 'example' ]  remainingWidth:  9
------------------------------------------------------------------------------------
word:  of  remainingWidth:  9  currentLineWords.length:  1
currentLineWords:  [ 'example', 'of' ]  remainingWidth:  7
------------------------------------------------------------------------------------
word:  text  remainingWidth:  7  currentLineWords.length:  2
currentLineWords:  [ 'example', 'of', 'text' ]  remainingWidth:  3
------------------------------------------------------------------------------------
word:  justification.  remainingWidth:  3  currentLineWords.length:  3
_______________________________addWordToResult start_______________________________
result:  [ 'This    is    an' ]  currentLineWords:  [ 'example', 'of', 'text' ]  maxWidth:  16
spacesNeeded:  3
spacesNeeded:  1  lastIndex:  2  currentIndex:  0
spacesNeeded:  1
*********************
spacesNeeded:  0  currentIndex:  0
currentLineWords:  [ 'example ', 'of', 'text' ]
currentIndex:  1
_____________________________addWordToResult ennd_______________________________
result:  [ 'This    is    an', 'example  of text' ]  currentLineWords:  [ 'example', 'of', 'text' ]
currentLineWords:  [ 'justification.' ]  remainingWidth:  2
result:  [ 'This    is    an', 'example  of text' ]
result:  [ 'This    is    an', 'example  of text', 'justification.  ' ]
output:  [ 'This    is    an', 'example  of text', 'justification.  ' ]
```

## Complexity Analysis
### Time Complexity
#### Greedy Packing:
- Iterating through the `words` array: `O(n)`, where `n` is the number of words.
- Each word is processed once to check if it fits in the current line and possibly multiple times to adjust spaces.
#### Justifying Lines:
- Calculating the number of spaces and distributing them in `addWordToResult` involves iterating through the words in the line, which can be at most `m` times, where `m` is the average number of words per line.

Overall Time Complexity: `O(n)`

### Space Complexity
- Storing the `result` and `currentLineWords` arrays requires `O(n)` space.
- Additional space for the operations like reduce, slice, and string manipulations is also `O(n)`.

Overall Space Complexity: `O(n)`
