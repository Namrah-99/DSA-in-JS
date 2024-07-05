# 76. Minimum Window Substring

## Leetcode Problem
https://leetcode.com/problems/minimum-window-substring/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
To solve the problem of finding the minimum window substring in s that contains all characters from t, including duplicates, you can use the `sliding window technique`. This approach allows you to efficiently find the required substring with a time complexity of `O(m+n)`.

### Initialize Counters and Maps:
- Use two maps: one to count characters in `t` (`tCount`) and another to count characters within the current window (`windowCount`).
- Initialize variables to keep track of the size and bounds of the minimum window.
### Expand the Window:
- Use a `right` pointer to expand the window by adding characters from `s` to `windowCount`.
- Keep track of how many unique characters from `t` are fully matched in the current window using a variable (`formed`).
### Contract the Window:
- When the current window contains all characters from `t` (i.e., `formed` equals the number of unique characters in `t`), try to shrink the window from the `left`.
- Update the minimum window size if the current window is smaller than the previously found windows.
### Return the Result:
- Return the smallest window found. If no such window exists, return an empty string.

## Solution Code
```javascript
function minWindow(s, t) {
    if (s.length === 0 || t.length === 0) return "";

    // Dictionary which keeps a count of all the unique characters in t.
    const tCount = new Map();
    for (let char of t) {
        tCount.set(char, (tCount.get(char) || 0) + 1);
    }

    // Number of unique characters in t that need to be present in the desired window.
    const required = tCount.size;

    // Left and Right pointer
    let l = 0, r = 0;

    // Formed is used to keep track of how many unique characters in t are present in the current window
    let formed = 0;

    // Dictionary which keeps a count of all the unique characters in the current window.
    const windowCount = new Map();

    // Result: (window length, left, right)
    let ans = [-1, 0, 0];

    while (r < s.length) {
        // Add one character from the right to the window
        const char = s[r];
        windowCount.set(char, (windowCount.get(char) || 0) + 1);

        // If the frequency of the current character added equals to the desired count in t then increment the formed count by 1.
        if (tCount.has(char) && windowCount.get(char) === tCount.get(char)) {
            formed++;
        }

        // Try and contract the window till the point where it ceases to be 'desirable'.
        while (l <= r && formed === required) {
            char = s[l];
            // Save the smallest window until now.
            if (ans[0] === -1 || r - l + 1 < ans[0]) {
                ans[0] = r - l + 1;
                ans[1] = l;
                ans[2] = r;
            }

            // The character at the position pointed by the `left` pointer is no longer a part of the window.
            windowCount.set(char, windowCount.get(char) - 1);
            if (tCount.has(char) && windowCount.get(char) < tCount.get(char)) {
                formed--;
            }

            // Move the left pointer ahead, this would help to look for a new window.
            l++;
        }

        // Keep expanding the window once we are done contracting.
        r++;
    }

    return ans[0] === -1 ? "" : s.slice(ans[1], ans[2] + 1);
}

// Example usage
console.log(minWindow("ADOBECODEBANC", "ABC")); // Output: "BANC"
console.log(minWindow("a", "a")); // Output: "a"
console.log(minWindow("a", "aa")); // Output: ""
```

