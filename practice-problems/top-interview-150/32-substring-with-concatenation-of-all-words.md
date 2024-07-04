# 30. Substring with Concatenation of All Words

## Problem Breakdown
To solve the problem of finding all starting indices of concatenated substrings in a given string s that exactly contains all the strings of any permutation of the given array of strings words, we can use the `sliding window technique`.

### Understanding the Problem:
- We need to find all starting indices in `s` where a concatenated string of all the `words` (in any permutation ( arrangement of all the elements of a set into a particular order or sequence ) ) in `words` starts.
- Each word in words is of the same length.
### Example Explanation:
#### Example 1:
```
Input: s = "barfoothefoobarman", words = ["foo","bar"]
Output: [0, 9]
```
- Explanation: The substrings starting at indices 0 and 9 are "barfoo" and "foobar", which are concatenations of "bar" and "foo" (any permutation).
#### Example 2:
```
Input: s = "wordgoodgoodgoodbestword", words = ["word","good","best","word"]
Output: []
```
- Explanation: No such concatenated substring exists.

### Constraints:
- 1 <= s.length <= 10^4
- 1 <= words.length <= 5000
- 1 <= words[i].length <= 30
`s` and `words[i]` consist of lowercase English letters.

## Approach
### Calculate Required Lengths:
- `wordLen`: Length of each word in words.
- `wordsLen`: Total length of all words concatenated together (number of words multiplied by the length of one word).
### Use a Sliding Window:
- Slide a window of size `wordsLen` across `s`.
- Check if the substring matches any permutation of the `words` in words.
### Use a HashMap:
- Maintain a hashmap of word counts for `words`.
- For each window, use another hashmap to track counts of words within the window.

## Solution Code
```javascript
function findSubstring(s, words) {
    // Length of each word in the words array
    const wordLen = words[0].length;
    // Total length of the concatenated string formed by all words
    const wordsLen = wordLen * words.length;
    // Length of the input string s
    const sLen = s.length;

    // If the input string is shorter than the total length of concatenated words, return an empty array
    if (sLen < wordsLen) return [];

    // Create a map to count the occurrences of each word in the words array
    const wordsCount = new Map();
    for (const word of words) {
        wordsCount.set(word, (wordsCount.get(word) || 0) + 1);
    }

    // Result array to store starting indices of concatenated substrings
    const result = [];

    // Traverse each character in the string up to the length of a word
    for (let i = 0; i < wordLen; i++) {
        // Initialize left and right pointers and a counter for the current window
        let left = i, right = i, currentCount = 0;
        // Create a map to count the occurrences of words in the current window
        const windowCount = new Map();

        // Expand the window by moving the right pointer
        while (right + wordLen <= sLen) {
            // Extract a word from the current position of the right pointer
            const word = s.substring(right, right + wordLen);
            // Move the right pointer to the next word position
            right += wordLen;

            // If the extracted word is in the words array
            if (wordsCount.has(word)) {
                // Increment the count of the word in the window
                windowCount.set(word, (windowCount.get(word) || 0) + 1);
                currentCount++;

                // If the word count in the window exceeds the count in the words array
                while (windowCount.get(word) > wordsCount.get(word)) {
                    // Remove the leftmost word from the window
                    const leftWord = s.substring(left, left + wordLen);
                    windowCount.set(leftWord, windowCount.get(leftWord) - 1);
                    currentCount--;
                    // Move the left pointer to the right by the length of a word
                    left += wordLen;
                }

                // If the current window contains all words exactly once, store the starting index
                if (currentCount === words.length) {
                    result.push(left);
                }
            } else {
                // If the extracted word is not in the words array, reset the window
                windowCount.clear();
                currentCount = 0;
                // Move the left pointer to the current right position
                left = right;
            }
        }
    }

    // Return the result array containing starting indices of concatenated substrings
    return result;
}

// Example usage
console.log(findSubstring("barfoothefoobarman", ["foo", "bar"])); // Output: [0, 9]
console.log(findSubstring("wordgoodgoodgoodbestword", ["word", "good", "best", "word"])); // Output: []
console.log(findSubstring("barfoofoobarthefoobarman", ["bar", "foo", "the"])); // Output: [6, 9, 12]
```

