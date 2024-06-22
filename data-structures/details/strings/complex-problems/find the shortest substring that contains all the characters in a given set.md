# Find the Shortest Substring that contains all the characters in a given set

## Solution 1: Sliding Window Technique with Map
```javascript
function shortestSubstring(s, t) {
    if (t.length === 0) return "";

    const charCount = new Map();
    for (const char of t) {
        charCount.set(char, (charCount.get(char) || 0) + 1);
    }

    let required = charCount.size;
    let left = 0, right = 0;
    let formed = 0;
    const windowCounts = new Map();
    let ans = [-1, 0, 0];

    while (right < s.length) {
        const char = s[right];
        windowCounts.set(char, (windowCounts.get(char) || 0) + 1);

        if (charCount.has(char) && windowCounts.get(char) === charCount.get(char)) {
            formed++;
        }

        while (left <= right && formed === required) {
            const char = s[left];

            if (ans[0] === -1 || right - left + 1 < ans[0]) {
                ans = [right - left + 1, left, right];
            }

            windowCounts.set(char, windowCounts.get(char) - 1);
            if (charCount.has(char) && windowCounts.get(char) < charCount.get(char)) {
                formed--;
            }

            left++;
        }

        right++;
    }

    return ans[0] === -1 ? "" : s.slice(ans[1], ans[2] + 1);
}
```

<details><summary><h3>Explanation</h3></summary>
<p>
The function shortestSubstring finds the shortest substring in string s that contains all the characters of string t. It uses a sliding window approach with two pointers, left and right, to expand and contract the window to find the optimal substring.

### Initialization:

```javascript
if (t.length === 0) return "";
If t is an empty string, there is nothing to search for, so the function returns an empty string.
```

### Character Count Map:

```javascript
const charCount = new Map();
for (const char of t) {
    charCount.set(char, (charCount.get(char) || 0) + 1);
}
```
A map charCount is created to keep track of the frequency of each character in t.

### Variables Setup:

```javascript
let required = charCount.size;
let left = 0, right = 0;
let formed = 0;
const windowCounts = new Map();
let ans = [-1, 0, 0];
```
- required keeps track of the number of unique characters in t that need to be present in the current window.
- left and right are the pointers for the sliding window.
- formed counts how many unique characters in t are currently present in the required frequency in the window.
- windowCounts is a map to keep track of the frequency of characters in the current window.
- ans stores the length of the best (shortest) window found and the start and end indices of this window.

### Expand the Window:

```javascript
while (right < s.length) {
    const char = s[right];
    windowCounts.set(char, (windowCounts.get(char) || 0) + 1);

    if (charCount.has(char) && windowCounts.get(char) === charCount.get(char)) {
        formed++;
    }
```

- Iterate through s with the right pointer.
- Add the character at right to windowCounts.
- If the current character's frequency matches its required frequency, increment formed.

### Contract the Window:

```javascript
    while (left <= right && formed === required) {
        const char = s[left];

        if (ans[0] === -1 || right - left + 1 < ans[0]) {
            ans = [right - left + 1, left, right];
        }

        windowCounts.set(char, windowCounts.get(char) - 1);
        if (charCount.has(char) && windowCounts.get(char) < charCount.get(char)) {
            formed--;
        }

        left++;
    }

    right++;
```
- Once all required characters are formed in the window, try to minimize the window by moving the left pointer.
- Update ans if the current window is smaller than the previously found best window.
- Remove the character at left from windowCounts and decrement formed if its frequency falls below the required frequency.
- Move left to the right to continue minimizing the window.

### Return the Result:

```javascript
return ans[0] === -1 ? "" : s.slice(ans[1], ans[2] + 1);
```
- If no valid window was found, return an empty string.
- Otherwise, return the substring of s from ans[1] to ans[2] inclusive.

## Dry Run Example
Let's perform a dry run with the input s = "abdecfabgh" and t = "abc":

