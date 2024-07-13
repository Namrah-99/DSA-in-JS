# 2. Add Two Numbers

## Leetcode Problem
https://leetcode.com/problems/add-two-numbers/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. The task is to add the two numbers and return the sum as a linked list.

### Examples
#### Example 1:
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
```
- Explanation: The numbers are 342 (from l1) and 465 (from l2). Their sum is 807, which is represented as [7,0,8] in reverse order.
#### Example 2:
```
Input: l1 = [0], l2 = [0]
Output: [0]
```
- Explanation: Both numbers are 0, and their sum is also 0.
#### Example 3:
```
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```
- Explanation: The numbers are 9999999 (from l1) and 9999 (from l2). Their sum is 10009998, which is represented as [8,9,9,9,0,0,0,1] in reverse order.

### Constraints
- The number of nodes in each linked list is in the range [1, 100].
- 0 <= Node.val <= 9
- The lists represent a number that does not have leading zeros, except the number 0 itself.

## Optimal Approach
The optimal approach involves `iterating through both linked lists` while `maintaining a carry` for digits that sum to a value greater than 9. We `use a dummy node` to simplify edge cases and ensure the result is in the correct format.

### Step-by-Step Explanation:
- Initialization:
  - `dummy` is initialized as a `new ListNode(0)`. This `dummy` node helps in simplifying the logic when constructing the result linked list.
  - `current` is set to `dummy`, which will initially point to the head of the result linked list.
  - `carry` is set to `0`, which keeps track of any carry that needs to be added to the next pair of digits.
- While Loop Execution:
  - The loop continues as long as `l1` is not null, `l2` is not null, or there's still a carry to be added.
- Sum Calculation:
  - `sum` is initialized with the value of `carry`. This starts the sum with any `carry-over` from the previous addition.
  - If `l1` is not null, add `l1.val` to `sum` and move `l1` to the next node (`l1 = l1.next`).
  - If `l2` is not null, add `l2.val` to `sum` and move `l2` to the next node (`l2 = l2.next`).
- Handling Carry:
  ```
  carry = Math.floor(sum / 10);
  ```
  - Calculates how many tens are carried over to the next place value. For example, if `sum` is 18, carry would be 1 (since 18 / 10 = 1.8 floored to 1).
  ```
  current.next = new ListNode(sum % 10);
  ```
  - Creates a new node with the units digit of `sum` (using sum % 10) and links it as the next node in the result linked list.
- Moving to Next Node:
  ```
  current = current.next;
  ```
  - Moves `current` pointer to the newly added node, preparing it for the next iteration.
- Completion:
  - Once the loop completes, `dummy.next` points to the head of the resulting linked list (ignoring the initial dummy node).

## Edge Cases Handled
- Different Lengths:
  ` The solution handles cases where the linked lists have different lengths by iterating as long as there are nodes in either list or there is a carry.
- Carry at the End:
  - If there is a carry after processing both lists, it is handled by creating an additional node.
- Single Node Lists:
  - Works correctly for single node lists and lists containing zero.

## Solution Code
```javascript
var addTwoNumbers = function(l1, l2) {
    let dummy = new ListNode(0);
    let current = dummy;
    let carry = 0;

    while (l1 !== null || l2 !== null || carry !== 0) {
        let sum = carry;
        if (l1 !== null) {
            sum += l1.val;
            l1 = l1.next;
        }
        if (l2 !== null) {
            sum += l2.val;
            l2 = l2.next;
        }
        carry = Math.floor(sum / 10);
        current.next = new ListNode(sum % 10);
        current = current.next;
    }

    return dummy.next;
};
```
## Example Dry Run

```css
Initial Setup:

dummy -> 0 (dummy node)
current -> 0 (points to the same dummy node)
carry = 0

First Iteration:

sum = carry = 0
sum += l1.val = 0 + 2 = 2
sum += l2.val = 2 + 5 = 7
carry = Math.floor(7 / 10) = 0
current.next = new ListNode(7)
After this, dummy -> 0 -> 7
current = current.next moves current to point to 7

Second Iteration:

sum = carry = 0
sum += l1.val = 0 + 4 = 4
sum += l2.val = 4 + 6 = 10
carry = Math.floor(10 / 10) = 1
current.next = new ListNode(0)
After this, dummy -> 0 -> 7 -> 0
current = current.next moves current to point to 0

Third Iteration:

sum = carry = 1
sum += l1.val = 1 + 3 = 3
l1 is now null, so skip adding l1.val
sum += l2.val = 3 + 4 = 7
carry = Math.floor(7 / 10) = 0
current.next = new ListNode(7)
After this, dummy -> 0 -> 7 -> 0 -> 7
current = current.next moves current to point to 7

End of Loop:
l1, l2 are both null, and carry is 0, so the while loop ends.

Result:
The final result linked list is dummy.next, which points to ListNode(7), ListNode(0), ListNode(8).
```

```lua
Input: l1 = [2,4,3], l2 = [5,6,4]

Initialization: dummy and current point to a new node with value 0. carry is 0.

Iteration 1:
sum = 2 + 5 + 0 = 7
carry = 0
current.next = new ListNode(7)
Move l1 to 4 and l2 to 6.

Iteration 2:
sum = 4 + 6 + 0 = 10
carry = 1
current.next = new ListNode(0)
Move l1 to 3 and l2 to 4.

Iteration 3:
sum = 3 + 4 + 1 = 8
carry = 0
current.next = new ListNode(8)
Move l1 and l2 to null.

Result: [7,0,8]
```

## Complexity Analysis
- **Time Complexity:** `O(n)`, where n is the maximum length of the two linked lists. Each node is processed exactly once.
- **Space Complexity:** `O(1)`, since we are using a fixed number of additional variables and the dummy node approach does not count as extra space in asymptotic analysis.
