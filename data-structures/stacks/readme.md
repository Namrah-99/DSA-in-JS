# Stack 
Stack is a `linear data structure` that follows a particular order in which the operations are performed. The order may be `LIFO(Last In First Out)` or `FILO(First In Last Out)`. LIFO implies that the element that is inserted last, comes out first and FILO implies that the element that is inserted first, comes out last.

To implement the stack, it is required to *maintain the pointer to the top of the stack* , which is the last element to be inserted because we can access the elements only on the top of the stack.

### LIFO(Last In First Out) Principle in Stack Data Structure:
This strategy states that the element that is inserted last will come out first. You can take a pile of plates kept on top of each other as a real-life example. The plate which we put last is on the top and since we remove the plate that is at the top, we can say that the plate that was put last comes out first.

## Types of Stack Data Structure:
### Fixed Size Stack : 
As the name suggests, a fixed size stack has a fixed size and cannot grow or shrink dynamically. If the stack is full and an attempt is made to add an element to it, an overflow error occurs. If the stack is empty and an attempt is made to remove an element from it, an underflow error occurs.
### Dynamic Size Stack : 
A dynamic size stack can grow or shrink dynamically. When the stack is full, it automatically increases its size to accommodate the new element, and when the stack is empty, it decreases its size. This type of stack is implemented using a linked list, as it allows for easy resizing of the stack.

## Operation on Stack:
- Push: Adds an element to the top of the stack
- Pop: Removes and returns the element at the top of the stack
- Peek: Returns the element at the top of the stack without removing it
- Size: Returns the number of elements in the stack
- IsEmpty: Checks if the stack is empty

Get all the details in depth related to stack from "https://www.geeksforgeeks.org/introduction-to-stack-data-structure-and-algorithm-tutorials/"

## Applications of Stack:
- Function calls
- Expression evaluation
- Backtracking
- Undo/redo operations

