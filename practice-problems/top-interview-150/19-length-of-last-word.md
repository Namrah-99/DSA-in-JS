# 58. Length of Last Word

## Leetcode Problem
https://leetcode.com/problems/length-of-last-word/description/?envType=study-plan-v2&envId=top-interview-150

## Solution Code
```javascript
var lengthOfLastWord = function (s) {
    s = s.trim().split(' ');
    return s[s.length - 1].length;
};
// Example usage:
console.log(lengthOfLastWord("luffy is still joyboy")); // Output: 6
```

## Explaantion
- Trim any trailing spaces from the string.
- Split the string by spaces to get an array of words.
- Return the length of the last element in the array.

## Complexity Analysis
#### Time Complexity:
- trim(): `O(n)`, where n is the length of the string.
- split(' '): `O(n)`, where n is the length of the string.
- Accessing the last element and getting its length: `O(1)`.
Therefore, the overall time complexity of the function is `O(n)`.

#### Space Complexity:
- The trim() method creates a new string that is a copy of the original string with the leading and trailing whitespace removed. This operation requires `O(n)` space, where n is the length of the string.
- The split(' ') method creates an array of words. In the worst case, where every character in the string is a space, the array would have n elements, each being an empty string. Therefore, this operation also requires `O(n)` space.
Therefore, the overall space complexity of the function is `O(n)`.
