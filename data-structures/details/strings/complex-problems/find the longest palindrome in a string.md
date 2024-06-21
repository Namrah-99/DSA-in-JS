# Find the longest palindromic substring using Manacher's Algorithm

The algorithm preprocesses the input string by adding `#` between each character, then iterates through the processed string to find the longest palindromic substring using Manacher's Algorithm.

### How Algorithm Works

1. Preprocess the string:
    - This step transforms the original string `s` into a new string processedString by adding special characters (`#`) between each character and at the boundaries. This helps to handle both odd and even length palindromes uniformly.
    - For example, if `s` is `"babad"`, the `processedString` will be "#b#a#b#a#d#".

2. Initialization:

    - `center` and `right` are initialized to 0. These will keep track of the center and right edge of the current longest palindrome.
    - `palindromeLengths` is an array initialized with zeros. It will store the length of the palindrome centered at each position in processedString.
    - `maxCenter` and `maxLength` are used to track the center and length of the longest palindrome found.

3. Main loop through the `processedString`:

    - Calculate the mirror position: For each character `i` in `processedString`, calculate its mirror position `mirror` with respect to the current center.
    - Use previously computed palindrome lengths: If `i` is within the right boundary of the current longest palindrome, use the minimum of the remaining length to the right edge and the palindrome length at the mirror position to initialize `palindromeLengths[i]`.
    - Expand around center: Expand around `i` to find the maximum length of the palindrome centered at `i`. This is done by comparing characters at positions `expandLeft` and `expandRight` and expanding as long as they are equal.
    - Update the center and right boundary: If the expanded palindrome at `i` goes beyond the current right boundary, update `center` and `right` to reflect the new palindrome's center and right edge.
    - Track the longest palindrome: Update `maxCenter` and `maxLength` if the palindrome centered at `i` is longer than the previously found longest palindrome.

4. Calculate the start index of the longest palindrome in the original string:
    - Convert the center and length of the longest palindrome found in processedString back to the corresponding substring in the original string `s`.

5. Return the longest palindromic substring:
    - Extract and return the longest palindromic substring from the original string `s` using the computed start index and length.

## Step by Step Code explanation

### Initialization:
- `processedString`: A new string created by adding `#` between each character of the input string `s`.
- `center`: The center of the current longest palindrome.
- `right`: The right boundary of the current longest palindrome.
- `palindromeLengths`: An array to store the length of palindromes centered at each index of `processedString`.
- `maxCenter`: The center of the longest palindrome found so far.
- `maxLength`: The length of the longest palindrome found so far.

### Preprocessing:
- `processedString` is created by inserting `#` between each character of `s`.

### Main Loop:
- For each character in `processedString`:
    - Calculate the mirror position `mirror` of the current index `i` with respect to the center `center`.
    - If `i` is within the current palindrome boundaries (`right`), update the palindrome length at `i` based on the minimum of the remaining length to `right` and the palindrome length at `mirror`.
    - Expand around `i` to check for palindromes by incrementing `expandLeft` and decrementing `expandRight` while the characters at these positions are equal.
    - Update the current palindrome length at `i`.
    - If the expanded palindrome at `i` reaches beyond `right`, update `center` and `right`.
    - If the current palindrome length at `i` is greater than maxLength, update `maxLength` and `maxCenter.

### Result Calculation:
- Calculate the starting index `start` of the longest palindrome substring in the original string `s`.
- Return the substring of `s` starting from `start` with a length of `maxLength`.

### Example Usage:
- Calling `longestPalindrome("babad")` returns `"bab"` or `"aba"` as these are the longest palindromic substrings in the input string.
- Calling `longestPalindrome("cbbd")` returns `"bb"` as this is the longest palindromic substring in the input string.

```javascript
function longestPalindrome(s) {
    if (!s || s.length === 0) return "";
    
    // Preprocess the string
    let processedString = "#";
    for (let i = 0; i < s.length; i++) {
        processedString += s[i] + "#";
    }
    
    let center = 0, right = 0;
    let palindromeLengths = new Array(processedString.length).fill(0);
    let maxCenter = 0, maxLength = 0;
    
    for (let i = 0; i < processedString.length; i++) {
        let mirror = 2 * center - i;
        
        if (i < right) {
            palindromeLengths[i] = Math.min(right - i, palindromeLengths[mirror]);
        }
        
        let expandLeft = i - palindromeLengths[i] - 1;
        let expandRight = i + palindromeLengths[i] + 1;
        
        while (expandLeft >= 0 && expandRight < processedString.length && 
               processedString[expandLeft] === processedString[expandRight]) {
            palindromeLengths[i]++;
            expandLeft--;
            expandRight++;
        }
        
        if (i + palindromeLengths[i] > right) {
            center = i;
            right = i + palindromeLengths[i];
        }
        
        if (palindromeLengths[i] > maxLength) {
            maxLength = palindromeLengths[i];
            maxCenter = i;
        }
    }
    
    let start = Math.floor((maxCenter - maxLength) / 2);
    return s.substr(start, maxLength);
}

