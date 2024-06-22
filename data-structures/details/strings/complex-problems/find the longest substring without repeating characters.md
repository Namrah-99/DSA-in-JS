# Find the Longest Substring Without Repeating Characters:

## Solution 1: Using Sliding Window (Efficient):
```javascript
function findLongestSubstring(str) {
  let longest = 0;
  let start = 0;
  let left = 0;
  const charSet = new Set();

  for (let right = 0; right < str.length; right++) {
    const char = str[right];

    while (charSet.has(char)) {
      charSet.delete(str[left]);
      left++;
    }

    charSet.add(char);

    if (right - left + 1 > longest) {
      longest = right - left + 1;
      start = left;
    }
  }

  return str.substring(start, start + longest);
}

console.log(findLongestSubstring("abcabcbb")); // Output: "abc"
```

### Sliding Window Technique
The sliding window technique is a method for keeping track of a range (or window) of elements within a sequence that satisfies certain conditions. In this case, the condition is that the window contains unique characters.

### Step-by-Step Breakdown
Here's a detailed explanation of each part of the function:

#### Initialization:

```javascript
let longest = 0;  // Stores the length of the longest substring found
let start = 0;    // Stores the starting index of the longest substring found
let left = 0;     // Left pointer of the sliding window
const charSet = new Set();  // Set to keep track of unique characters in the current window
```
#### Iterate through the string with the right pointer:

```javascript
for (let right = 0; right < str.length; right++) {
  const char = str[right];  // Current character at the right pointer
```
#### Check if the character is already in the set:

```javascript
while (charSet.has(char)) {
  charSet.delete(str[left]);  // Remove the character at the left pointer from the set
  left++;  // Move the left pointer to the right
}
```
This while loop ensures that all characters in the window are unique. If a duplicate character is found (charSet.has(char) is true), it removes characters from the left of the window until the duplicate character is removed.

#### Add the current character to the set:

```javascript
charSet.add(char);  // Add the current character to the set
```

#### Update the longest substring found:

```javascript
if (right - left + 1 > longest) {
  longest = right - left + 1;  // Update the length of the longest substring
  start = left;  // Update the starting index of the longest substring
}
```
This condition checks if the current window size (right - left + 1) is greater than the previously recorded longest substring. If true, it updates longest and start.

#### Return the longest substring:

```javascript
return str.substring(start, start + longest);  // Return the longest substring without repeating characters
```
### Example Walkthrough with "abcabcbb"
Let's walk through the function with the input string "abcabcbb":

#### Initialization:

- longest = 0
- start = 0
- left = 0
- charSet = {}

#### First iteration (right = 0):

- char = 'a'
- charSet = { 'a' }
- right - left + 1 = 1 (greater than longest = 0)
- Update longest = 1
- Update start = 0

#### Second iteration (right = 1):

- char = 'b'
- charSet = { 'a', 'b' }
- right - left + 1 = 2 (greater than longest = 1)
- Update longest = 2
- Update start = 0

#### Third iteration (right = 2):

- char = 'c'
- charSet = { 'a', 'b', 'c' }
- right - left + 1 = 3 (greater than longest = 2)
- Update longest = 3
- Update start = 0

#### Fourth iteration (right = 3):

- char = 'a'
- Since 'a' is in charSet, enter the while loop:
    - Remove str[left] (which is 'a'): charSet = { 'b', 'c' }, left = 1
- Add 'a' to charSet: charSet = { 'b', 'c', 'a' }
- right - left + 1 = 3 (equal to longest = 3)
- No update to longest or start

#### Fifth iteration (right = 4):

- char = 'b'
- Since 'b' is in charSet, enter the while loop:
- Remove str[left] (which is 'b'): charSet = { 'c', 'a' }, left = 2
- Add 'b' to charSet: charSet = { 'c', 'a', 'b' }
- right - left + 1 = 3 (equal to longest = 3)
- No update to longest or start

#### Sixth iteration (right = 5):

- char = 'c'
- Since 'c' is in charSet, enter the while loop:
    - Remove str[left] (which is 'c'): charSet = { 'a', 'b' }, left = 3
- Add 'c' to charSet: charSet = { 'a', 'b', 'c' }
- right - left + 1 = 3 (equal to longest = 3)
- No update to longest or start

#### Seventh iteration (right = 6):

- char = 'b'
- Since 'b' is in charSet, enter the while loop:
    - Remove str[left] (which is 'a'): charSet = { 'b', 'c' }, left = 4
    - Remove str[left] (which is 'b'): charSet = { 'c' }, left = 5
- Add 'b' to charSet: charSet = { 'c', 'b' }
- right - left + 1 = 2 (less than longest = 3)
- No update to longest or start

#### Eighth iteration (right = 7):

- char = 'b'
- Since 'b' is in charSet, enter the while loop:
- Remove str[left] (which is 'c'): charSet = { 'b' }, left = 6
- Remove str[left] (which is 'b'): charSet = { }, left = 7
- Add 'b' to charSet: charSet = { 'b' }
- right - left + 1 = 1 (less than longest = 3)
- No update to longest or start

