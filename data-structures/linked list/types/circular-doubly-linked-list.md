# Circular Doubly linked list
Circular Doubly Linked List has properties of both doubly linked list and circular linked list in which two consecutive elements are linked or connected by the previous and next pointer and the last node points to the first node by the next pointer and also the first node points to the last node by the previous pointer.

## Node Structure
```javascript
class Node {
    constructor(data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}
```

## Operations
- Search: Finds if a node with given data exists.
- Length: Returns the number of nodes in the list.
- Insertion:
  - At the beginning.
  - At the end.
  - At a specific position.
- Deletion:
  - At the beginning.
  - At the end.
  - At a specific position.
- Traversal: Prints all elements in the list.

## Implementation
```javascript
// Node class for the Circular Doubly Linked List
class Node {
    constructor(data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

// Circular Doubly Linked List class
class CircularDoublyLinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    // Method to get the length of the Circular Doubly Linked List
    getLength() {
        return this.length;
    }

    // Method to insert a node at the beginning of the Circular Doubly Linked List
    insertAtBeginning(data) {
        const newNode = new Node(data);
        if (this.head === null) {
            this.head = newNode;
            this.tail = newNode;
            newNode.next = newNode;
            newNode.prev = newNode;
        } else {
            newNode.next = this.head;
            newNode.prev = this.tail;
            this.head.prev = newNode;
            this.tail.next = newNode;
            this.head = newNode;
        }
        this.length++;
    }

    // Method to insert a node at the end of the Circular Doubly Linked List
    insertAtEnd(data) {
        const newNode = new Node(data);
        if (this.head === null) {
            this.head = newNode;
            this.tail = newNode;
            newNode.next = newNode;
            newNode.prev = newNode;
        } else {
            newNode.next = this.head;
            newNode.prev = this.tail;
            this.tail.next = newNode;
            this.head.prev = newNode;
            this.tail = newNode;
        }
        this.length++;
    }

    // Method to insert a node at a specific position in the Circular Doubly Linked List
    insertAtPosition(data, position) {
        if (position < 0 || position > this.length) {
            console.log("Invalid position.");
            return;
        }

        if (position === 0) {
            this.insertAtBeginning(data);
            return;
        }

        if (position === this.length) {
            this.insertAtEnd(data);
            return;
        }

        const newNode = new Node(data);
        let current = this.head;
        let count = 0;

        while (count < position - 1) {
            current = current.next;
            count++;
        }

        newNode.next = current.next;
        newNode.prev = current;
        current.next.prev = newNode;
        current.next = newNode;

        this.length++;
    }

    // Method to delete a node at the beginning of the Circular Doubly Linked List
    deleteAtBeginning() {
        if (this.head === null) {
            console.log("List is empty.");
            return;
        }

        if (this.head === this.tail) {
            this.head = null;
            this.tail = null;
        } else {
            this.head = this.head.next;
            this.head.prev = this.tail;
            this.tail.next = this.head;
        }

        this.length--;
    }

    // Method to delete a node at the end of the Circular Doubly Linked List
    deleteAtEnd() {
        if (this.head === null) {
            console.log("List is empty.");
            return;
        }

        if (this.head === this.tail) {
            this.head = null;
            this.tail = null;
        } else {
            this.tail = this.tail.prev;
            this.tail.next = this.head;
            this.head.prev = this.tail;
        }

        this.length--;
    }

    // Method to delete a node at a specific position in the Circular Doubly Linked List
    deleteAtPosition(position) {
        if (position < 0 || position >= this.length) {
            console.log("Invalid position.");
            return;
        }

        if (position === 0) {
            this.deleteAtBeginning();
            return;
        }

        if (position === this.length - 1) {
            this.deleteAtEnd();
            return;
        }

        let current = this.head;
        let count = 0;

        while (count < position) {
            current = current.next;
            count++;
        }

        current.prev.next = current.next;
        current.next.prev = current.prev;

        this.length--;
    }

    // Method to search for a node with given data in the Circular Doubly Linked List
    search(data) {
        let current = this.head;
        let found = false;

        if (!current) {
            return found;
        }

        do {
            if (current.data === data) {
                found = true;
                break;
            }
            current = current.next;
        } while (current !== this.head);

        return found;
    }

    // Method to traverse and print the Circular Doubly Linked List
    traverse() {
        let current = this.head;
        let result = [];
        
        if (!current) {
            console.log("List is empty.");
            return;
        }

        do {
            result.push(current.data);
            current = current.next;
        } while (current !== this.head);

        console.log(result.join(" -> "));
    }
}

// Example usage:

const circularDLL = new CircularDoublyLinkedList();

circularDLL.insertAtEnd(10);
circularDLL.insertAtEnd(20);
circularDLL.insertAtEnd(30);
circularDLL.insertAtBeginning(5);

circularDLL.traverse(); // Output: 5 -> 10 -> 20 -> 30

console.log("Length:", circularDLL.getLength()); // Output: Length: 4

circularDLL.deleteAtPosition(2);

circularDLL.traverse(); // Output: 5 -> 10 -> 30

console.log("Length:", circularDLL.getLength()); // Output: Length: 3

console.log("Search for 10:", circularDLL.search(10)); // Output: Search for 10: true
console.log("Search for 100:", circularDLL.search(100)); // Output: Search for 100: false
```

