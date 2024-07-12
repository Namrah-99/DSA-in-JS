# 234. Palindrome Linked List

## Leetcode Problem
https://leetcode.com/problems/palindrome-linked-list/description/

## Problem Explanation
The solution provided is a function to check if a singly linked list is a palindrome. It does this in `O(n)` time and `O(1)` space by following these steps:

- **Find the Middle of the Linked List:**
  - Use the `fast` and `slow` pointer technique to reach the middle of the list.
- **Reverse the Second Half of the List:**
  - Reverse the second half of the linked list in place.
- **Compare Both Halves:**
  - Compare the values of nodes from the first half and the reversed second half to determine if the list is a palindrome.
- **Return the Result:**
  - If all values match, return `true`; otherwise, return `false`.

## Solution Code
```javascript
var isPalindrome = function (head) {
    let slow = head, fast = head, prev, temp
    while (fast && fast.next)
        slow = slow.next, fast = fast.next.next
    prev = slow, slow = slow.next, prev.next = null
    while (slow)
        temp = slow.next, slow.next = prev, prev = slow, slow = temp
    fast = head, slow = prev
    while (slow)
        if (fast.val !== slow.val) return false
        else fast = fast.next, slow = slow.next
    return true
};
```

## Step-by-Step Explanation and Dry Run

### 1. Function Definition
  ```javascript
  var isPalindrome = function (head) {
      let slow = head, fast = head, prev, temp;
  ```
  - Initialize `slow` and `fast` pointers to the head of the list.
  - `prev` and `temp` will be used later for reversing the list.

### 2. Find the Middle of the List
  ```javascript
      while (fast && fast.next) {
          slow = slow.next;
          fast = fast.next.next;
      }
  ```
  - Move `slow one step` at a time and `fast two steps` at a time.
  - When fast reaches the end, slow will be at the middle.
#### Dry Run Example 1 (head = [1, 2, 2, 1]):
- Initial state: slow at 1, fast at 1.
- First iteration: slow at 2, fast at 2.
- Second iteration: slow at 2, fast at null.

### 3. Reverse the Second Half of the List
```javascript
    prev = slow;
    slow = slow.next;
    prev.next = null;
    while (slow) {
        temp = slow.next;
        slow.next = prev;
        prev = slow;
        slow = temp;
    }
```
- Reverse the second half of the list starting from the node after the middle node.
#### Dry Run Example 1:
- prev at 2, slow at 1.
- First iteration: temp at null, slow.next points to prev (2), prev becomes 1, slow becomes null.
- The list now looks like: 1 -> 2 -> null and 2 -> 1 -> null.

### 4. Compare Both Halves
```javascript
    fast = head;
    slow = prev;
    while (slow) {
        if (fast.val !== slow.val) return false;
        fast = fast.next;
        slow = slow.next;
    }
    return true;
};
```
- Set fast back to the head and slow to the beginning of the reversed second half.
- Compare values of nodes from the first and the reversed second half.
#### Dry Run Example 1:
- fast at 1, slow at 1.
- First iteration: fast.val (1) matches slow.val (1), move fast to 2, slow to 2.
- Second iteration: fast.val (2) matches slow.val (2), move fast and slow to null.

Since all values match, return true.

## Edge Cases
- **Empty List:** Returns true (an empty list is a palindrome by definition).
- **Single Node List:** Returns true (a single element list is a palindrome).
- **Even/Odd Length List:** The solution works for both even and odd length lists by correctly handling the middle node.

## Example 2 (head = [1, 2]):
### Dry Run:
- Initial state: slow at 1, fast at 1.
- First iteration: slow at 2, fast at null.
- prev at 2, slow at null (list is already in the second half).
- Comparison: fast at 1, slow at 2. fast.val (1) does not match slow.val (2), return false.

## Dry Run for More Examples
Let's dry run the function with the following examples:

## Example 3 (head = [1, 2, 3, 2, 1])
```
Input: [1, 2, 3, 2, 1]
```
- Find the Middle of the List
  - Initial state: slow at 1, fast at 1.
  - First iteration: slow at 2, fast at 3.
  - Second iteration: slow at 3, fast at 1.
  - Third iteration: slow at 2, fast at null.
- Reverse the Second Half of the List
  - prev at 2, slow at 1.
  - First iteration: temp at null, slow.next points to prev (2), prev becomes 1, slow becomes null.
  - Now, the list looks like:
  ```
  First half: 1 -> 2 -> 3
  ```
  - Reversed second half: 1 -> 2
- Compare Both Halves
  - fast at 1, slow at 1.
  - First iteration: fast.val (1) matches slow.val (1), move fast to 2, slow to 2.
  - Second iteration: fast.val (2) matches slow.val (2), move fast to 3, slow to null.
  - Third iteration: fast.val (3) has no counterpart in the second half but comparison is already done.

Since all values match, return true.

## Example 4 (head = [1, 2, 3, 4, 5])
```
Input: [1, 2, 3, 4, 5]
```
- Find the Middle of the List
  - Initial state: slow at 1, fast at 1.
  - First iteration: slow at 2, fast at 3.
  - Second iteration: slow at 3, fast at 5.
- Reverse the Second Half of the List
  - prev at 3, slow at 4.
  - First iteration: temp at 5, slow.next points to prev (3), prev becomes 4, slow becomes 5.
  - Second iteration: temp at null, slow.next points to prev (4), prev becomes 5, slow becomes null.
  - Now, the list looks like:
  ```
  First half: 1 -> 2 -> 3
  ```
  - Reversed second half: 5 -> 4
- Compare Both Halves
  - fast at 1, slow at 5.
  - First iteration: fast.val (1) does not match slow.val (5), return false.

Since values do not match, return false.

## Example 5 (head = [1, 2, 2, 3])
```
Input: [1, 2, 2, 3]
```
- Find the Middle of the List
  - Initial state: slow at 1, fast at 1.
  - First iteration: slow at 2, fast at 2.
  - Second iteration: slow at 2, fast at null.
- Reverse the Second Half of the List
  - prev at 2, slow at 3.
  - First iteration: temp at null, slow.next points to prev (2), prev becomes 3, slow becomes null.
  - Now, the list looks like:
  ```
  First half: 1 -> 2
  ```
  - Reversed second half: 3 -> 2
- Compare Both Halves
  - fast at 1, slow at 3.
  - First iteration: fast.val (1) does not match slow.val (3), return false.

Since values do not match, return false.

## Example 6 (head = [1, 2, 3, 2, 1, 0])
```
Input: [1, 2, 3, 2, 1, 0]
```
- Find the Middle of the List
  - Initial state: slow at 1, fast at 1.
  - First iteration: slow at 2, fast at 3.
  - Second iteration: slow at 3, fast at 1.
  - Third iteration: slow at 2, fast at null.
- Reverse the Second Half of the List
  - prev at 2, slow at 1.
  - First iteration: temp at 0, slow.next points to prev (2), prev becomes 1, slow becomes 0.
  - Second iteration: temp at null, slow.next points to prev (1), prev becomes 0, slow becomes null.
  - Now, the list looks like:
  ```
  First half: 1 -> 2 -> 3
  ```
  - Reversed second half: 0 -> 1 -> 2
- Compare Both Halves
  - fast at 1, slow at 0.
  - First iteration: fast.val (1) does not match slow.val (0), return false.

Since values do not match, return false.