#### Conclusion
The longest substring without repeating characters is "abc" with a length of 3. The function correctly identifies this and returns "abc". The sliding window approach ensures that we efficiently find the longest substring by adjusting the window size dynamically based on the presence of duplicate characters.

## Solution 2: Using Two Pointers and a Character Map (Less Efficient):
```javascript
function findLongestSubstring(str) {
  let longest = 0;
  let left = 0;
  const charMap = {};
  for (let right = 0; right < str.length; right++) {
    const char = str[right];
    if (charMap[char] !== undefined && charMap[char] >= left) {
      left = Math.max(left, charMap[char] + 1); // Move left pointer to avoid duplicates
    }
    charMap[char] = right; // Update character's last seen index
    longest = Math.max(longest, right - left + 1);
  }
  return str.substring(left, left + longest);
}

console.log(findLongestSubstring("abcabcbb")); // Output: "abc"
```

### Explanation
The function findLongestSubstring uses two pointers (left and right) and a character map (charMap) to keep track of the last seen index of each character. Here's a detailed explanation of how it works:

#### Initialization:

```javascript
let longest = 0;       // To store the length of the longest substring found
let left = 0;          // Left pointer of the sliding window
const charMap = {};    // Map to keep track of the last seen index of each character
```
#### Iterate through the string with the right pointer:

```javascript
for (let right = 0; right < str.length; right++) {
  const char = str[right];  // Current character at the right pointer
```
#### Check if the character has been seen before and is within the current window:

```javascript
if (charMap[char] !== undefined && charMap[char] >= left) {
  left = Math.max(left, charMap[char] + 1);  // Move the left pointer to avoid duplicates
}
If the current character (char) has been seen before (charMap[char] !== undefined) and its last seen index is greater than or equal to left, it means the character is within the current window. To avoid duplicates, move the left pointer to one position after the last seen index of the current character.
```
#### Update the character's last seen index:

```javascript
charMap[char] = right;  // Update the last seen index of the current character
```
#### Update the longest substring length:

```javascript
longest = Math.max(longest, right - left + 1);  // Update the length of the longest substring found
```
#### Return the longest substring:

```javascript
return str.substring(left, left + longest);  // Return the longest substring without repeating characters
```
### Example Walkthrough with "abcabcbb"

Let's walk through the function with the input string "abcabcbb":

#### Initialization:

- longest = 0
- left = 0
- charMap = {}

#### First iteration (right = 0):

- char = 'a'
- charMap = { 'a': 0 }
- longest = 1 (since right - left + 1 = 1)

#### Second iteration (right = 1):

- char = 'b'
- charMap = { 'a': 0, 'b': 1 }
- longest = 2 (since right - left + 1 = 2)

#### Third iteration (right = 2):

- char = 'c'
- charMap = { 'a': 0, 'b': 1, 'c': 2 }
- longest = 3 (since right - left + 1 = 3)

#### Fourth iteration (right = 3):

- char = 'a'
- charMap = { 'a': 0, 'b': 1, 'c': 2 }
- Since 'a' is in charMap and charMap['a'] >= left, move left to charMap['a'] + 1 = 1
- charMap = { 'a': 3, 'b': 1, 'c': 2 }
- longest = 3 (since right - left + 1 = 3)

#### Fifth iteration (right = 4):

- char = 'b'
- charMap = { 'a': 3, 'b': 1, 'c': 2 }
- Since 'b' is in charMap and charMap['b'] >= left, move left to charMap['b'] + 1 = 2
- charMap = { 'a': 3, 'b': 4, 'c': 2 }
- longest = 3 (since right - left + 1 = 3)

#### Sixth iteration (right = 5):

- char = 'c'
- charMap = { 'a': 3, 'b': 4, 'c': 2 }
- Since 'c' is in charMap and charMap['c'] >= left, move left to charMap['c'] + 1 = 3
- charMap = { 'a': 3, 'b': 4, 'c': 5 }
- longest = 3 (since right - left + 1 = 3)

#### Seventh iteration (right = 6):

- char = 'b'
- charMap = { 'a': 3, 'b': 4, 'c': 5 }
- Since 'b' is in charMap and charMap['b'] >= left, move left to charMap['b'] + 1 = 5
- charMap = { 'a': 3, 'b': 6, 'c': 5 }
- longest = 3 (since right - left + 1 = 2)

#### Eighth iteration (right = 7):

- char = 'b'
- charMap = { 'a': 3, 'b': 6, 'c': 5 }
- Since 'b' is in charMap and charMap['b'] >= left, move left to charMap['b'] + 1 = 7
- charMap = { 'a': 3, 'b': 7, 'c': 5 }
- longest = 3 (since right - left + 1 = 1)

### Conclusion
The longest substring without repeating characters is "abc" with a length of 3. The function correctly identifies this and returns "abc". The use of a character map allows the function to efficiently update the position of the left pointer, ensuring that the window always contains unique characters. This solution is less efficient compared to the sliding window technique but provides a clear and understandable approach to solving the problem.

## Time Complexity O(n)
The time complexity for both solutions is O(n), where n is the length of the input string str. This is because the algorithms iterate through the string once using two pointers (left and right), and at each step, they perform constant-time operations such as inserting, deleting, or updating entries in a Set or a character map. Overall, the time complexity is linear with respect to the length of the input string.