### Initialization:
```
charCount: { a: 1, b: 1, c: 1 }
required: 3
left: 0
right: 0
formed: 0
windowCounts: {}
ans: [-1, 0, 0]
```
Iteration 1 (right = 0):
```
char: 'a'
windowCounts: { a: 1 }
formed: 1 (because 'a' matches the frequency in charCount)
```
Iteration 2 (right = 1):
```
char: 'b'
windowCounts: { a: 1, b: 1 }
formed: 2 (because 'b' matches the frequency in charCount)
```
Iteration 3 (right = 2):
```
char: 'd'
windowCounts: { a: 1, b: 1, d: 1 }
formed: 2 (no change because 'd' is not in charCount)
```
Iteration 4 (right = 3):
```
char: 'e'
windowCounts: { a: 1, b: 1, d: 1, e: 1 }
formed: 2 (no change because 'e' is not in charCount)
```
Iteration 5 (right = 4):
```
char: 'c'
windowCounts: { a: 1, b: 1, d: 1, e: 1, c: 1 }
formed: 3 (because 'c' matches the frequency in charCount)
```
Start Contracting:
```
formed equals required, so try to minimize the window:
left = 0 to left = 1
char: 'a'
windowCounts: { a: 0, b: 1, d: 1, e: 1, c: 1 }
formed: 2 (because 'a' frequency is less than required)
ans: [5, 0, 4]
```
Iteration 6 (right = 5):
```
char: 'f'
windowCounts: { a: 0, b: 1, d: 1, e: 1, c: 1, f: 1 }
formed: 2 (no change because 'f' is not in charCount)
```
Iteration 7 (right = 6):
```
char: 'a'
windowCounts: { a: 1, b: 1, d: 1, e: 1, c: 1, f: 1 }
formed: 3 (because 'a' matches the frequency in charCount)
```
Start Contracting:
```
formed equals required, so try to minimize the window:
left = 1 to left = 2
char: 'b'
windowCounts: { a: 1, b: 0, d: 1, e: 1, c: 1, f: 1 }
formed: 2 (because 'b' frequency is less than required)
ans: [5, 0, 4] (no change because the new window size is not smaller)
```
Continue with the rest of the iterations:

- Follow the same process for the remaining characters 'b', 'g', 'h'.
- Each time, adjust the windowCounts and update formed accordingly.
- Contract the window when formed equals required and update ans if a smaller window is found.

### Final Output:

The shortest substring is s.slice(ans[1], ans[2] + 1), which is "abdec".
### Conclusion
The function correctly finds the shortest substring containing all characters of t using a sliding window approach. The time complexity of this algorithm is O(S + T), where S is the length of s and T is the length of t. This is efficient and ensures that we find the optimal solution.

</p>
</details>

## Time Complexity: O(S + T)

- Building the charCount map takes O(T) time.
- The outer while loop runs in O(S) time because right pointer traverses the entire string s.
- The inner while loop also runs in O(S) time in total because left pointer only moves forward.
- Both maps, charCount and windowCounts, require O(1) operations for insertion, update, and lookup because the maximum number of different characters is fixed (128 for ASCII).

## Solution 2: Optimized Sliding Window with Array
```javascript
function shortestSubstring(s, t) {
    if (t.length === 0) return "";

    const charCount = new Array(128).fill(0);
    for (const char of t) {
        charCount[char.charCodeAt(0)]++;
    }

    let required = t.length;
    let left = 0, right = 0;
    let minLength = Infinity, minLeft = 0;

    while (right < s.length) {
        if (charCount[s.charCodeAt(right)] > 0) {
            required--;
        }
        charCount[s.charCodeAt(right)]--;
        right++;

        while (required === 0) {
            if (right - left < minLength) {
                minLength = right - left;
                minLeft = left;
            }

            charCount[s.charCodeAt(left)]++;
            if (charCount[s.charCodeAt(left)] > 0) {
                required++;
            }
            left++;
        }
    }

    return minLength === Infinity ? "" : s.substring(minLeft, minLeft + minLength);
}
```

<details><summary><b>Explanation</b></summary>
<p>
The function shortestSubstring finds the shortest substring in string s that contains all the characters of string t. It uses a sliding window approach with two pointers, left and right, to expand and contract the window to find the optimal substring.

### Initialization:

```javascript
if (t.length === 0) return "";
If t is an empty string, there is nothing to search for, so the function returns an empty string.
```
### Character Count Array:

```javascript
const charCount = new Array(128).fill(0);
for (const char of t) {
    charCount[char.charCodeAt(0)]++;
}
```
- An array charCount of size 128 is created (to cover all ASCII characters) and initialized with zeros.
- The frequency of each character in t is stored in this array based on the ASCII value of the characters.
### Variables Setup:

```javascript
let required = t.length;
let left = 0, right = 0;
let minLength = Infinity, minLeft = 0;
```
- required keeps track of the total number of characters needed from t.
- left and right are the pointers for the sliding window.
- minLength keeps track of the length of the best (shortest) window found.
- minLeft stores the starting index of the best window.

### Expand the Window:

```javascript
while (right < s.length) {
    if (charCount[s.charCodeAt(right)] > 0) {
        required--;
    }
    charCount[s.charCodeAt(right)]--;
    right++;
```
- Iterate through s with the right pointer.
- If the current character is needed (i.e., charCount[s.charCodeAt(right)] > 0), decrement required.
- Decrement the count of the current character in charCount.
- Move the right pointer to the right to expand the window.

