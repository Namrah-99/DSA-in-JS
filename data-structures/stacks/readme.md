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

## Implementation of Stack Data Structure:
The basic operations that can be performed on a stack include push, pop, and peek. There are two ways to implement a stack –

### Using Array
In an array-based implementation, the `push` operation is implemented by incrementing the index of the top element and storing the new element at that index. The `pop` operation is implemented by returning the value stored at the top index and then decrementing the index of the top element.

```javascript
let t = -1;
let MAX = 1000;
let arrStack = Array(MAX).fill(0);

function isEmpty(){
        if(t < 0){
        console.log('Stack underflows');
        return true
    }else{
        return false
    }
}

function isFull(){
    if(t >= MAX-1){
        console.log('Stack overflows');
        return true
    }else{
        return false
    }
}

function push(data){
    if(isFull()){
        return false
    }else{
        t+=1; 
        arrStack[t] = data;
        console.log(data,'pushed')
        return true;
    }
}

function pop(){
    if(isEmpty()){
        return 0
    }else{
        let ele = arrStack[t];
        t-=1;
        return ele;
    }
}

function peek(){
    if(isEmpty()){
        return 0
    }else{
        let ele = arrStack[t];
        return ele
    }
}

function print(){
    console.log('_____________________')
    for(let i = t; i > -1; i--){
        console.log(arrStack[i])
    }
    console.log('_____________________')
}

push(2);
push(4);
push(1);
print();
pop();
console.log('peek ele: ',peek());
print();
```

### Using Linked List
In a linked list-based implementation, the `push` operation is implemented by creating a new node with the new element and setting the next pointer of the current top node to the new node. The `pop` operation is implemented by setting the next pointer of the current top node to the next node and returning the value of the current top node.

```javascript
let root;

class Node {
    constructor(data){
        this.data = data;
        this.next = null;
    }
}

function isEmpty(){
    return root === null;
}

function push(data){
    let newNode = new Node(data);
    
    if(isEmpty()){
        root = newNode;
    }else{
        newNode.next = root;
        root = newNode;
    }
}

function pop(){
    if(isEmpty()){
        console.log('Stack is empty')
    }else{
        let poppedNode = root;
        root = root.next;
        return poppedNode.data;
    }
}

function peek(){
     if(isEmpty()){
        console.log('Stack is empty')
    }else{
        return root.data;
    }
}

function print(){
    console.log('_________')
    let current = root;
    while(current){
        console.log('data: ',current.data)
        current = current.next;
    }
}

push(2);
push(4);
push(3);
print()
console.log('popped ele: ',pop());
print()
console.log('peek ele: ',peek())
```
