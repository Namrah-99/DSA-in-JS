# Find the longest palindromic substring using Manacher's Algorithm

The algorithm preprocesses the input string by adding `#` between each character, then iterates through the processed string to find the longest palindromic substring using Manacher's Algorithm.

## Step by Step Code explanation

### Initialization:
- `processedString`: A new string created by adding `#` between each character of the input string `s`.
- `center`: The center of the current longest palindrome.
- `right`: The right boundary of the current longest palindrome.
- palindromeLengths: An array to store the length of palindromes centered at each index of `processedString`.
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

```javascript
function longestPalindrome(s) {
    if (!s || s.length === 0) return "";
    
    // Preprocess the string
    let processedString = "#";
    for (let i = 0; i < s.length; i++) {
        processedString += s[i] + "#";
    }
    console.log(processedString)
    console.log(processedString.length)
    let center = 0, right = 0;
    let palindromeLengths = new Array(processedString.length).fill(0);
    let maxCenter = 0, maxLength = 0;
    console.log(palindromeLengths)
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
console.log(longestPalindrome("cbbd")); // Output: "bb"
```