### Contract the Window:

```javascript
    while (required === 0) {
        if (right - left < minLength) {
            minLength = right - left;
            minLeft = left;
        }

        charCount[s.charCodeAt(left)]++;
        if (charCount[s.charCodeAt(left)] > 0) {
            required++;
        }
        left++;
    }
```
- Once all required characters are included in the window (required === 0), try to minimize the window by moving the left pointer.
- Update minLength and minLeft if the current window is smaller than the previously found best window.
- Increment the count of the character at left in charCount.
- If the current character at left is needed (i.e., charCount[s.charCodeAt(left)] > 0), increment required.
- Move the left pointer to the right to continue minimizing the window.

### Return the Result:

```javascript
return minLength === Infinity ? "" : s.substring(minLeft, minLeft + minLength);
```
- If no valid window was found, return an empty string.
- Otherwise, return the substring of s from minLeft to minLeft + minLength.

### Try the below code in any online editor 
```javascript
function findShortestSubstring(s, t) {
    if (t.length === 0) return "";

    const charCount = new Array(128).fill(0);
    for (const char of t) {
        console.log(char.charCodeAt(0))
        charCount[char.charCodeAt(0)]++;
    }
    console.log('initial ch count: ',charCount)
    let required = t.length;
    let left = 0, right = 0;
    let minLength = Infinity, minLeft = 0;

    while (right < s.length) {
        console.log('----------------------------------------------')
        console.log('right: ',right)
        if (charCount[s.charCodeAt(right)] > 0) {
            required--;
             console.log('charCount[s.charCodeAt(right)] : ',charCount[s.charCodeAt(right)], "required : ",required )
        }
        charCount[s.charCodeAt(right)]--;
        right++;
        console.log(charCount)

        while (required === 0) {
            console.log('****************************')
            console.log(left, right, minLength)
            
            
            if (right - left < minLength) {
                minLength = right - left;
                minLeft = left;
                console.log('minLength: ', minLength, 'minLeft: ',minLeft)
            }
            console.log(charCount[s.charCodeAt(left)])
            charCount[s.charCodeAt(left)]++;
            console.log(charCount[s.charCodeAt(left)])
            if (charCount[s.charCodeAt(left)] > 0) {
                required++;
                console.log(charCount)
                console.log('required : ',required)
            }
             console.log('required : ',required);
             
            left++;
        }
    }
    console.log('minLength: ', minLength, 'minLeft: ',minLeft)
    return minLength === Infinity ? "" : s.substring(minLeft, minLeft + minLength);
}


console.log(findShortestSubstring("abdecfabgh", "abc")); // Output: "cfab"
```
#### Output
```
97
98
99
initial ch count:  [
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 1, 1,
  ... 28 more items
]
----------------------------------------------
right:  0
charCount[s.charCodeAt(right)] :  1 required :  2
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 1,
  ... 28 more items
]
----------------------------------------------
right:  1
charCount[s.charCodeAt(right)] :  1 required :  1
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1,
  ... 28 more items
]
----------------------------------------------
right:  2
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1,
  ... 28 more items
]
----------------------------------------------
right:  3
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1,
  ... 28 more items
]
----------------------------------------------
right:  4
charCount[s.charCodeAt(right)] :  1 required :  0
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0,
  ... 28 more items
]
****************************
0 5 Infinity
minLength:  5 minLeft:  0
0
1
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0,
  ... 28 more items
]
required :  1
required :  1
----------------------------------------------
right:  5
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 1, 0, 0,
  ... 28 more items
]
----------------------------------------------
right:  6
charCount[s.charCodeAt(right)] :  1 required :  0
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0,
  ... 28 more items
]
****************************
1 7 5
0
1
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 1, 0,
  ... 28 more items
]
required :  1
required :  1
----------------------------------------------
right:  7
charCount[s.charCodeAt(right)] :  1 required :  0
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0,
  ... 28 more items
]
****************************
2 8 5
-1
0
required :  0
****************************
3 8 5
-1
0
required :  0
****************************
4 8 5
minLength:  4 minLeft:  4
0
1
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1,
  ... 28 more items
]
required :  1
required :  1
----------------------------------------------
right:  8
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1,
  ... 28 more items
]
----------------------------------------------
right:  9
[
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
  0, 0, 0, 1,
  ... 28 more items
]
minLength:  4 minLeft:  4
cfab
```

## Dry Run Example
Let's perform a dry run with the input s = "abdecfabgh" and t = "abc":

