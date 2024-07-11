# Doubly Linked List
A doubly linked list is a data structure that consists of a set of nodes, each of which contains a `value` and `two pointers`, one pointing to the `previous` node in the list and one pointing to the `next` node in the list.

- It allows for efficient traversal of the list in both directions.
- It allows for quick and easy insertion and deletion of nodes from the list.

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
- Searching in Doubly Linked List
- Finding Length of Doubly Linked List
- Insertion in Doubly Linked List:
    - Insertion at the beginning of Doubly Linked List
    - Insertion at the end of the Doubly Linked List
    - Insertion at a specific position in Doubly Linked List
- Deletion in Doubly Linked List:
    - Deletion of a node at the beginning of Doubly Linked List
    - Deletion of a node at the end of Doubly Linked List
    - Deletion of a node at a specific position in Doubly Linked List
- Traversal in Doubly Linked List:
  - Forward Traversal
  - Backward Traversal

## Implementation
```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
        this.size = 0;
    }

    // Searching in Doubly Linked List
    search(value) {
        let current = this.head;
        while (current !== null) {
            if (current.value === value) {
                return true;
            }
            current = current.next;
        }
        return false;
    }

    // Finding Length of Doubly Linked List
    getLength() {
        return this.size;
    }

    // Insertion at the beginning of Doubly Linked List
    insertAtBeginning(value) {
        const newNode = new Node(value);
        if (this.head === null) {
            this.head = newNode;
            this.tail = newNode;
        } else {
            newNode.next = this.head;
            this.head.prev = newNode;
            this.head = newNode;
        }
        this.size++;
    }

    // Insertion at the end of Doubly Linked List
    insertAtEnd(value) {
        const newNode = new Node(value);
        if (this.tail === null) {
            this.head = newNode;
            this.tail = newNode;
        } else {
            newNode.prev = this.tail;
            this.tail.next = newNode;
            this.tail = newNode;
        }
        this.size++;
    }

    // Insertion at a specific position in Doubly Linked List
    insertAtPosition(value, position) {
        if (position < 0 || position > this.size) {
            throw new Error("Invalid position");
        }
        if (position === 0) {
            this.insertAtBeginning(value);
        } else if (position === this.size) {
            this.insertAtEnd(value);
        } else {
            const newNode = new Node(value);
            let current = this.head;
            let index = 0;
            while (index < position) {
                current = current.next;
                index++;
            }
            newNode.prev = current.prev;
            newNode.next = current;
            current.prev.next = newNode;
            current.prev = newNode;
            this.size++;
        }
    }

    // Deletion of a node at the beginning of Doubly Linked List
    deleteFromBeginning() {
        if (this.head === null) {
            return;
        }
        if (this.head.next === null) {
            this.head = null;
            this.tail = null;
        } else {
            this.head = this.head.next;
            this.head.prev = null;
        }
        this.size--;
    }

    // Deletion of a node at the end of Doubly Linked List
    deleteFromEnd() {
        if (this.tail === null) {
            return;
        }
        if (this.tail.prev === null) {
            this.head = null;
            this.tail = null;
        } else {
            this.tail = this.tail.prev;
            this.tail.next = null;
        }
        this.size--;
    }

    // Deletion of a node at a specific position in Doubly Linked List
    deleteAtPosition(position) {
        if (position < 0 || position >= this.size) {
            throw new Error("Invalid position");
        }
        if (position === 0) {
            this.deleteFromBeginning();
        } else if (position === this.size - 1) {
            this.deleteFromEnd();
        } else {
            let current = this.head;
            let index = 0;
            while (index < position) {
                current = current.next;
                index++;
            }
            current.prev.next = current.next;
            current.next.prev = current.prev;
            this.size--;
        }
    }

    // Forward Traversal
    forwardTraversal() {
        let current = this.head;
        while (current !== null) {
            console.log(current.value);
            current = current.next;
        }
    }

    // Backward Traversal
    backwardTraversal() {
        let current = this.tail;
        while (current !== null) {
            console.log(current.value);
            current = current.prev;
        }
    }
}

// Example usage
const list = new DoublyLinkedList();
list.insertAtEnd(1);
list.insertAtEnd(2);
list.insertAtEnd(3);
list.insertAtBeginning(0);
list.insertAtPosition(1.5, 2);
list.forwardTraversal(); // Output: 0, 1, 1.5, 2, 3
console.log('Length:', list.getLength()); // Output: Length: 5
console.log('Search 2:', list.search(2)); // Output: Search 2: true
list.deleteFromBeginning();
list.deleteFromEnd();
console.log('---------')
list.forwardTraversal(); // Output: 1, 1.5, 2
console.log('---------')
list.deleteAtPosition(1);
list.forwardTraversal(); // Output: 1, 2
list.backwardTraversal(); // Output: 2, 1
console.log('Length:', list.getLength()); // Output: Length: 2
```

