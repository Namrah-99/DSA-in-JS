# 71. Simplify Path

## Leetcode Problem
https://leetcode.com/problems/simplify-path/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of simplifying a Unix-style absolute file path into its canonical form, we can utilize a `stack-based approach`. This approach ensures that we handle each component of the path efficiently and adhere to the specified rules. Here’s a detailed explanation:

## Approach

### Understanding Path Components:
- Root: The path always starts with a slash (`/`).
- Directories: Any sequence of characters between slashes (`/`) represents a directory name.
- Special Directories:
  - `.` represents the current directory and can be ignored.
  - `..` represents the parent directory and requires removing the last directory from the canonical path (if available).

### Using a Stack for Canonicalization:
- We'll use a stack to keep track of valid directories in the canonical path.
- Iterate through the input path splitting by `/`.
- For each component:
  - Ignore empty components resulting from consecutive slashes.
  - Push valid directory names onto the stack.
  - Pop from the stack when encountering `..` to move up one directory level, ensuring not to pop beyond the root.

### Constructing the Result:
- After processing all components, construct the final path by joining the directories in the stack.
- Ensure the result starts with a single `/` and handles edge cases such as empty or root-only paths.

## Edge Cases Handled:
- Paths with consecutive slashes (`//`) are treated as a single slash.
- Paths with multiple `.` (e.g., `...`) are treated as valid directory names.
- Paths with `..` correctly move up the directory hierarchy without exceeding the root.

## Complexity Analysis:
- Time Complexity: `O(n)` where `n` is the length of the input path. We traverse the path string once and perform stack operations that are constant time on average.
- Space Complexity: `O(n)` in the worst case, where `n` is the length of the input path. This space is primarily used by the stack to store directory components.

## Solution Code
```javascript
function simplifyPath(path) {
    const stack = [];
    const components = path.split('/'); // Split by '/'
    
    for (let component of components) {
        // Ignore empty strings and current directory references
        if (component === '' || component === '.') {
            continue;
        }
        
        // Handle moving up one directory level
        if (component === '..') {
            if (stack.length > 0) {
                stack.pop(); // Move up one level if stack is not empty
            }
        } else {
            stack.push(component); // Push valid directory name
        }
    }
    
    // Construct the simplified path
    const simplifiedPath = '/' + stack.join('/');
    
    return simplifiedPath || '/'; // If stack is empty, return root '/'
}
```
### Example Usage:
```javascript
console.log(simplifyPath("/home/")); // Output: "/home"
console.log(simplifyPath("/home//foo/")); // Output: "/home/foo"
console.log(simplifyPath("/home/user/Documents/../Pictures")); // Output: "/home/user/Pictures"
console.log(simplifyPath("/../")); // Output: "/"
console.log(simplifyPath("/.../a/../b/c/../d/./")); // Output: "/.../b/d"
```
### Explanation of Examples:
```css
Example 1: "/home/" simplifies to "/home".
Example 2: "/home//foo/" simplifies to "/home/foo".
Example 3: "/home/user/Documents/../Pictures" simplifies to "/home/user/Pictures".
Example 4: "/../" simplifies to "/".
Example 5: "/.../a/../b/c/../d/./" simplifies to "/.../b/d".
```