// Example usage
console.log(longestPalindrome("babad")); // Output: "aba" or "bab"
console.log(longestPalindrome("cbbd")); // Output: "bb"
```

Let's break down the concept of the mirror position and the overall algorithm in simpler terms:

### Mirror Position Calculation (mirror):

- The mirror position of an index i with respect to a center center is the index on the other side of the center that mirrors the position of i.
- For example, if center = 3 and i = 5, then mirror = 2 * center - i = 2 * 3 - 5 = 1.

### Algorithm Steps:

- Initialization: Initialize center and right to 0, and create an array palindromeLengths to store the lengths of palindromes centered at each index of the processed string.
- Main Loop: For each character in the processed string:
- Mirror Check: Calculate the mirror position mirror of the current index i with respect to the current center center.
- Palindromic Boundary Check: If i is within the current palindrome boundaries (right), update the palindrome length at i based on the minimum of the remaining length to right and the palindrome length at mirror.
- Palindrome Expansion: Expand around i to check for palindromes by incrementing expandLeft and decrementing expandRight while the characters at these positions are equal.
- Update Palindrome Length: Update the current palindrome length at i.
- Update Center and Right: If the expanded palindrome at i reaches beyond right, update center and right.
- Update Max Length: If the current palindrome length at i is greater than maxLength, update maxLength and maxCenter.

### Result Calculation:

- Calculate the starting index start of the longest palindrome substring in the original string s using maxCenter and maxLength.
- Return the substring of s starting from start with a length of maxLength.

### Example Usage:

- For the input string "babad", the algorithm would find "bab" or "aba" as the longest palindromic substring.
- For the input string "cbbd", the algorithm would find "bb" as the longest palindromic substring.

In essence, the algorithm uses the concept of mirroring to efficiently expand around potential palindrome centers and keep track of the longest palindrome found so far.
<!--
```javascript
function longestPalindrome(s) {
    if (!s || s.length === 0) return "";
    
    // Preprocess the string
    let processedString = "#";
    for (let i = 0; i < s.length; i++) {
        processedString += s[i] + "#";
    }
    console.log('processedString: ', processedString, "processedString.length: ",processedString.length)
    let center = 0, right = 0;
    let palindromeLengths = new Array(processedString.length).fill(0);
    let maxCenter = 0, maxLength = 0;
    console.log('palindromeLengths: ',palindromeLengths)
    for (let i = 0; i < processedString.length; i++) {
        
        let mirror = 2 * center - i;
        console.log("i : ",i,", center: ",center,", mirror: ",mirror)
        console.log("i < right: ",i < right)
        if (i < right) {
            console.log('palindromeLengths[i] ',palindromeLengths[i])
            palindromeLengths[i] = Math.min(right - i, palindromeLengths[mirror]);
        }
        console.log('i: ',i,' palindromeLengths[i]:  ', palindromeLengths[i] )
      
        let expandLeft = i - palindromeLengths[i] - 1;
        let expandRight = i + palindromeLengths[i] + 1;
          console.log('expandLeft : ',expandLeft,', processedString[expandLeft] : ',processedString[expandLeft])
        console.log('expandRight : ',expandRight,', processedString[expandRight] : ',processedString[expandRight])
   
        while (expandLeft >= 0 && expandRight < processedString.length && 
               processedString[expandLeft] === processedString[expandRight]) {
            palindromeLengths[i]++;
            console.log('palindromeLengths : ',palindromeLengths)
            expandLeft--;
            expandRight++;
            console.log('expandLeft : ',expandLeft,', processedString[expandLeft] : ',processedString[expandLeft])
        console.log('expandRight : ',expandRight,', processedString[expandRight] : ',processedString[expandRight])
        }
        console.log('palindromeLengths[i] : ', palindromeLengths[i],', right', right,', maxLength: ', maxLength)
        if (i + palindromeLengths[i] > right) {
            center = i;
            right = i + palindromeLengths[i];
            console.log('center : ',center, ', right : ',right)
      
        }
        if (palindromeLengths[i] > maxLength) {
            maxLength = palindromeLengths[i];
            maxCenter = i;
             console.log('maxLength: ', maxLength,', maxCenter: ', maxCenter)
           
        }
        
        console.log("---------------------------------------------------------------------")
    }
    console.log("maxCenter : ",maxCenter,"maxLength : ",maxLength )
    let start = Math.floor((maxCenter - maxLength) / 2);
    console.log('start : ', start)
    return s.substr(start, maxLength);
}