## Explanation
- Searching: Traverses the list to find a node with the specified value.
- Finding Length: Returns the size of the list.
- Insertion:
  - At Beginning: Adds a new node at the start of the list.
  - At End: Adds a new node at the end of the list.
  - At Position: Adds a new node at a specific position in the list.
- Deletion:
  - From Beginning: Removes the node at the start of the list.
  - From End: Removes the node at the end of the list.
  - At Position: Removes the node at a specific position in the list.
- Traversal:
  - Forward Traversal: Traverses the list from head to tail.
  - Backward Traversal: Traverses the list from tail to head.

## Complexity Analysis

- search(value)
  - Time Complexity: `O(n)`
    - In the worst case, you may need to traverse the entire list to find the value or determine it does not exist.
  - Space Complexity: `O(1)`
    - No extra space is required, as the search operates in-place.
- getLength()
  - Time Complexity: `O(1)`
    - The size of the list is maintained as a property, so returning it is a constant-time operation.
  - Space Complexity: `O(1)`
    - No extra space is required.
- Insertion
  - insertAtBeginning(value)
    - Time Complexity: `O(1)`
      - Inserting a node at the beginning involves updating the head pointer and the new node's next pointer.
    - Space Complexity: `O(1)`
      - Only a new node is created, which is a constant space requirement.
  - insertAtEnd(value)
    - Time Complexity: `O(1)`
      - Inserting a node at the end involves updating the tail pointer and the new node's prev pointer.
    - Space Complexity: `O(1)`
      - Only a new node is created, which is a constant space requirement.
  - insertAtPosition(value, position)
    - Time Complexity: `O(n)`
      - Inserting at a specific position may require traversing up to n/2 elements in the list, in the worst case.
    - Space Complexity: `O(1)`
      - Only a new node is created, which is a constant space requirement.
- Deletion
  - deleteFromBeginning()
    - Time Complexity: `O(1)`
      - Deleting the first node involves updating the head pointer and the next node's prev pointer.
    - Space Complexity: `O(1)`
      - No extra space is required.
  - deleteFromEnd()
    - Time Complexity: `O(1)`
      - Deleting the last node involves updating the tail pointer and the prev node's next pointer.
    - Space Complexity: `O(1)`
      - No extra space is required.
  - deleteAtPosition(position)
    - Time Complexity: `O(n)`
      - Deleting at a specific position may require traversing up to n/2 elements in the list, in the worst case.
    - Space Complexity: `O(1)`
      - No extra space is required.
- Traversal
  - forwardTraversal()
    - Time Complexity: `O(n)`
      - Traversing from the head to the tail involves visiting each node once.
    - Space Complexity: `O(1)`
      - No extra space is required.
  - backwardTraversal()
    - Time Complexity: `O(n)`
      - Traversing from the tail to the head involves visiting each node once.
    - Space Complexity: `O(1)`
      - No extra space is required.

### Summary
- Insertion at beginning/end: `O(1)`
- Insertion at a specific position: `O(n)`
- Deletion from beginning/end: `O(1)`
- Deletion from a specific position: `O(n)`
- Searching: `O(n)`
- Finding Length: `O(1)`
- Traversal (Forward/Backward): `O(n)`