```css
s:  barfoothefoobarman  words:  [ 'foo', 'bar' ]
wordLen:  3  wordsLen:  6  sLen:  18
wordsCount:  Map(2) { 'foo' => 1, 'bar' => 1 }
________________________________________________________ i:  0
windowCount:  Map(0) {}
 --------------------------------------------- 
right:  0  wordLen:  3  sLen:  18
word:  bar
right:  3
windowCount:  Map(1) { 'bar' => 1 }
currentCount:  1
 --------------------------------------------- 
right:  3  wordLen:  3  sLen:  18
word:  foo
right:  6
windowCount:  Map(2) { 'bar' => 1, 'foo' => 1 }
currentCount:  2
result:  [ 0 ]  currentCount:  2  words.length:  2
 --------------------------------------------- 
right:  6  wordLen:  3  sLen:  18
word:  the
right:  9
windowCount:  Map(0) {}  currentCount:  0  left:  9
 --------------------------------------------- 
right:  9  wordLen:  3  sLen:  18
word:  foo
right:  12
windowCount:  Map(1) { 'foo' => 1 }
currentCount:  1
 --------------------------------------------- 
right:  12  wordLen:  3  sLen:  18
word:  bar
right:  15
windowCount:  Map(2) { 'foo' => 1, 'bar' => 1 }
currentCount:  2
result:  [ 0, 9 ]  currentCount:  2  words.length:  2
 --------------------------------------------- 
right:  15  wordLen:  3  sLen:  18
word:  man
right:  18
windowCount:  Map(0) {}  currentCount:  0  left:  18
________________________________________________________ i:  1
windowCount:  Map(0) {}
 --------------------------------------------- 
right:  1  wordLen:  3  sLen:  18
word:  arf
right:  4
windowCount:  Map(0) {}  currentCount:  0  left:  4
 --------------------------------------------- 
right:  4  wordLen:  3  sLen:  18
word:  oot
right:  7
windowCount:  Map(0) {}  currentCount:  0  left:  7
 --------------------------------------------- 
right:  7  wordLen:  3  sLen:  18
word:  hef
right:  10
windowCount:  Map(0) {}  currentCount:  0  left:  10
 --------------------------------------------- 
right:  10  wordLen:  3  sLen:  18
word:  oob
right:  13
windowCount:  Map(0) {}  currentCount:  0  left:  13
 --------------------------------------------- 
right:  13  wordLen:  3  sLen:  18
word:  arm
right:  16
windowCount:  Map(0) {}  currentCount:  0  left:  16
________________________________________________________ i:  2
windowCount:  Map(0) {}
 --------------------------------------------- 
right:  2  wordLen:  3  sLen:  18
word:  rfo
right:  5
windowCount:  Map(0) {}  currentCount:  0  left:  5
 --------------------------------------------- 
right:  5  wordLen:  3  sLen:  18
word:  oth
right:  8
windowCount:  Map(0) {}  currentCount:  0  left:  8
 --------------------------------------------- 
right:  8  wordLen:  3  sLen:  18
word:  efo
right:  11
windowCount:  Map(0) {}  currentCount:  0  left:  11
 --------------------------------------------- 
right:  11  wordLen:  3  sLen:  18
word:  oba
right:  14
windowCount:  Map(0) {}  currentCount:  0  left:  14
 --------------------------------------------- 
right:  14  wordLen:  3  sLen:  18
word:  rma
right:  17
windowCount:  Map(0) {}  currentCount:  0  left:  17
result:  [ 0, 9 ]
[ 0, 9 ]
```

## Explanation of the Code
#### Initialization:
- `wordLen`: The length of each word.
- `wordsLen`: The total length of the concatenated words.
- `wordsCount`: A hashmap to store the count of each word in words.
#### Sliding Window:
- For each possible starting index within the range of `wordLen`, slide a window of size `wordsLen` across `s`.
- Use `windowCount` to keep track of word counts within the current window.
- Adjust the window's `start` and `end` positions based on whether the word counts match the required counts.
#### Result:
- If the current window matches the required counts, add the starting index to the `result`.

## Complexity Analysis
### Time Complexity
- The time complexity of this approach is `O(n * wordLen)`, which is linear with respect to the length of the string `s`, making it efficient for large inputs.
### Space Complexity
- The `wordsCount` and `windowCount` maps together use `O(m)` space.
- The `result` array uses `O(n)` space in the worst case.
Therefore, the total space complexity is `O(m + n)`.
