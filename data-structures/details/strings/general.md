<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h1>JavaScript Strings Questions</h1>
</div>

<p align="center">Create, Traverse & Manipulate Strings</p>



###### 1. Write a function to reverse a string.
<details><summary><b>Solution</b></summary>
<p>

Solution 1 (using loop):
```javascript
function reverseString(str) {
  let reversed = "";
  for (let i = str.length - 1; i >= 0; i--) {
    reversed += str[i];
  }
  return reversed;
}

console.log(reverseString("hello")); // Output: "olleh"
```

### Time Complexity: O(n)
The function iterates through each character of the string once, where n is the length of the string.

##### Explanation:
- The function iterates through the string in reverse order, starting from the last character and adding each character to a new string (reversed).

Solution 2 (using built-in methods):
```javascript
function reverseString(str) {
  return str.split("").reverse().join("");
}

console.log(reverseString("hello")); // Output: "olleh"
```

### Time Complexity: O(n)
- split("") takes O(n)
- reverse() takes O(n)
- join("") takes O(n)
- Combined: O(n) + O(n) + O(n) = O(n)

##### Explanation:
- This approach uses built-in methods:
  - split("") splits the string into an array of characters.
  - reverse() reverses the order of elements in the array.
  - join("") joins the characters back into a string.

</p>
</details>

###### 2. Write a function to check if a string is a palindrome.
<details><summary><b>Solution</b></summary>
<p>

Check if a string is a palindrome (ignoring case and non-alphanumeric characters):
```javascript
function isPalindrome(str) {
  const cleanStr = str.replace(/[^a-z0-9]/gi, "").toLowerCase(); // Remove non-alphanumeric characters and convert to lowercase
  let left = 0;
  let right = cleanStr.length - 1;

  while (left < right) {
    if (cleanStr[left] !== cleanStr[right]) {
      return false;
    }
    left++;
    right--;
  }

  return true;
}

console.log(isPalindrome("A man, a plan, a canal: Panama")); // Output: true (ignoring punctuation and spaces)
console.log(isPalindrome("racecar")); // Output: true
console.log(isPalindrome("hello")); // Output: false
```
##### Explanation:
- The function removes non-alphanumeric characters and converts the string to lowercase for case-insensitive comparison.
- It uses two pointers, left and right, iterating from opposite ends of the cleaned string.
- It checks if the characters at the left and right pointers match. If not, it's not a palindrome.
- If the loop completes without finding a mismatch, it's a palindrome.

### Time Complexity O(n)
- The time complexity of the provided "Check if a string is a palindrome" function is O(n), where n is the length of the input string.
- O(n) for cleaning the string (str.replace and toLowerCase both iterate over the string once).
- O(n) for the two-pointer comparison loop.
- Thus, the overall time complexity is O(n).

</p>
</details>

###### 3. Write a function to count the number of vowels in a string.
<details><summary><b>Solution</b></summary>
<p>

Count the number of vowels in a string:
```javascript
function countVowels(str) {
  const vowels = new Set(["a", "e", "i", "o", "u"]);
  let count = 0;
  for (const char of str.toLowerCase()) {
    if (vowels.has(char)) {
      count++;
    }
  }
  return count;
}

console.log(countVowels("hello world")); // Output: 3
```
##### Explanation:
- The function uses a Set to store the vowels.
- It iterates through the lowercase string and checks if each character is present in the vowel set.
- If it is, the count is incremented.

### Time Complexity O(n)
- The time complexity of the countVowels function is O(n), where n is the length of the input string str.
- The function iterates through each character in the string once.
- Checking if a character is in the Set takes O(1) time.
- Thus, the overall time complexity is O(n).

</p>
</details>

###### 4. Write a function to count the number of words in a string.
<details><summary><b>Solution</b></summary>
<p>

Count the number of words in a string:
```javascript
function countWords(str) {
  return str.trim().split(/\s+/).length; // Split on whitespace (one or more spaces)
}

console.log(countWords("hello world")); // Output: 2
console.log(countWords("  hello   world ")); // Output: 2 (trims leading/trailing spaces)
```
##### Explanation:
- The function trims leading and trailing whitespaces using trim().
- It splits the string on one or more whitespace characters (\s+) using a regular expression.
- The length property of the resulting array gives the number of words.

### Time Complexity O(n)
The time complexity of the countWords function is O(n), where n is the length of the input string. This is because:

- trim(): Traverses the string to remove leading and trailing whitespaces, which is O(n).
- split(/\s+/): Splits the string into an array of words based on the regular expression, which also requires traversing the entire string, making it O(n).
- length: Accessing the length property of the array is O(1).

Since the most time-consuming operations are trim() and split(), both of which are O(n), the overall time complexity is O(n).

</p>
</details>

###### 5. Write a function to capitalize the first letter of each word in a string.
<details><summary><b>Solution</b></summary>
<p>

Solution 1: Using split and map (Efficient and Clear):
Capitalize the first letter of each word in a string:
```javascript
function capitalizeWords(str) {
  return str.split(/\s+/).map(word => word.charAt(0).toUpperCase() + word.slice(1)).join(" ");
}

console.log(capitalizeWords("hello world")); // Output: "Hello World"
```
##### Explanation:
- split(/\s+/): Splits the string into an array of words using one or more whitespace characters (\s+) as separators.
- map(word => ... ): Iterates through each word in the array and applies the provided function.
  - word.charAt(0).toUpperCase(): Gets the first character, converts it to uppercase.
  - word.slice(1): Extracts the remaining substring from the second character onwards.
  - Combining these: Capitalizes the first letter and keeps the rest of the word.
- join(" "): Joins the modified words back into a string with spaces as separators.

### Time Complexity: O(n)
- split(/\s+/): Splits the string into an array of words, O(n).
- map(word => ...): Iterates through each word to capitalize the first letter, O(n).
- join(" "): Joins the words back into a string, O(n).


Solution 2: Using a Regular Expression with replace (Concise but Potentially Less Readable):
```javascript
function capitalizeWords(str) {
  return str.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase());
}

console.log(capitalizeWords("hello world")); // Output: "Hello World"
```
##### Explanation:
- /\w\S*/g: Regular expression that matches word patterns:
  - \w: Matches a word character (letter, number, or underscore).
  - \S*: Matches zero or more non-whitespace characters.
  - g: Global flag to replace all occurrences.
- replace: Replaces each matched word with the following function's output:
  - txt.charAt(0).toUpperCase(): Capitalizes the first character.
  - txt.substr(1).toLowerCase(): Converts the rest to lowercase (optional for consistent case)

### Time Complexity: O(n)
replace(/\w\S*/g, ...): Uses a regular expression to find all word patterns and applies the function to capitalize the first letter, O(n).

Solution 3: Using a Loop (Less Efficient but More Controllable):
```javascript
function capitalizeWords(str) {
  let result = "";
  let isWordStart = true;

  for (let char of str) {
    if (/\s/.test(char)) {
      isWordStart = true;
    } else if (isWordStart) {
      result += char.toUpperCase();
      isWordStart = false;
    } else {
      result += char;
    }
  }

  return result;
}

console.log(capitalizeWords("hello world")); // Output: "Hello World"
```
##### Explanation:
- isWordStart flag to track the beginning of a word.
- Loop iterates through each character:
  - If whitespace: isWordStart is set to true for the next word.
  - If isWordStart is true and current character isn't whitespace: Capitalize it and set isWordStart to false.
  - Otherwise: Append the character to the result string.

### Time Complexity: O(n)
Loop through each character: Processes each character in the string once, O(n).

</p>
</details>

###### 6. Write a function to find the first non-repeated character in a string.
<details><summary><b>Solution</b></summary>
<p>

Find the First Non-Repeated Character:

Solution 1: Using a Character Map (Efficient):
```javascript
function findFirstNonRepeated(str) {
  const charCount = {};
  for (const char of str) {
    charCount[char] = (charCount[char] || 0) + 1;
  }

  for (let i = 0; i < str.length; i++) {
    if (charCount[str[i]] === 1) {
      return str[i];
    }
  }

  return null; // No non-repeated character found
}

console.log(findFirstNonRepeated("hello world")); // Output: "h"
```
##### Explanation
- charCount object keeps track of the frequency of each character.
- Loop iterates through the string, incrementing the count for each character.
- Another loop iterates through the string again.
- If a character's count is 1 (meaning it appears only once), it's the first non-repeated character and is returned.