## Output
```css
s:  ADOBECODEBANC  t:  ABC  tCount:  Map(3) { 'A' => 1, 'B' => 1, 'C' => 1 }
required:  3
===========================================================================
char:  A  windowCount:  Map(1) { 'A' => 1 }  formed:  1
r:  1  ______________________________________
char:  D  windowCount:  Map(2) { 'A' => 1, 'D' => 1 }  formed:  1
r:  2  ______________________________________
char:  O  windowCount:  Map(3) { 'A' => 1, 'D' => 1, 'O' => 1 }  formed:  1
r:  3  ______________________________________
char:  B  windowCount:  Map(4) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 1 }  formed:  2
r:  4  ______________________________________
char:  E  windowCount:  Map(5) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 1, 'E' => 1 }  formed:  2
r:  5  ______________________________________
char:  C  windowCount:  Map(6) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 1, 'E' => 1, 'C' => 1 }  formed:  3
-------------- char = s[l]: A
ans[0]:  6  ans[1]:  0  ans[2]:  5
formed:  2
formed:  2  windowCount:  Map(6) { 'A' => 0, 'D' => 1, 'O' => 1, 'B' => 1, 'E' => 1, 'C' => 1 }  l:  1
r:  6  ______________________________________
char:  O  windowCount:  Map(6) { 'A' => 0, 'D' => 1, 'O' => 2, 'B' => 1, 'E' => 1, 'C' => 1 }  formed:  2
r:  7  ______________________________________
char:  D  windowCount:  Map(6) { 'A' => 0, 'D' => 2, 'O' => 2, 'B' => 1, 'E' => 1, 'C' => 1 }  formed:  2
r:  8  ______________________________________
char:  E  windowCount:  Map(6) { 'A' => 0, 'D' => 2, 'O' => 2, 'B' => 1, 'E' => 2, 'C' => 1 }  formed:  2
r:  9  ______________________________________
char:  B  windowCount:  Map(6) { 'A' => 0, 'D' => 2, 'O' => 2, 'B' => 2, 'E' => 2, 'C' => 1 }  formed:  2
r:  10  ______________________________________
char:  A  windowCount:  Map(6) { 'A' => 1, 'D' => 2, 'O' => 2, 'B' => 2, 'E' => 2, 'C' => 1 }  formed:  3
-------------- char = s[l]: D
formed:  3  windowCount:  Map(6) { 'A' => 1, 'D' => 1, 'O' => 2, 'B' => 2, 'E' => 2, 'C' => 1 }  l:  2
-------------- char = s[l]: O
formed:  3  windowCount:  Map(6) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 2, 'E' => 2, 'C' => 1 }  l:  3
-------------- char = s[l]: B
formed:  3  windowCount:  Map(6) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 1, 'E' => 2, 'C' => 1 }  l:  4
-------------- char = s[l]: E
formed:  3  windowCount:  Map(6) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 1, 'E' => 1, 'C' => 1 }  l:  5
-------------- char = s[l]: C
formed:  2
formed:  2  windowCount:  Map(6) { 'A' => 1, 'D' => 1, 'O' => 1, 'B' => 1, 'E' => 1, 'C' => 0 }  l:  6
r:  11  ______________________________________
char:  N  windowCount:  Map(7) {
  'A' => 1,
  'D' => 1,
  'O' => 1,
  'B' => 1,
  'E' => 1,
  'C' => 0,
  'N' => 1
}  formed:  2
r:  12  ______________________________________
char:  C  windowCount:  Map(7) {
  'A' => 1,
  'D' => 1,
  'O' => 1,
  'B' => 1,
  'E' => 1,
  'C' => 1,
  'N' => 1
}  formed:  3
-------------- char = s[l]: O
formed:  3  windowCount:  Map(7) {
  'A' => 1,
  'D' => 1,
  'O' => 0,
  'B' => 1,
  'E' => 1,
  'C' => 1,
  'N' => 1
}  l:  7
-------------- char = s[l]: D
formed:  3  windowCount:  Map(7) {
  'A' => 1,
  'D' => 0,
  'O' => 0,
  'B' => 1,
  'E' => 1,
  'C' => 1,
  'N' => 1
}  l:  8
-------------- char = s[l]: E
ans[0]:  5  ans[1]:  8  ans[2]:  12
formed:  3  windowCount:  Map(7) {
  'A' => 1,
  'D' => 0,
  'O' => 0,
  'B' => 1,
  'E' => 0,
  'C' => 1,
  'N' => 1
}  l:  9
-------------- char = s[l]: B
ans[0]:  4  ans[1]:  9  ans[2]:  12
formed:  2
formed:  2  windowCount:  Map(7) {
  'A' => 1,
  'D' => 0,
  'O' => 0,
  'B' => 0,
  'E' => 0,
  'C' => 1,
  'N' => 1
}  l:  10
r:  13  ______________________________________
Output:  BANC
```
## Explanation of the Code:
### Initialization:
- `tCount` stores the frequency of each character in `t`.
- `required` stores the number of unique characters in `t`.
- `windowCount` stores the frequency of characters in the current window.
- `formed` keeps track of how many unique characters from `t` are currently fully matched in the window.
- `ans` is an array that stores the length of the smallest window and its `left` and `right` bounds.
### Expanding the Window:
- The right pointer (`right`) expands the window by moving to the right and including new characters in windowCount.
- If the current character's frequency matches its frequency in `tCount`, increment `formed`.
### Contracting the Window:
- While the current window is valid (i.e., contains all characters from `t`), move the left pointer (`left`) to the right to try and find a smaller valid window.
- Update the smallest window found so far if the current window is smaller.
- If moving the left pointer removes a necessary character, decrement `formed`.
### Result:
- Return the smallest window found. If no valid window exists, return an empty string.

## Complexity Analysis
### Time Complexity:
The time complexity of this solution is `O(m+n)`, where `m` is the length of `s` and `n` is the length of `t`. This is because each character is processed at most twice (once by the `right` pointer and once by the `left` pointer).

### Space Complexity
The space complexity of the provided solution for finding the minimum window substring is `O(m+n)`, where `m` is the length of the string `s` and `n` is the length of the string `t`. Here's the detailed breakdown:
##### Space for Frequency Maps:
- `tCount`: This map stores the frequency of each character in `t`. In the worst case, it will have n entries if all characters in t are unique.
- `windowCount`: This map stores the frequency of each character in the current window of `s`. In the worst case, it will have m entries if all characters in the current window are unique.
##### Space for Result Storage:
- `ans`: This array stores three integers to keep track of the best window found so far. This contributes a constant space.
So, the total space complexity is `O(m+n)`.