## Complexity Analysis

1. Insertion Operations
  - Insertion at Beginning (insertAtBeginning(data)):
    - Time Complexity: `O(1)`
    - Explanation: Creating a new node and updating a few pointers (head, tail, and their respective next and prev pointers) involves constant time operations.
  - Insertion at End (insertAtEnd(data)):
    - Time Complexity: `O(1)`
    - Explanation: Similar to insertion at the beginning, except the tail pointer is updated instead of the head pointer. It involves constant time operations.
  - Insertion at a Specific Position (insertAtPosition(data, position)):
    - Time Complexity: `O(n)`
    - Explanation: In the worst case, when inserting at the end of the list (position n), traversal up to the n-1th node is required. Therefore, this operation is O(n) where n is the length of the list.
2. Deletion Operations
  - Deletion at Beginning (deleteAtBeginning()):
    - Time Complexity: `O(1)`
    - Explanation: Similar to insertion at the beginning, updating a few pointers (head, tail, and their respective next and prev pointers) involves constant time operations.
  - Deletion at End (deleteAtEnd()):
    - Time Complexity: `O(1)`
    - Explanation: Similar to deletion at the beginning, except the tail pointer is updated instead of the head pointer. It involves constant time operations.
  - Deletion at a Specific Position (deleteAtPosition(position)):
    - Time Complexity: `O(n)`
    - Explanation: Similar to insertion at a specific position, in the worst case when deleting the last node (position n-1), traversal up to the n-1th node is required. Therefore, this operation is O(n) where n is the length of the list.
3. Search Operation
  - Search (search(data)):
    - Time Complexity: `O(n)`
    - Explanation: In the worst case, where the node with the specified data is at the end of the list or does not exist, the entire list must be traversed. Therefore, this operation is O(n) where n is the length of the list.
4. Traversal Operation
  - Traversal (traverse()):
    - Time Complexity: `O(n)`
    - Explanation: Printing or processing all nodes requires visiting each node once. Therefore, the traversal operation is O(n) where n is the length of the list.

Summary of Complexity Analysis:
- Space Complexity: `O(n)`, where `n` is the number of elements in the Circular Doubly Linked List. This accounts for the space used by the nodes.
- Time Complexity:
  - Insertion (beginning and end): `O(1)`
  - Insertion (specific position): `O(n)`
  - Deletion (beginning and end): `O(1)`
  - Deletion (specific position): `O(n)`
  - Search: `O(n)`
  - Traversal: `O(n)`