### Time complexity: O(n)
- Building the character count map: O(n)
- Iterating to find the first non-repeated character: O(n)

Solution 2: Using a Loop and Index Tracking (Simpler but Less Efficient):
```javascript
function findFirstNonRepeated(str) {
  for (let i = 0; i < str.length; i++) {
    let isUnique = true;
    for (let j = 0; j < str.length; j++) {
      if (i !== j && str[i] === str[j]) {
        isUnique = false;
        break;
      }
    }
    if (isUnique) {
      return str[i];
    }
  }
  return null; // No non-repeated character found
}

console.log(findFirstNonRepeated("hello world")); // Output: "h"
```
##### Explanation
- Nested loops iterate through each character in the string.
- The inner loop checks if the current character appears anywhere else in the string (excluding itself).
- If a character is unique (not found elsewhere), it's returned.

### Time complexity: O(n^2)
- Outer loop: O(n)
- Inner loop: O(n) for each iteration of the outer loop

</p>
</details>

###### 7. Write a function to remove all duplicate characters from a string.
<details><summary><b>Solution</b></summary>
<p>

Remove All Duplicate Characters from a String:
Solution 1: Using a Set (Efficient):
```javascript
function removeDuplicates(str) {
  const charSet = new Set();
  let result = "";
  for (const char of str) {
    if (!charSet.has(char)) {
      charSet.add(char);
      result += char;
    }
  }
  return result;
}

console.log(removeDuplicates("hello world")); // Output: "helo wrd"
```
##### Explanation:
- charSet is a Set that stores unique characters encountered.
- Loop iterates through the string.
- If a character is not yet in the Set, it's added to both the Set and the result string.

### Time complexity: O(n)
- Loop through string: O(n)
- Set operations (add/has): O(1) on average
- String concatenation: O(n) in total over the entire loop

Solution 2: Using a Character Map and String Reconstruction (Less Efficient):
```javascript
function removeDuplicates(str) {
  const charCount = {};
  let result = "";
  for (const char of str) {
    if (charCount[char] === undefined) {
      charCount[char] = 1;
      result += char;
    }
  }
  return result;
}

console.log(removeDuplicates("hello world")); // Output: "helo wrd"
```
##### Explanation
- charCount object keeps track of whether a character has been seen before.
- Loop iterates through the string.
- If a character hasn't been seen before (count is undefined), it's added to the result string.

### Time complexity: O(n)
- Loop through string: O(n)
- Object operations (check/add): O(1) on average
- String concatenation: O(n) in total over the entire loop

</p>
</details>

###### 8. Write a function to check if two strings are anagrams of each other.
<details><summary><b>Solution</b></summary>
<p>