// Example usage
console.log(longestPalindrome("babad")); // Output: "aba" or "bab"
//console.log(longestPalindrome("cbbd")); // Output: "bb"
```-->
### Dry Run the provided code step by step
```
processedString:  #b#a#b#a#d# processedString.length:  11
palindromeLengths:  [
  0, 0, 0, 0, 0,
  0, 0, 0, 0, 0,
  0
]
i :  0 , center:  0 , mirror:  0
i < right:  false
i:  0  palindromeLengths[i]:   0
expandLeft :  -1 , processedString[expandLeft] :  undefined
expandRight :  1 , processedString[expandRight] :  b
palindromeLengths[i] :  0 , right 0 , maxLength:  0
---------------------------------------------------------------------
i :  1 , center:  0 , mirror:  -1
i < right:  false
i:  1  palindromeLengths[i]:   0
expandLeft :  0 , processedString[expandLeft] :  #
expandRight :  2 , processedString[expandRight] :  #
palindromeLengths :  [
  0, 1, 0, 0, 0,
  0, 0, 0, 0, 0,
  0
]
expandLeft :  -1 , processedString[expandLeft] :  undefined
expandRight :  3 , processedString[expandRight] :  a
palindromeLengths[i] :  1 , right 0 , maxLength:  0
center :  1 , right :  2
maxLength:  1 , maxCenter:  1
---------------------------------------------------------------------
i :  2 , center:  1 , mirror:  0
i < right:  false
i:  2  palindromeLengths[i]:   0
expandLeft :  1 , processedString[expandLeft] :  b
expandRight :  3 , processedString[expandRight] :  a
palindromeLengths[i] :  0 , right 2 , maxLength:  1
---------------------------------------------------------------------
i :  3 , center:  1 , mirror:  -1
i < right:  false
i:  3  palindromeLengths[i]:   0
expandLeft :  2 , processedString[expandLeft] :  #
expandRight :  4 , processedString[expandRight] :  #
palindromeLengths :  [
  0, 1, 0, 1, 0,
  0, 0, 0, 0, 0,
  0
]
expandLeft :  1 , processedString[expandLeft] :  b
expandRight :  5 , processedString[expandRight] :  b
palindromeLengths :  [
  0, 1, 0, 2, 0,
  0, 0, 0, 0, 0,
  0
]
expandLeft :  0 , processedString[expandLeft] :  #
expandRight :  6 , processedString[expandRight] :  #
palindromeLengths :  [
  0, 1, 0, 3, 0,
  0, 0, 0, 0, 0,
  0
]
expandLeft :  -1 , processedString[expandLeft] :  undefined
expandRight :  7 , processedString[expandRight] :  a
palindromeLengths[i] :  3 , right 2 , maxLength:  1
center :  3 , right :  6
maxLength:  3 , maxCenter:  3
---------------------------------------------------------------------
i :  4 , center:  3 , mirror:  2
i < right:  true
palindromeLengths[i]  0
i:  4  palindromeLengths[i]:   0
expandLeft :  3 , processedString[expandLeft] :  a
expandRight :  5 , processedString[expandRight] :  b
palindromeLengths[i] :  0 , right 6 , maxLength:  3
---------------------------------------------------------------------
i :  5 , center:  3 , mirror:  1
i < right:  true
palindromeLengths[i]  0
i:  5  palindromeLengths[i]:   1
expandLeft :  3 , processedString[expandLeft] :  a
expandRight :  7 , processedString[expandRight] :  a
palindromeLengths :  [
  0, 1, 0, 3, 0,
  2, 0, 0, 0, 0,
  0
]
expandLeft :  2 , processedString[expandLeft] :  #
expandRight :  8 , processedString[expandRight] :  #
palindromeLengths :  [
  0, 1, 0, 3, 0,
  3, 0, 0, 0, 0,
  0
]
expandLeft :  1 , processedString[expandLeft] :  b
expandRight :  9 , processedString[expandRight] :  d
palindromeLengths[i] :  3 , right 6 , maxLength:  3
center :  5 , right :  8
---------------------------------------------------------------------
i :  6 , center:  5 , mirror:  4
i < right:  true
palindromeLengths[i]  0
i:  6  palindromeLengths[i]:   0
expandLeft :  5 , processedString[expandLeft] :  b
expandRight :  7 , processedString[expandRight] :  a
palindromeLengths[i] :  0 , right 8 , maxLength:  3
---------------------------------------------------------------------
i :  7 , center:  5 , mirror:  3
i < right:  true
palindromeLengths[i]  0
i:  7  palindromeLengths[i]:   1
expandLeft :  5 , processedString[expandLeft] :  b
expandRight :  9 , processedString[expandRight] :  d
palindromeLengths[i] :  1 , right 8 , maxLength:  3
---------------------------------------------------------------------
i :  8 , center:  5 , mirror:  2
i < right:  false
i:  8  palindromeLengths[i]:   0
expandLeft :  7 , processedString[expandLeft] :  a
expandRight :  9 , processedString[expandRight] :  d
palindromeLengths[i] :  0 , right 8 , maxLength:  3
---------------------------------------------------------------------
i :  9 , center:  5 , mirror:  1
i < right:  false
i:  9  palindromeLengths[i]:   0
expandLeft :  8 , processedString[expandLeft] :  #
expandRight :  10 , processedString[expandRight] :  #
palindromeLengths :  [
  0, 1, 0, 3, 0,
  3, 0, 1, 0, 1,
  0
]
expandLeft :  7 , processedString[expandLeft] :  a
expandRight :  11 , processedString[expandRight] :  undefined
palindromeLengths[i] :  1 , right 8 , maxLength:  3
center :  9 , right :  10
---------------------------------------------------------------------
i :  10 , center:  9 , mirror:  8
i < right:  false
i:  10  palindromeLengths[i]:   0
expandLeft :  9 , processedString[expandLeft] :  d
expandRight :  11 , processedString[expandRight] :  undefined
palindromeLengths[i] :  0 , right 10 , maxLength:  3
---------------------------------------------------------------------
maxCenter :  3 maxLength :  3
start :  0
bab
```


<details><summary><b>Another Good Example</b></summary>
<p>
Let's break down each step with an easy-to-understand example. We'll use the string "abac" for demonstration.

## Step-by-Step Explanation

##### Calculate the mirror position:

- For each character i in processedString, calculate its mirror position mirror with respect to the current center.
- Example: Let's say center = 3 and i = 5. The mirror of i is calculated as mirror = 2 * center - i = 2 * 3 - 5 = 1.

### Use previously computed palindrome lengths:

- If i is within the right boundary right of the current longest palindrome, use the minimum of the remaining length to the right edge and the palindrome length at the mirror position to initialize palindromeLengths[i].
- Example: If right = 6 and i = 5, i is within right. Let’s say palindromeLengths[mirror] = 1 and right - i = 1. We take the minimum of these two, so palindromeLengths[i] = 1.

### Expand around center:

- Expand around i to find the maximum length of the palindrome centered at i. This is done by comparing characters at positions expandLeft and expandRight and expanding as long as they are equal.
- Example: If i = 5, expandLeft = i - palindromeLengths[i] - 1 = 5 - 1 - 1 = 3 and expandRight = i + palindromeLengths[i] + 1 = 5 + 1 + 1 = 7. We check if processedString[3] equals processedString[7]. If they are equal, we increase palindromeLengths[i].

### Update the center and right boundary:

- If the expanded palindrome at i goes beyond the current right boundary, update center and right to reflect the new palindrome's center and right edge.
- Example: If i + palindromeLengths[i] = 5 + 2 = 7 is greater than right = 6, we update center = 5 and right = 7.

### Track the longest palindrome:

- Update maxCenter and maxLength if the palindrome centered at i is longer than the previously found longest palindrome.
- Example: If palindromeLengths[i] = 2 and maxLength = 1, we update maxLength = 2 and maxCenter = 5.

## Full Example: "abac"

### Preprocess the string:
- Original: "abac"
- Processed: "#a#b#a#c#"

### Initialize variables:
- center = 0, right = 0
- palindromeLengths = [0, 0, 0, 0, 0, 0, 0, 0, 0]
- maxCenter = 0, maxLength = 0

### Iteration through processedString:

i = 0:

- mirror = 2 * 0 - 0 = 0
- No expansion since i < right is false.
- center and right remain unchanged.

i = 1:

- mirror = 2 * 0 - 1 = -1
- No expansion since mirror < 0.
- Expand around i finds palindrome "a" (length 1).
- Update center = 1, right = 2.
- Update maxLength = 1, maxCenter = 1.

i = 2:

- mirror = 2 * 1 - 2 = 0
- Use palindrome length from mirror, palindromeLengths[2] = min(0, 0) = 0.
- Expand around i finds palindrome "aba" (length 3).
- Update center = 2, right = 4.
- Update maxLength = 3, maxCenter = 2.

i = 3:

- mirror = 2 * 2 - 3 = 1
- Use palindrome length from mirror, palindromeLengths[3] = min(1, 1) = 1.
- Expand around i does not find a longer palindrome.
- No update to center and right.

i = 4:

- mirror = 2 * 2 - 4 = 0
- Use palindrome length from mirror, palindromeLengths[4] = min(0, 0) = 0.
- Expand around i finds palindrome "aca" (length 1).
- Update center = 4, right = 5.
- No update to maxLength.

i = 5:

- mirror = 2 * 4 - 5 = 3
- Use palindrome length from mirror, palindromeLengths[5] = min(1, 1) = 1.
- Expand around i finds no longer palindrome.
- No update to center and right.

i = 6:

- mirror = 2 * 4 - 6 = 2
- Use palindrome length from mirror, palindromeLengths[6] = min(1, 0) = 0.
- No expansion since characters do not match.
- No update to center and right.

i = 7:

- mirror = 2 * 4 - 7 = 1
- Use palindrome length from mirror, palindromeLengths[7] = min(1, 1) = 1.
- Expand around i finds palindrome "c" (length 1).
- No update to maxLength.

### Final Calculation:
- Longest palindrome is centered at maxCenter = 2 with maxLength = 3.
- Convert back to original string indices: (2 - 3) / 2 = -0.5 (floor to 0) and length 3 gives "aba".

### Conclusion:
The algorithm efficiently finds the longest palindromic substring using a linear time complexity approach by expanding around possible centers and utilizing previously computed palindrome lengths to minimize redundant calculations.
</p>
</details>