Initialization:
```
charCount: [0, 0, 0, ..., 1, 1, 1, ..., 0] (ASCII values of 'a', 'b', 'c' incremented)
required: 3
left: 0
right: 0
minLength: Infinity
minLeft: 0
```
Iteration 1 (right = 0):
```
char: 'a'
charCount: [0, 0, 0, ..., 0, 1, 1, ..., 0]
required: 2 (because 'a' was needed)
right: 1
```
Iteration 2 (right = 1):
```
char: 'b'
charCount: [0, 0, 0, ..., 0, 0, 1, ..., 0]
required: 1 (because 'b' was needed)
right: 2
```
Iteration 3 (right = 2):
```
char: 'd'
charCount: [0, 0, 0, ..., 0, 0, 1, ..., 0]
required: 1 (no change because 'd' is not in t)
right: 3
```
Iteration 4 (right = 3):
```
char: 'e'
charCount: [0, 0, 0, ..., 0, 0, 1, ..., 0]
required: 1 (no change because 'e' is not in t)
right: 4
```
Iteration 5 (right = 4):
```
char: 'c'
charCount: [0, 0, 0, ..., 0, 0, 0, ..., 0]
required: 0 (because 'c' was needed)
right: 5
```
Start Contracting:
```
required equals 0, so try to minimize the window:
left = 0 to left = 1
char: 'a'
charCount: [0, 0, 0, ..., 1, 0, 0, ..., 0]
required: 1 (because 'a' was needed again)
minLength: 5
minLeft: 0
```
Iteration 6 (right = 5):
```
char: 'f'
charCount: [0, 0, 0, ..., 1, 0, 0, ..., 0]
required: 1 (no change because 'f' is not in t)
right: 6
```
Iteration 7 (right = 6):
```
char: 'a'
charCount: [0, 0, 0, ..., 0, 0, 0, ..., 0]
required: 0 (because 'a' was needed)
right: 7
```
Start Contracting:
```
required equals 0, so try to minimize the window:
left = 1 to left = 2
char: 'b'
charCount: [0, 0, 0, ..., 0, 1, 0, ..., 0]
required: 1 (because 'b' was needed again)
minLength: 5 (no change because the new window size is not smaller)
```
### Continue with the rest of the iterations:

- Follow the same process for the remaining characters 'b', 'g', 'h'.
- Each time, adjust the charCount and update required accordingly.
- Contract the window when required equals 0 and update minLength if a smaller window is found.

### Final Output:
- The shortest substring is s.substring(minLeft, minLeft + minLength), which is "abdec".

### Conclusion
The function correctly finds the shortest substring containing all characters of t using a sliding window approach. The time complexity of this algorithm is O(S + T), where S is the length of s and T is the length of t. This is efficient and ensures that we find the optimal solution.

</p>
</details>

## Time Complexity: O(S + T)

- Building the charCount array takes O(T) time.
- The outer while loop runs in O(S) time because right pointer traverses the entire string s.
- The inner while loop also runs in O(S) time in total because left pointer only moves forward.
- Array operations (access and update) take O(1) time.

## Solution 3: Using Frequency Maps and Counters
```javascript
function shortestSubstring(s, t) {
    if (s.length === 0 || t.length === 0) return "";

    const required = new Map();
    for (const char of t) {
        required.set(char, (required.get(char) || 0) + 1);
    }

    let left = 0, right = 0, formed = 0;
    const windowCounts = new Map();
    const result = { length: Infinity, start: 0, end: 0 };

    while (right < s.length) {
        const char = s[right];
        windowCounts.set(char, (windowCounts.get(char) || 0) + 1);

        if (required.has(char) && windowCounts.get(char) === required.get(char)) {
            formed++;
        }

        while (left <= right && formed === required.size) {
            const char = s[left];

            if (right - left + 1 < result.length) {
                result.length = right - left + 1;
                result.start = left;
                result.end = right;
            }

            windowCounts.set(char, windowCounts.get(char) - 1);
            if (required.has(char) && windowCounts.get(char) < required.get(char)) {
                formed--;
            }

            left++;
        }

        right++;
    }

    return result.length === Infinity ? "" : s.substring(result.start, result.end + 1);
}
```

<details><summary><b>Explanation</b></summary>
<p>


</p>
</details>

## Time Complexity: O(S + T)

- Building the required map takes O(T) time.
- The outer while loop runs in O(S) time because right pointer traverses the entire string s.
- The inner while loop also runs in O(S) time in total because left pointer only moves forward.
- Both maps, required and windowCounts, require O(1) operations for insertion, update, and lookup because the maximum number of different characters is fixed (128 for ASCII).

In summary, all three solutions have a time complexity of `O(S + T)`, where S is the length of the string s and T is the length of the string t.