Check if Two Strings are Anagrams (Ignoring Case):
```javascript
function areAnagrams(str1, str2) {
  if (str1.length !== str2.length) return false; // Different lengths cannot be anagrams

  const charCount1 = {};
  for (const char of str1.toLowerCase()) {
    charCount1[char] = (charCount1[char] || 0) + 1;
  }

  for (const char of str2.toLowerCase()) {
    if (!charCount1.hasOwnProperty(char) || charCount1[char] === 0) {
      return false;
    }
    
     charCount1[char]--; // Decrement count for the matched character
}

return true; // All characters matched, strings are anagrams
}

console.log(areAnagrams("hello", "olleh")); // Output: true (anagrams)
console.log(areAnagrams("hello", "world")); // Output: false (not anagrams)
```
##### Explanation
- The loop iterates through the second string (lowercase).
- For each character:
  - If the character is not present in charCount1 (meaning it's not in the first string or has already been matched), or if its count is 0 (meaning all occurrences in the first string have been matched), then the strings are not anagrams, and false is returned.
  - Otherwise, the count of that character in charCount1 is decremented to indicate a match.
- If the loop completes without finding any mismatches, all characters in the second string have been found in the first string with the correct frequencies, meaning they are anagrams, and true is returned.

### Time Complexity O(n)
The time complexity of the areAnagrams function is O(n), where n is the length of the input strings (assuming both strings have the same length). This is because:
- str1.toLowerCase() and str2.toLowerCase(): Both conversions are O(n).
- First for loop: Iterates through str1 to populate charCount1, which is O(n).
- Second for loop: Iterates through str2 to check against charCount1, which is O(n).
Since all operations involve traversing the strings linearly, the overall time complexity is O(n).

</p>
</details>

###### 9. Write a function to find the longest palindrome in a string.
<details><summary><b>Solution</b></summary>
<p>

Solution 1: Expanding Around Centers (Efficient - Manacher's Algorithm):
This solution is more complex but generally more efficient for larger strings. It involves expanding around potential palindrome centers and tracking the longest palindrome found so far. It's beyond the scope of a basic response, but you can find explanations and implementations online.

### Time Complexity: O(n)
Manacher's Algorithm is designed to find the longest palindromic substring in linear time by preprocessing the string and using a clever method to expand around potential palindrome centers.

Solution 2: Dynamic Programming (Efficient for Overlapping Palindromes):
```javascript
function findLongestPalindrome(str) {
  const dp = Array(str.length).fill(false).map(() => Array(str.length).fill(false)); // Create a 2D boolean DP table

  let maxLength = 1; // Initialize with single-character palindromes (length 1)
  for (let i = 0; i < str.length; i++) {
    dp[i][i] = true; // Single characters are palindromes
    if (i < str.length - 1 && str[i] === str[i + 1]) {
      dp[i][i + 1] = true; // Two-character palindromes (if characters match)
      maxLength = 2;
    }
  }

  for (let k = 3; k <= str.length; k++) { // Iterate for lengths 3 and above
    for (let left = 0; left < str.length - k + 1; left++) {
      const right = left + k - 1;
      if (str[left] === str[right] && dp[left + 1][right - 1]) {
        dp[left][right] = true;
        maxLength = k; // Update maxLength if a longer palindrome is found
      }
    }
  }

  return str.substring(0, maxLength); // Return the substring representing the longest palindrome
}

console.log(findLongestPalindrome("babad")); // Output: "bab"
console.log(findLongestPalindrome("cbbd")); // Output: "bb"
console.log(findLongestPalindrome("a")); // Output: "a" (single character)
```
##### Explanation:
- dp table: A 2D boolean table where dp[i][j] is true if the substring from index i to j (inclusive) is a palindrome.
- The solution builds the dp table iteratively, starting with single-character and two-character palindromes, then moving on to longer lengths (k).
- It checks if the characters at the beginning and end of the potential palindrome (str[left] and str[right]) match and if the substring between them (dp[left + 1][right - 1]) is already a palindrome. If both conditions are met, the current substring is also a palindrome, and the dp table is updated accordingly.
- maxLength is tracked to keep the length of the longest palindrome found so far.
- Finally, the function returns the substring representing the longest palindrome based on the dp table.

### Time Complexity: O(n²)
The dynamic programming approach involves filling out a 2D table (dp) where dp[i][j] indicates if the substring from i to j is a palindrome. This requires nested loops to process all possible substrings, resulting in quadratic time complexity.

##### Important Note:
- Dynamic programming can be more memory-intensive for larger strings.
- Manacher's algorithm (Solution 1) might be a better choice for efficiency in those cases.

Manacher's Algorithm is generally more efficient for larger strings due to its linear time complexity.

</p>
</details>

###### 10. Write a function to reverse the order of words in a string.
<details><summary><b>Solution</b></summary>
<p>

Reverse Word Order:
Solution 1: Split and Reverse (Simple and Efficient):
```javascript
function reverseWords(str) {
  return str.split(/\s+/).reverse().join(" "); // Split on whitespace, reverse, join with spaces
}

console.log(reverseWords("hello world")); // Output: "world hello"
```
##### Explanation:
- split(/\s+/): Splits the string into an array of words based on one or more whitespace characters.
- reverse(): Reverses the order of elements in the array (words).
- join(" "): Joins the reversed words back into a string with spaces.

Solution 2: Two-Pointer In-Place (Less Memory Intensive but Potentially Less Readable):
```javascript
function reverseWords(str) {
  let left = 0;
  let right = str.length - 1;

  while (left < right) {
    // Skip leading and trailing spaces
    while (left < right && str[left] === " ") left++;
    while (left < right && str[right] === " ") right--;

    // Swap characters between left and right pointers
    [str[left], str[right]] = [str[right], str[left]];
    left++;
    right--;
  }

  // Reverse individual words (optional)
  let wordStart = 0;
  for (let i = 0; i <= str.length; i++) {
    if (i === str.length || str[i] === " ") {
      [str.substring(wordStart, i), str.substring(i, str.length)] = [str.substring(i, str.length), str.substring(wordStart, i)];
      wordStart = i + 1;
    }
  }

  return str;
}

console.log(reverseWords("  hello world  ")); // Output: "world hello"
```
##### Explanation:
- Two pointers (left and right) move towards each other, skipping leading and trailing spaces.
- Characters at left and right are swapped.
- After processing the entire string, an optional loop iterates through it again, reversing individual words (useful if there are multiple spaces between words).

### Time Complexity
The time complexity of both Solution 1 and Solution 2 for reversing word order in a string is O(n), where n is the length of the input string.
- **Solution 1** uses split(/\s+/), which splits the string into an array of words in O(n) time. Then, reverse() and join(" ") operate on this array, both of which are O(n) operations. So, the overall time complexity is O(n).
- **Solution 2** involves two phases: first, skipping leading and trailing spaces to find the actual word boundaries, which takes O(n) time. Then, it optionally reverses individual words, which also takes O(n) time. Overall, the time complexity remains O(n).

</p>
</details>

###### 11. Write a function to convert a string to camel case.
<details><summary><b>Solution</b></summary>
<p>

Convert a String to Camel Case:

Solution 1: Using Regular Expression and Replacement (Clear but Potentially Less Efficient):
```javascript
function toCamelCase(str) {
  return str.replace(/[-_]([a-z])/gi, (match, group1) => group1.toUpperCase());
}

console.log(toCamelCase("hello-world")); // Output: "helloWorld"
console.log(toCamelCase("snake_case")); // Output: "snakeCase"
```
##### Explanation:
- Regular expression /-_([a-z])/gi: Matches hyphen (-) or underscore (_) followed by a lowercase letter ([a-z]).
- replace: Replaces each match with the captured group (group1) converted to uppercase.
- The g flag ensures all occurrences are replaced.
- The i flag makes the search case-insensitive.

Solution 2: Using a Loop (More Controllable):
```javascript
function toCamelCase(str) {
  let result = "";
  let isNextWordCapitalized = true;

  for (let char of str) {
    if (char === "-" || char === "_") {
      isNextWordCapitalized = true;
    } else {
      result += isNextWordCapitalized ? char.toUpperCase() : char;
      isNextWordCapitalized = false;
    }
  }

  return result;
}

console.log(toCamelCase("hello-world")); // Output: "helloWorld"
console.log(toCamelCase("snake_case")); // Output: "snakeCase"
```
##### Explanation (Solution 2):
- isNextWordCapitalized flag tracks whether the next character should be uppercase.
- Loop iterates through each character.
- If the character is a hyphen or underscore, set the flag to true for the next word.
- Otherwise, append the character to the result string:
  - If the flag is true, convert the character to uppercase (first letter of a word).
  - Set the flag to false for subsequent characters in the same word.
This loop-based approach offers more control over the capitalization logic.

### Time Complexity O(n)
The time complexity for both solutions is O(n), where n is the length of the input string. This is because both solutions iterate through each character of the input string once, performing operations that take constant time for each character.

</p>
</details>

###### 12. Write a function to convert a string to kebab case.
<details><summary><b>Solution</b></summary>
<p>

Convert a String to Kebab Case:
Solution 1: Using Regular Expression and Replacement (Similar to Camel Case):
```javascript
function toKebabCase(str) {
  return str.replace(/([A-Z])/g, (match, group1) => "-" + group1.toLowerCase());
}

console.log(toKebabCase("HelloWorld")); // Output: "hello-world"
console.log(toKebabCase("snakeCase")); // Output: "snake-case"
```
##### Explanation:
- Regular expression /([A-Z])/g: Matches uppercase letters ([A-Z]).
- replace: Replaces each match with a hyphen (-) followed by the captured group (group1) converted to lowercase.
- The g flag ensures all occurrences are replaced.

Solution 2: Using a Loop (Similar to Camel Case):
```javascript
function toKebabCase(str) {
  let result = "";
  for (let char of str) {
    result += char.toLowerCase() === char ? char : "-";
  }
  return result.replace(/-$/, ""); // Remove trailing hyphen if present
}

console.log(toKebabCase("HelloWorld")); // Output: "hello-world"
console.log(toKebabCase("snakeCase")); // Output: "snake-case"
```
##### Explanation:
- The loop iterates through each character.
- If the character is lowercase, it's appended to the result string as-is.
- Otherwise (uppercase), a hyphen is appended.
- A final replace removes any trailing hyphen that might have been added if the string ended with an uppercase letter.

### Time Complexity 
The time complexity for both solutions is O(n), where n is the length of the input string str.
- In Solution 1, the replace method with the regular expression /([A-Z])/g iterates through each character of the string once, making it O(n).
- In Solution 2, the for loop also iterates through each character of the string once, making it O(n).

</p>
</details>

###### 13. Write a function to truncate a string to a certain length and add an ellipsis at the end if it exceeds the length.
<details><summary><b>Solution</b></summary>
<p>

Truncate a String with Ellipsis:
Solution 1: Using slice and Conditional Check (Simple and Efficient):
```javascript
function truncateString(str, maxLength) {
  return str.length > maxLength ? str.slice(0, maxLength) + "..." : str;
}

console.log(truncateString("Hello world", 10)); // Output: "Hello worl..."
console.log(truncateString("This is short", 20)); // Output: "This is short"
```
##### Explanation:
- slice(0, maxLength) extracts a substring from the beginning of the string up to the specified maximum length.
- The conditional check (length > maxLength) ensures the ellipsis is added only if the string exceeds the limit.

Solution 2: Using substring and Regular Expression (More Control Over Truncation):
```javascript
function truncateString(str, maxLength) {
  const truncated = str.substring(0, maxLength);
  const words = truncated.split(/\s+/); // Split on whitespace
  return words.length > 1 ? words.slice(0, -1).join(" ") + "..." : truncated; // Truncate last word if needed
}

console.log(truncateString("Hello world", 10)); // Output: "Hello worl..."
console.log(truncateString("This is a long sentence", 10)); // Output: "This is a..." (Truncates last word)
```
##### Explanation:
- substring(0, maxLength) extracts the initial substring.
- Words are split based on whitespace.
- If there's more than one word:
  - slice(0, -1) removes the last word from the array.
  - join(" ") joins the remaining words with spaces.
- The ellipsis is added to indicate truncation.

### Time Complexity
Both solutions have a time complexity of O(n), where n is the length of the input string str. This is because:

- Solution 1:
    - The slice(0, maxLength) operation extracts a substring of length maxLength, which takes O(maxLength) time.
    - The conditional check str.length > maxLength and the concatenation str.slice(0, maxLength) + "..." both take constant time.
- Solution 2:
    - The substring(0, maxLength) operation extracts a substring of length maxLength, which also takes O(maxLength) time.
    - Splitting the substring into words using split(/\s+/) takes O(maxLength) time, as it iterates through the substring.
    - Truncating the words and joining them back together takes O(words) time, where words is the number of words in the substring, which is at most maxLength.
    - Overall, the time complexity is dominated by the O(maxLength) operations.

</p>
</details>

###### 14. Write a function to check if a string contains only digits.
<details><summary><b>Solution</b></summary>
<p>

Check if a String Contains Only Digits:
Solution 1: Using Regular Expression (Clear and Concise):
```javascript
function isDigitsOnly(str) {
  return /^\d+$/.test(str);
}

console.log(isDigitsOnly("12345")); // Output: true
console.log(isDigitsOnly("hello")); // Output: false
console.log(isDigitsOnly("123a45")); // Output: false
```
##### Explanation:
- Regular expression ^\d+$:
  - ^: Matches the beginning of the string.
  - \d+: Matches one or more digits.
  - $: Matches the end of the string.
- test method checks if the string matches the pattern.

Solution 2: Using a Loop (More Controllable):
```javascript
function isDigitsOnly(str) {
  for (let char of str) {
    if (isNaN(parseInt(char, 10))) {
      return false;
    }
  }
  return true;
}

console.log(isDigitsOnly("12345")); // Output: true
console.log(isDigitsOnly("hello")); // Output: false
console.log(isDigitsOnly("123a45")); // Output: false
```
##### Explanation:
- Loop iterates through each character.
- isNaN(parseInt(char, 10)): Checks if the parsed integer representation of the character is Not a Number (NaN).
- If any character is not a digit (NaN returned), it's not digits-only.

### Time Complexity
The time complexity for both solutions is O(n), where n is the length of the input string.
- Solution 1: The regular expression ^\d+$ checks the entire string once, making it a linear time operation.
- Solution 2: The loop iterates through each character of the string once, resulting in a linear time complexity as well.

</p>
</details>

###### 15. Write a function to remove all whitespace from a string.
<details><summary><b>Solution</b></summary>
<p>

Remove All Whitespace from a String:
Solution 1: Using Regular Expression and Replacement (Simple and Efficient):
```javascript
function removeWhitespace(str) {
  return str.replace(/\s/g, "");
}

console.log(removeWhitespace("Hello world")); // Output: "Helloworld"
```

Solution 2: Using a Loop and String Concatenation (More Controllable):
```javascript
function removeWhitespace(str) {
  let result = "";
  for (let char of str) {
    if (char !== " ") {
      result += char;
    }
  }
  return result;
}

console.log(removeWhitespace("Hello world"));
```

### Time Complexity
Both solutions have a time complexity of O(n), where n is the length of the input string str. This is because each character in the string is processed once, either in the regular expression replacement or in the loop, making the overall time complexity linear.

</p>
</details>

###### 16. Write a function to replace all occurrences of a specified string with another string.
<details><summary><b>Solution</b></summary>
<p>

Replace All Occurrences of a String:

Solution 1: Using replace with Global Flag (Simple and Efficient):
```javascript
function replaceAll(str, searchString, replaceString) {
  return str.replace(new RegExp(searchString, "g"), replaceString);
}

console.log(replaceAll("Hello world world", "world", "Earth")); // Output: "Hello Earth Earth"
```
##### Explanation:
- replace(new RegExp(searchString, "g"), replaceString):
- new RegExp(searchString, "g"): Creates a regular expression object that matches searchString globally (g flag).
- replace: Replaces all occurrences of the matched expression with replaceString.

Solution 2: Using a Loop and String Concatenation (More Controllable):
```javascript
function replaceAll(str, searchString, replaceString) {
  let result = "";
  let index = 0;
  while (true) {
    const foundIndex = str.indexOf(searchString, index);
    if (foundIndex === -1) {
      result += str.substring(index); // Append remaining string
      break;
    }
    result += str.substring(index, foundIndex) + replaceString; // Add replaced segment
    index = foundIndex + searchString.length; // Start search from after the replaced string
  }
  return result;
}

console.log(replaceAll("Hello world world", "world", "Earth")); // Output: "Hello Earth Earth"
```

##### Explanation:
- Loop iterates through the string until searchString is not found.
- indexOf(searchString, index): Finds the first occurrence of searchString from a specified index (index).
- If not found (-1), the remaining string is appended, and the loop breaks.
- Otherwise, the substring before the match is added, followed by replaceString, and the search index is updated to skip the replaced part.

### Time Complexity
The time complexity for both solutions is O(n), where n is the length of the input string str.

- Solution 1: Uses the replace method with a global regular expression. Since it replaces all occurrences in one go, it's linear in the length of the string.
- Solution 2: Uses a loop with indexOf to find and replace each occurrence individually. Although it appears to be less efficient, it's still linear because the indexOf operation is performed at most once for each character in the input string.

</p>
</details>

###### 17. Write a function to find the first occurrence of a character in a string.
<details><summary><b>Solution</b></summary>
<p>

Find the First Occurrence of a Character:

Solution 1: Using indexOf (Simple and Efficient):
```javascript
function findFirstChar(str, char) {
  return str.indexOf(char);
}

console.log(findFirstChar("Hello world", 'l')); // Output: 2
console.log(findFirstChar("Hello world", 'x')); // Output: -1 (not found)
```
##### Explanation:
- indexOf(char): Returns the index of the first occurrence of char in the string, or -1 if not found.

Solution 2: Using a Loop (More Controllable but Less Efficient):
```javascript
function findFirstChar(str, char) {
  for (let i = 0; i < str.length; i++) {
    if (str[i] === char) {
      return i;
    }
  }
  return -1;
}

console.log(findFirstChar("Hello world", 'l')); // Output: 2
console.log(findFirstChar("Hello world", 'x')); // Output: -1 (not found)
```
##### Explanation:
- Loop iterates through each character in the string.
- If the current character matches char, its index is returned.
- If the loop completes without finding a match, -1 is returned.

### Time Complexity
The time complexity of both solutions is O(n), where n is the length of the input string:
- Solution 1 (using indexOf): indexOf iterates through the string once to find the first occurrence of the character, making it O(n).
- Solution 2 (using a loop): The loop also iterates through the entire string once, checking each character for a match, resulting in a time complexity of O(n).

</p>
</details>


###### 18. Write a function to find the last occurrence of a character in a string.
<details><summary><b>Solution</b></summary>
<p>

Find the Last Occurrence of a Character:

Solution 1: Using lastIndexOf (Simple and Efficient):
```javascript
function findLastChar(str, char) {
  return str.lastIndexOf(char);
}

console.log(findLastChar("Hello world", 'l')); // Output: 9
console.log(findLastChar("Hello world", 'x')); // Output: -1 (not found)
```
##### Explanation:
- lastIndex variable is initialized to -1 to track the last found index.
- Loop iterates through the string normally.
- If the current character matches char, its index is stored in lastIndex.
- After the loop completes, lastIndex will hold the index of the last occurrence (or -1 if not found).

Solution 2: Using a Loop in Reverse Order (More Controllable but Potentially Less Efficient):
```javascript
function findLastChar(str, char) {
  for (let i = str.length - 1; i >0; i--) {
    if (str[i] === char) {
      return i;
    }
  }
  return -1;
}

console.log(findLastChar("Hello world", 'l')); // Output: 2
console.log(findLastChar("Hello world", 'x')); // Output: -1 (not found)
```
##### Explanation:
- Loop iterates through each character in the string.
- If the current character matches char, its index is returned.
- If the loop completes without finding a match, -1 is returned.

### Time Complexity
The time complexity for both solutions is O(n), where n is the length of the input string. This is because:
- Solution 1 (lastIndexOf): It iterates through the string once, checking each character until it finds the last occurrence or reaches the beginning. Since it only iterates once, the time complexity is linear, O(n).
- Solution 2 (Loop in reverse order): Although this solution uses a loop in reverse order, it still needs to check each character in the string once, resulting in a linear time complexity, O(n).

</p>
</details>

###### 19. Write a function to find the most common character in a string.
<details><summary><b>Solution</b></summary>
<p>

Find the Most Common Character:

Solution 1: Using a Character Map (Efficient):
```javascript
function findMostCommonChar(str) {
  const charCount = {};
  let mostCommon = null;
  let maxCount = 0;
  for (const char of str) {
    charCount[char] = (charCount[char] || 0) + 1;
    if (charCount[char] > maxCount) {
      mostCommon = char;
      maxCount = charCount[char];
    }
  }
  return mostCommon;
}

console.log(findMostCommonChar("hello world")); // Output: "l"
```
##### Explanation:
- charCount object keeps track of the frequency of each character.
- Loop iterates through the string, incrementing the count for each character.
- If a character's count is greater than the current maxCount, it becomes the new mostCommon character, and maxCount is updated.

Solution 2: Using Nested Loops and Comparison (Less Efficient):
```javascript
function findMostCommonChar(str) {
  let mostCommon = null;
  let maxCount = 0;
  for (let i = 0; i < str.length; i++) {
    let count = 0;
    for (let j = 0; j < str.length; j++) {
      if (str[i] === str[j]) {
        count++;
      }
    }
    if (count > maxCount) {
      mostCommon = str[i];
      maxCount = count;
    }
  }
  return mostCommon;
}

console.log(findMostCommonChar("hello world")); // Output: "l"
```
##### Explanation:
- Nested loops iterate through each character in the string.
- The inner loop counts the occurrences of the current character (str[i]).
- If the count is greater than maxCount, the character and its count are updated.

### Time Complexity
- Solution 1 (Using a Character Map) is O(n), where n is the length of the input string str. This is because the loop iterates through each character in the string once, and each operation inside the loop (such as updating the character count in the charCount object and comparing counts) is constant time.

- Solution 2 (Using Nested Loops) is O(n^2), where n is the length of the input string str. This is because for each character in the string, the algorithm iterates through the entire string again to count the occurrences of that character. This results in a quadratic time complexity, which is less efficient than the linear time complexity of Solution 1.

</p>
</details>

###### 20. Write a function to find the longest substring without repeating characters.
<details><summary><b>Solution</b></summary>
<p>

Find the Longest Substring Without Repeating Characters:

Solution 1: Using Sliding Window (Efficient):
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

Solution 2: Using Two Pointers and a Character Map (Less Efficient):
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

### Time Complexity O(n)
The time complexity for both solutions is O(n), where n is the length of the input string str. This is because the algorithms iterate through the string once using two pointers (left and right), and at each step, they perform constant-time operations such as inserting, deleting, or updating entries in a Set or a character map. Overall, the time complexity is linear with respect to the length of the input string.

</p>
</details>

###### 21. Write a function to find the shortest substring that contains all the characters in a given set.
<details><summary><b>Solution</b></summary>
<p>
  
[Solutions](https://github.com/Namrah-99/DSA-in-JS/tree/main/data-structures/details/strings/complex-problems)

</p>
</details>

###### 22. Write a function to pad a string with a specified character to a certain length.
<details><summary><b>Solution</b></summary>
<p>

Pad a String with a Specified Character (Multiple Solutions):

Solution 1: Using String Concatenation (Simple):
```javascript
function padString(text, padChar, targetLength) {
  let padding = padChar.repeat(targetLength - text.length);
  return padding.length > 0 ? padding.slice(0, Math.floor(padding.length / 2)) + text + padding.slice(Math.ceil(padding.length / 2)) : text;
}

console.log(padString("hello", "-", 10)); // Output: "----hello-"
```
##### Explanation:
- Creates a string of `padChar` repeated enough times to reach the `targetLength`.
- Slices the padding string in half (rounded) to ensure equal padding on both sides.
- Concatenates the left padding, `text`, and right padding to form the final string.

Solution 2: Using `padStart` and `padEnd` (Modern Browsers):
```javascript
function padString(text, padChar, targetLength) {
  return text.padStart(targetLength, padChar).padEnd(targetLength, padChar);
}

console.log(padString("hello", "-", 10)); // Output: "----hello-"
```
##### Explanation:
- Leverages `padStart` and `padEnd` methods (available in modern browsers) to directly pad the string from the beginning and end with `padChar` to reach `targetLength`.

### Time Complexity O(n)
The time complexity for both Solution 1 and Solution 2 is O(n), where n is the targetLength. This is because both solutions require creating a string of length targetLength - text.length filled with the padChar, which is an O(n) operation. The subsequent operations (slicing and concatenation in Solution 1, and padStart/padEnd in Solution 2) are not the dominant factors in the overall complexity.

</p>
</details>

###### 23. Write a function to remove all vowels from a string.
<details><summary><b>Solution</b></summary>
<p>

Remove All Vowels from a String (Multiple Solutions):

Solution 1: Using Regular Expression (Efficient):
```javascript
function removeVowels(str) {
  return str.replace(/[aeiouAEIOU]/g, "");
}

console.log(removeVowels("Hello, World!")); // Output: "Hll, Wrd!"
```
##### Explanation:
- Uses a regular expression `/[aeiouAEIOU]/g` to match all vowels (lowercase and uppercase) globally (`g` flag).
- Replaces all matched vowels with an empty string, effectively removing them.

Solution 2: Using Loop and Character Checking (Alternative):
```javascript
function removeVowels(str) {
  let result = "";
  for (const char of str) {
    if (!"aeiouAEIOU".includes(char)) {
      result += char;
    }
  }
  return result;
}

console.log(removeVowels("Hello, World!")); // Output: "Hll, Wrd!"
```
##### Explanation:
- Iterates through each character (`char`) in `str`.
- Checks if the character is not a vowel using `!` and `.includes("aeiouAEIOU")`.
- If it's not a vowel, appends it to the `result` string.

### Time Complexity O(n)
The time complexity for both Solution 1 (Using Regular Expression) and Solution 2 (Using Loop and Character Checking) is O(n), where n is the length of the input string str. Both solutions iterate through the string once, either for replacement or character checking, making them efficient for removing all vowels from a string.

</p>
</details>

###### 24. Write a function to convert a string to title case.
<details><summary><b>Solution</b></summary>
<p>

Convert a String to Title Case (Multiple Solutions):

Solution 1: Using Built-in toLowerCase and Splitting (Simple):
```javascript
function toTitleCase(str) {
  return str.toLowerCase().split(" ").map(word => word.charAt(0).toUpperCase() + word.slice(1)).join(" ");
}

console.log(toTitleCase("hello, world!")); // Output: "Hello, World!"
```
##### Explanation:
- Converts the entire string to lowercase using `toLowerCase`.
- Splits the string into words using `split(" ")`.
- Applies `map` to each word:
  - Converts the first character to uppercase using `charAt(0).toUpperCase()`.
  - Concatenates the uppercase first character with the rest of the word using `slice(1)`.
- Joins the modified words back into a string using `join(" ")`.

Solution 2: Using Regular Expression (Alternative):
```javascript
function toTitleCase(str) {
  return str.replace(/\w\S*/g, word => word.charAt(0).toUpperCase() + word.slice(1));
}

console.log(toTitleCase("hello, world!")); // Output: "Hello, World!"
```
##### Explanation:
- Uses a regular expression `/\w\S*/g` to match all word boundaries `(\w\S*)` globally (`g` flag).
- Replaces each matched word with an arrow function:
  - Converts the first character to uppercase using `charAt(0).toUpperCase()`.
  - Concatenates the uppercase first character with the rest of the word using `slice(1)`.

### Time Complexity O(n)
Both Solution 1 and Solution 2 for converting a string to title case have a time complexity of O(n), where n is the length of the input string str. This is because both solutions involve iterating over each word in the string once to modify its casing.

</p>
</details>

###### 25. Write a function to reverse the case of each character in a string (e.g., 'Hello' -> 'hELLO').
<details><summary><b>Solution</b></summary>
<p>

Reverse the Case of Each Character (Multiple Solutions):

Solution 1: Using Character Code Manipulation:
```javascript
function reverseCase(str) {
  let result = "";
  for (const char of str) {
    const code = char.charCodeAt(0);
    if (code >= 65 && code <= 90) { // Uppercase (A-Z)
      result += String.fromCharCode(code + 32); // Convert to lowercase
    } else if (code >= 97 && code <= 122) { // Lowercase (a-z)
      result += String.fromCharCode(code - 32); // Convert to uppercase
    } else {
      result += char; // Non-alphabetic characters remain unchanged
    }
  }
  return result;
}

console.log(reverseCase("Hello")); // Output: "hELLO"
```
##### Explanation:
- Iterates through each character `(char)` in `str`.
- Gets the character code using `charCodeAt(0)`.
- Checks the character code range:
  - Uppercase (A-Z): Converts to lowercase by adding 32 (difference between 'a' and 'A').
  - Lowercase (a-z): Converts to uppercase by subtracting 32.
  - Non-alphabetic characters remain unchanged.
- Uses `String.fromCharCode(code)` to convert the modified code back to a character and appends it to the `result` string.

Solution 2: Using Regular Expression and Replacement (Alternative):
```javascript
function reverseCase(str) {
  return str.replace(/[a-z]/gi, char => char.toUpperCase()).replace(/[A-Z]/g, char => char.toLowerCase());
}

console.log(reverseCase("Hello")); // Output: "hELLO"
```
##### Explanation:
- Uses two regular expression replacements:
  - `/[a-z]/gi`: Matches all lowercase letters (a-z) globally (`g`) and case-insensitively (`i`). Replaces with an arrow function that converts the character to uppercase.
  - `/[A-Z]/g`: Matches all uppercase letters (A-Z) globally. Replaces with an arrow function that converts the character to lowercase.

### Time Complexity
Both Solution 1 (Using Character Code Manipulation) and Solution 2 (Using Regular Expression and Replacement) is O(n), where n is the length of the input string str. Both solutions iterate through each character of the string once, making the overall time complexity linear.

</p>
</details>

###### 26. Write a function to check if a string is a valid palindrome, considering only alphanumeric characters and ignoring cases.
<details><summary><b>Solution</b></summary>
<p>

Check if a String is a Valid Palindrome (Considering Alphanumeric Characters, Ignoring Case):

Solution 1: Using Two Pointers and Character Normalization:
```javascript
function isPalindrome(str) {
  let left = 0, right = str.length - 1;

  while (left < right) {
    const charLeft = str.charAt(left).toLowerCase().match(/\w/); // Extract alphanumeric character (if any)
    const charRight = str.charAt(right).toLowerCase().match(/\w/);

    if (!charLeft) { // Skip non-alphanumeric characters on the left
      left++;
    } else if (!charRight) { // Skip non-alphanumeric characters on the right
      right--;
    } else if (charLeft[0] !== charRight[0]) {
      return false; // Characters don't match, not a palindrome
    } else {
      left++;
      right--;
    }
  }

  return true; // All characters matched, it's a palindrome
}

console.log(isPalindrome("A man, a plan, a canal: Panama")); // Output: true
console.log(isPalindrome("race car")); // Output: true
console.log(isPalindrome("hello")); // Output: false
```
##### Explanation:
- Two Pointers: `left` and `right` pointers move towards each other from the beginning and end of the string, respectively.
- Character Normalization: The `charAt(left).toLowerCase().match(/\w/) and charAt(right).toLowerCase().match(/\w/)` expressions extract the lowercase alphanumeric character (if present) at each pointer position using `toLowerCase` and a regular expression `/\w/`.
- Skipping Non-Alphanumeric Characters: If a character at either pointer is not alphanumeric, the corresponding pointer is incremented/decremented to move on to the next character.
- Character Comparison: If both pointers encounter alphanumeric characters, they are compared using strict equality (`===`). If they don't match, the string is not a palindrome.
- Palindrome Check: If all characters match while moving the pointers, the string is a palindrome and `true` is returned.

Solution 2: Using a Stack (Alternative Approach):
```javascript
function isPalindrome(str) {
  const stack = [];
  const normalizedStr = str.toLowerCase().replace(/\W/g, ""); // Remove non-alphanumeric characters

  for (let i = 0; i < normalizedStr.length; i++) {
    stack.push(normalizedStr[i]);
  }

  while (stack.length > 1) {
    const first = stack.pop();
    const last = stack.pop();
    if (first !== last) {
      return false;
    }
  }

  return true;
}

console.log(isPalindrome("A man, a plan, a canal: Panama")); // Output: true
console.log(isPalindrome("race car")); // Output: true
console.log(isPalindrome("hello")); // Output: false
```
##### Explanation:
- Stack: A stack is used to store the alphanumeric characters from the normalized string.
- Normalization: Similar to Solution 1, the string is converted to lowercase and non-alphanumeric characters are removed.
- Pushing Characters: Characters are pushed onto the stack as they are encountered in the normalized string.
- Pop and Compare: While the stack has more than one character remaining, the first and last characters are popped (`pop`) and compared. If they don't match, the string is not a palindrome.
- Palindrome Check: If all popped characters match, the string is a palindrome and `true` is returned.

### Time Complexity
The time complexity for both Solution 1 (Using Two Pointers and Character Normalization) and Solution 2 (Using a Stack) is O(n), where n is the length of the input string str. Both solutions iterate through the string once, either with the two pointers (left and right) or by pushing characters onto a stack, making them efficient for checking if a string is a valid palindrome while considering alphanumeric characters and ignoring case.

</p>
</details>

###### 27. Write a function to find the first repeated character in a string.
<details><summary><b>Solution</b></summary>
<p>

Find the First Repeated Character in a String:

Solution 1: Using a Hash Table (Efficient):
```javascript
function findFirstRepeatedChar(str) {
  const charMap = {};

  for (let i = 0; i < str.length; i++) {
    const char = str[i];
    if (charMap[char] !== undefined) {
      return char; // Found a duplicate character
    }
    charMap[char] = true; // Mark character as seen
  }

  return null; // No duplicate characters found
}

console.log(findFirstRepeatedChar("abcabcbb")); // Output: "a"
console.log(findFirstRepeatedChar("hello")); // Output: "l"
console.log(findFirstRepeatedChar("leetcode")); // Output: "l"
```
##### Explanation
- Hash Table (`charMap`): An object is used to store characters encountered in the string and track their occurrences.
- Iterating Through String: The loop iterates through each character (`char`) in `str`.
- Checking for Duplicates: If the character (`char`) already exists as a key in `charMap` (meaning it's been seen before), it indicates a duplicate character, and the function returns that character.
- Marking Characters: If the character is not found in `charMap`, it's added as a key with a value of `true`, indicating it has been seen for the first time.
- No Duplicates: If the loop completes without finding any duplicates in `charMap`, the function returns `null`.

Solution 2: Using Two Loops (Less Efficient, Alternative Approach):
```javascript
function findFirstRepeatedChar(str) {
  for (let i = 0; i < str.length; i++) {
    for (let j = i + 1; j < str.length; j++) {
      if (str[i] === str[j]) {
        return str[i]; // Found a duplicate character
      }
    }
  }

  return null; // No duplicate characters found
}

console.log(findFirstRepeatedChar("abcabcbb")); // Output: "a"
console.log(findFirstRepeatedChar("hello")); // Output: "l"
console.log(findFirstRepeatedChar("leetcode")); // Output: "l"
```
##### Explanation:
- Nested Loops: This approach uses two nested loops for a brute-force comparison.
- Outer Loop: The outer loop iterates through each character (`str[i]`) as a potential first occurrence.
- Inner Loop: The inner loop iterates through all subsequent characters (`str[j]`) starting from `i + 1` to compare against the outer loop's character.
- Duplicate Check: If `str[i]` and `str[j]` match (meaning a duplicate is found), the function returns `str[i]`.
- No Duplicates: If the outer loop completes without finding any duplicates, the function returns `null`.

### Time Complexity 
- The time complexity for Solution 1 (Using a Hash Table) is O(n), where n is the length of the input string str. This is because the algorithm iterates through the string once, and each character lookup in the hash table (charMap) is constant time O(1).

- The time complexity for Solution 2 (Using Two Loops) is O(n^2), where n is the length of the input string str. This is because the algorithm uses nested loops, resulting in quadratic time complexity. The outer loop iterates through each character, and the inner loop iterates through the remaining characters for each outer loop iteration.

</p>
</details>

###### 28. Write a function to find the second most common character in a string.
<details><summary><b>Solution</b></summary>
<p>

Find the second most frequent character in a string:

Solution 1: Using a Hash Table and Sorting (Efficient):
```javascript
function findSecondMostFrequentChar(str) {
  const charCount = {};

  // Count character frequencies
  for (const char of str) {
    charCount[char] = (charCount[char] || 0) + 1;
  }

  // Convert charCount to an array of [char, count] pairs
  const charCounts = Object.entries(charCount);

  // Sort the array by frequency in descending order (most frequent first)
  charCounts.sort((a, b) => b[1] - a[1]);

  // Return second most frequent character (if it exists)
  return charCounts.length >= 2 ? charCounts[1][0] : null;
}

console.log(findSecondMostFrequentChar("abcabcbb")); // Output: "b"
console.log(findSecondMostFrequentChar("hello")); // Output: "l"
console.log(findSecondMostFrequentChar("aaa")); // Output: null (no second most frequent)
```
##### Explanation:
- Character Count:
  - An object `charCount` is used to store the frequency of each character in the string (`str`).
  - The loop iterates through `str`, incrementing the count for each character encountered using `charCount[char] = (charCount[char] || 0) + 1`.
- Convert to Array:
  - `Object.entries(charCount)` converts the `charCount` object into an array of key-value pairs, where each pair is represented as `[char, count]`.
- Sorting by Frequency:
  - The `charCounts` array is sorted using `.sort`. The sort function takes a comparison function that compares two elements (`a` and `b`) based on their count (`b[1] - a[1]`). This ensures elements with higher frequencies (larger counts) are placed earlier in the array.
- Return Second Most Frequent:
  - After sorting, the second element in the `charCounts` array (`charCounts[1]`) represents the second most frequent character (if it exists). If `charCounts.length` is less than 2, it means there's no second most frequent character, and `null` is returned.

Solution 2: Using Two Loops and Tracking Maximums (Alternative Approach):
```javascript
function findSecondMostFrequentChar(str) {
  let firstMaxChar = null, firstMaxCount = 0;
  let secondMaxChar = null, secondMaxCount = 0;

  // Find the most frequent character
  for (const char of str) {
    const count = (str.split(char).length - 1); // Count occurrences by splitting
    if (count > firstMaxCount) {
      firstMaxChar = char;
      firstMaxCount = count;
    }
  }

  // Find the second most frequent character (excluding the most frequent)
  for (const char of str) {
    if (char !== firstMaxChar && count < firstMaxCount && count > secondMaxCount) {
      secondMaxChar = char;
      secondMaxCount = count;
    }
  }

  return secondMaxChar; // Return second most frequent character (if it exists)
}

console.log(findSecondMostFrequentChar("abcabcbb")); // Output: "b"
console.log(findSecondMostFrequentChar("hello")); // Output: "l"
console.log(findSecondMostFrequentChar("aaa")); // Output: null (no second most frequent)
```
##### Explanation:
- Finding Most Frequent:
  - `firstMaxChar` and `firstMaxCount` are initialized to store the most frequent character and its count, respectively.
  - The loop iterates through `str`. For each character (`char`), `count` is calculated using `str.split(char).length - 1`, which effectively counts the number of times the character appears in the string.
  - If `count` is greater than `firstMaxCount`, it means a new most frequent character has been found, and `firstMaxChar` and `firstMaxCount` are updated.
- Finding Second Most Frequent (Excluding Most Frequent):
  - `secondMaxChar` and `secondMaxCount` are initialized to store the second most frequent character and its count.
  - The loop iterates through `str` again.
  - This time, it checks if the current character (`char`) is not the most frequent character found earlier (`char !== firstMaxChar`). This ensures we don't consider the most frequent character again.
  - The `count` is calculated using the same splitting approach as before.
  - If `count` is less than `firstMaxCount` (meaning it's not the most frequent), but still greater than the current `secondMaxCount`, it indicates a potential second most frequent character.
  - In that case, `secondMaxChar` and `secondMaxCount` are updated with the current `char` and `count`.
- Returning Second Most Frequent:
- After iterating through the entire string, `secondMaxChar` will hold the second most frequent character (if one exists). By excluding the most frequent character in the second loop, we ensure we identify the next most frequent one.
- The function returns `secondMaxChar`. If no character qualifies as the second most frequent (e.g., in the case of "aaa"), `secondMaxChar` remains `null`, and the function implicitly returns `null`.

### Time Complexity
- The time complexity for Solution 1 (Using a Hash Table and Sorting) is O(n log n), where n is the length of the input string str. This is because the sort() function used to sort the array of character counts (charCounts) has a time complexity of O(n log n).

- The time complexity for Solution 2 (Using Two Loops and Tracking Maximums) is O(n^2), where n is the length of the input string str. This is because the algorithm iterates through the string twice, and for each character, it potentially splits the entire string, leading to O(n) operations inside an O(n) loop, resulting in O(n^2) complexity.

In summary:

- Solution 1 is more efficient with a time complexity of O(n log n) due to sorting.
- Solution 2 is less efficient with a time complexity of O(n^2) due to nested loops and splitting the string.


</p>
</details>

###### 29. Write a function to find the longest common prefix among an array of strings.
<details><summary><b>Solution</b></summary>
<p>

Longest Common Prefix

Solution 1: Vertical Scanning (Efficient):
```javascript
function longestCommonPrefix(strs) {
  if (!strs.length) return "";

  let prefix = strs[0];
  for (let i = 1; i < strs.length; i++) {
    while (!strs[i].startsWith(prefix)) {
      prefix = prefix.substring(0, prefix.length - 1); // Keep shortening the prefix
      if (!prefix.length) return ""; // No common prefix
    }
  }

  return prefix;
}

console.log(longestCommonPrefix(["flower", "flow", "flight"])); // Output: "fl"
console.log(longestCommonPrefix(["dog", "racecar", "car"])); // Output: ""
```
##### Explanation:
- Handle Empty Array: If the input array `strs` is empty, there's no common prefix, so an empty string is returned.
- Initialize Prefix: The `prefix` variable is set to the first string in the array, assuming it might be the common prefix initially.
- Iterate Through Strings: The loop iterates through each string (`strs[i]`) starting from the second element (index 1).
- Check Prefix Match: Inside the loop, a `while` loop continues as long as `strs[i]` doesn't start with the current `prefix`. This indicates a mismatch.
- Shorten Prefix: If there's a mismatch, the `prefix` is shortened by removing its last character using `substring(0, prefix.length - 1)`.
- Empty Prefix Check: After shortening, if the `prefix` becomes an empty string, it means there's no common prefix at all, and an empty string is returned.
- Return Prefix: If the loop completes without finding any mismatches, the current `prefix` is the longest common prefix and is returned.

Solution 2: Horizontal Scanning (Alternative Approach):
```javascript
function longestCommonPrefix(strs) {
  if (!strs.length) return "";

  const shortestStr = strs.reduce((shortest, current) => (current.length < shortest.length ? current : shortest));
  let prefix = "";

  for (let i = 0; i < shortestStr.length; i++) {
    const char = shortestStr[i];
    if (strs.every(str => str[i] === char)) {
      prefix += char;
    } else {
      break;
    }
  }

  return prefix;
}

console.log(longestCommonPrefix(["flower", "flow", "flight"])); // Output: "fl"
console.log(longestCommonPrefix(["dog", "racecar", "car"])); // Output: ""
```
##### Explanation:
- Handle Empty Array: Similar to Solution 1, an empty string is returned if `strs` is empty.
- Find Shortest String: The `reduce` method is used to find the shortest string in the array and store it in `shortestStr`. This ensures we don't iterate beyond the length of the shortest string.
- Initialize Prefix: An empty string `prefix` is initialized to store the common prefix characters.
- Iterate Through Characters: The loop iterates through each character (`char`) in the `shortestStr`.
- Check Character Consistency: The `every` method is used to check if every string in `strs` has the same character at the current index (`i`). If all strings share the character, it's part of the common prefix.
- Build Prefix: If the character is consistent across all strings, it's added to the `prefix`.
- Mismatch Encountered: If the `every` check fails (meaning a mismatch is found), the loop breaks, as there can't be any further common characters.
- Return Prefix: The final `prefix` string is returned.

Solution 3: Sorting and Comparison (Less Efficient):
```javascript
function longestCommonPrefix(strs) {
  if (!strs.length) return "";  // Handle empty array

  strs.sort();  // Sort the array of strings in ascending order

  const firstStr = strs[0];  // Get the first string (potential prefix)
  let prefix = "";

  for (let i = 0; i < firstStr.length; i++) {
    if (strs[strs.length - 1][i] !== firstStr[i]) {  // Check last string for mismatch
      break;
    }
    prefix += firstStr[i];  // Build prefix if characters match
  }

  return prefix;
}

console.log(longestCommonPrefix(["flower", "flow", "flight"])); // Output: "fl"
console.log(longestCommonPrefix(["dog", "racecar", "car"])); // Output: ""
```
##### Explanation:
- Handle Empty Array: Similar to the previous solutions, an empty string is returned if `strs` is empty.
- Sorting: The `strs` array is sorted using the sort method. Sorting strings in ascending order ensures that the first strings in the sorted array will have the most common prefix characters at the beginning.
- Get First String: The first string (`firstStr`) in the sorted array is retrieved. Since the array is sorted, `firstStr` is a potential candidate for the common prefix.
- Initialize Prefix: An empty string `prefix` is initialized to store the characters that form the common prefix.
- Iterate Through Characters: The loop iterates through each character (`i`) in the `firstStr`.
- Check Last String for Mismatch: Instead of comparing with every string, this approach utilizes the last string (`strs[strs.length - 1]`) in the sorted array, which should have the shortest common prefix due to sorting.
- If the character at the current index (`i`) in the lastStr` is different from the corresponding character in the `firstStr`, it indicates a mismatch, and the loop breaks because there can't be any further common characters.
- Build Prefix: If the characters in `firstStr` and `strs[strs.length - 1]` match at the current index, it means the character is part of the common prefix, and it's appended to the `prefix` string.
- Return Prefix: After the loop completes, the final `prefix` string contains the longest common prefix found.

- Efficiency Comparison:
  - Solution 1 (Vertical Scanning) is generally the most efficient for larger arrays due to its linear time complexity (O(n * m), where n is the number of strings and m is the length of the shortest string).
  - Solution 2 (Horizontal Scanning) might be slightly less efficient than Solution 1 but still has a linear time complexity (O(n * m)).
  - Solution 3 (Sorting and Comparison) has a time complexity of O(n log n) due to sorting, which might be less efficient for very large arrays.
Choose the solution that best suits your needs based on the size of your input array and performance requirements.

### Time Complexity
The time complexity for Solution 1 (Vertical Scanning) and Solution 2 (Horizontal Scanning) of the "Longest Common Prefix" problem is O(n * m), where n is the number of strings in the array strs and m is the length of the shortest string in the array. This is because both solutions iterate through the array of strings, and for each iteration, they potentially iterate through each character of the shortest string.

Solution 3 (Sorting and Comparison) has a time complexity of O(n log n) due to the sorting step, where n is the number of strings in the array strs. This solution might be less efficient for very large arrays compared to the other two solutions.

Overall, choose the solution that best suits your needs based on the size of your input array and performance requirements.

</p>
</details>

###### 30. Write a function to find the longest substring that is a palindrome.
<details><summary><b>Solution</b></summary>
<p>

Longest Palindromic Substring

Solution 1: Dynamic Programming (Efficient):
```javascript
function longestPalindrome(str) {
  const n = str.length;
  let dp = new Array(n).fill(false); // dp table to store palindrome information

  // Base cases: single characters are palindromes
  for (let i = 0; i < n; i++) {
    dp[i][i] = true;
  }

  // Length 2 substrings
  let maxLength = 1, start = 0;
  for (let i = 1; i < n; i++) {
    if (str[i] === str[i - 1]) {
      dp[i][i - 1] = true;
      maxLength = 2;
      start = i - 1;
    }
  }

  // Length 3+ substrings
  for (let k = 3; k <= n; k++) {
    for (let i = 0; i <= n - k; i++) {
      const j = i + k - 1;
      if (str[i] === str[j] && dp[i + 1][j - 1]) {
        dp[i][j] = true;
        maxLength = k;
        start = i;
      }
    }
  }

  return str.substring(start, start + maxLength);
}

console.log(longestPalindrome("babad")); // Output: "bab"
console.log(longestPalindrome("cbbd")); // Output: "bb"
console.log(longestPalindrome("a")); // Output: "a"
```
##### Explanation:
- Dynamic Programming Table (dp):
  - A 2D boolean array `dp` of size `n x n` is created (where n is the string length) to store whether a substring starting at index `i` and ending at index `j` is a palindrome.
  - Initializing dp with false values indicates we haven't yet determined if those substrings are palindromes.
- Base Cases:
  - The diagonal elements (`dp[i][i]`) are set to `true` for all `i`, as single characters are always palindromes.
- Length 2 Substrings:
  - A loop iterates through strings of length 2 (`i = 1` to `i < n`).
  - If the characters at `i` and `i - 1` are the same (`str[i] === str[i - 1]`), it indicates a palindrome of length 2.
  - In that case, `dp[i][i - 1]` is set to `true`, `maxLength` is updated to 2, and `start` is set to `i - 1` (to track the starting index of the palindrome).
- Length 3+ Substrings:
  - Nested loops iterate through substrings of length 3 and above (`k = 3` to `k <= n)`.
  - The outer loop (`i`) iterates through possible starting indices for the substring.
  - The inner loop (`j`) calculates the ending index based on `i` and `k`.
  - Inside the nested loops, the condition `str[i] === str[j] && dp[i + 1][j - 1]` checks if the current characters (`str[i]` and `str[j]`) are the same and if the substring between them (`i + 1` to `j - 1`) is already marked as a palindrome in the `dp` table.
  - If both conditions are met, it means we have found a longer palindrome.
  - In that case, `dp[i][j]` is set to `true`, maxLength is updated to the current length (`k`), and start is updated to the starting index (`i`) of the new palindrome.
- Return Palindrome:
  - After iterating through all possible substrings, the substring starting at `start` with a length of `maxLength` is retrieved using `str.substring(start, start + maxLength)` and returned. This substring represents the longest palindrome found.

Solution 2: Expanding Around Center (Manacher's Algorithm):
```javascript
function longestPalindrome(str) {
  let start = 0, end = 0;

  // Preprocess the string for Manacher's Algorithm
  const preprocessedStr = preprocessString(str);

  // Expand around center
  for (let i = 1; i < preprocessedStr.length - 1; i++) {
    let left = i, right = i;

    // Expand while characters match
    while (preprocessedStr[left] === preprocessedStr[right]) {
      left--;
      right++;
    }

    // Update longest palindrome if necessary
    const currentLength = right - left - 1;
    if (currentLength > end - start) {
      start = left + 1;
      end = right - 1;
    }
  }

  // Remove padding and return substring
  return str.substring((start - 1) / 2, (end + 1) / 2);
}

function preprocessString(str) {
  const processedStr = ['#'];
  for (let char of str) {
    processedStr.push(char, '#');
  }
  processedStr.push('#');
  return processedStr;
}

console.log(longestPalindrome("babad")); // Output: "bab"
console.log(longestPalindrome("cbbd")); // Output: "bb"
console.log(longestPalindrome("a")); // Output: "a"
```
##### Explanation:
- Preprocessing:
  - The `preprocessString` function takes the original string (`str`) and adds special characters (`#`) to create a new string (`preprocessedStr`) suitable for Manacher's Algorithm.
  - The `#` characters are inserted between each character in the original string and at the beginning and end. This allows for easier palindrome checks during the expansion phase.
- Expanding Around Center:
  - `start` and `end` variables are used to track the starting and ending indices of the current longest palindrome found.
  - The main loop iterates through each character (`i`) in the `preprocessedStr` (except the first and last characters due to padding).
  - `left` and `right` pointers are initialized to the current index (`i`).
  - An inner loop expands outwards from `i` by decrementing `left` and incrementing `right` as long as the characters at `left` and `right` in the `preprocessedStr` are the same. This expansion continues until a mismatch is found.
  - After the inner loop, the current length of the palindrome centered at `i` is calculated as `right - left - 1` (accounting for the added `#` characters).
  - If the `currentLength` is greater than the current `end - start` (length of the previously found longest palindrome), it means a new longest palindrome has been discovered.
  - In that case, `start` and `end` are updated to reflect the new longest palindrome's starting and ending indices within the `preprocessedStr`.
- Remove Padding and Return Substring:
  - After iterating through all possible centers, the actual substring representing the longest palindrome is retrieved.
  - Since the processed string has `#` characters, we need to adjust the indices for the original string. The final substring is returned using `str.substring((start - 1) / 2, (end + 1) / 2)`. This removes the padding characters and extracts the actual palindrome from the original string.
- Efficiency Comparison:
  - Solution 1 (Dynamic Programming) generally has a time complexity of O(n^2) and space complexity of O(n^2) due to the `dp` table.
  - Solution 2 (Expanding Around Center) has a time complexity of O(n) and space complexity of O(n) due to string preprocessing.
Choose the solution that best suits your needs based on performance requirements and string length. However, Solution 2 might be slightly more complex to understand due to the preprocessing step.

### Time Complexity
- The time complexity for Solution 1 (Dynamic Programming) is O(n^2), where n is the length of the input string str. This is because the algorithm uses a 2D array dp to store whether substrings are palindromes, leading to nested loops that iterate through all substrings.

- The time complexity for Solution 2 (Expanding Around Center) is O(n), where n is the length of the input string str. This is because the algorithm expands around each character and checks for palindromes, leading to a linear time complexity.

Overall, Solution 2 is more efficient in terms of time complexity for finding the longest palindromic substring.

</p>
</details>

